---
name: Sync an agency's property portfolio from Street
description: Page through every property in a Street.co.uk account, pull the related branch, owner and listing data in the same request, and keep a downstream store in sync.
api: openapi/street-co-open-api-openapi.yml
base_url: https://street.co.uk/open-api/v1
operations:
  - get-properties
  - get-properties-propertyId
  - get-branches
  - get-brands
  - get-areas
generated: '2026-07-26'
method: generated
---

# Sync an agency's property portfolio from Street

Use this when you need a complete, current picture of the properties an estate agency holds in
Street.co.uk — for a data warehouse, a portal feed, or an agent that answers questions about
stock.

## Before you start

- Authenticate with an HTTP bearer token: `Authorization: Bearer <token>`. The token is created
  in the agency's Street account under **Settings > Account Administration > Applications** by a
  company admin. If you are not a Street customer, email `apis@street.co.uk` for a staging token
  and point the base URL at `https://demo.street.co.uk/open-api/v1`.
- Send `Accept: application/vnd.api+json`. Every response is JSON:API.
- Stay under **600 GET requests per minute**. There are no rate-limit response headers, so pace
  yourself rather than waiting to be told.

## Steps

1. **Establish the org shape.** Call `get-branches` and `get-brands` once and cache them; branch
   and brand ids are the join keys on nearly every other resource. `get-areas` gives you the
   agency's area vocabulary.
2. **Page the portfolio.** Call `get-properties` with `page[size]=100` and increment
   `page[number]` until `meta.pagination.current_page` equals `meta.pagination.total_pages`, or
   simply follow `links.next` until it is absent. `page[size]` is capped at 100.
3. **Ask for relationships in the same call.** Pass `include=` with a comma-separated list rather
   than making N+1 requests — related objects come back once in the top-level `included` array,
   not nested inside each property. Reassembling them by hand is the classic mistake here; use a
   JSON:API client library.
4. **Narrow with filters when you do not need everything.** `get-properties` supports
   `filter[category]` (sales or lettings), `filter[branch]`, `filter[postcode]`,
   `filter[bedrooms]`, `filter[min_bedrooms]`, `filter[property_status]`, `filter[tags]`,
   `filter[max_price_sales]`, `filter[min_price_sales]`, `filter[max_price_lettings]`,
   `filter[min_price_lettings]`, `filter[include_archived]` and `filter[trashed]`.
5. **Run incrementally after the first load.** `filter[updated_from]` and `filter[updated_to]`
   (and `filter[created_from]` / `filter[created_to]`) let you fetch only what changed since the
   last sync — do this instead of re-paging the whole portfolio.
6. **Drill into one record** with `get-properties-propertyId` when you need the full detail for a
   single property id, including invoices and property keys via `include`.

## Rules

- **Do not blind-retry writes.** Street publishes no idempotency key of any kind, so a retried
  POST creates a duplicate. This skill is read-only, which is why it is safe to retry.
- **Percent-encode the brackets** in `page[number]`, `page[size]` and `filter[...]`.
- **Never use `filter[max_price]` / `filter[min_price]`** — deprecated 2025-06-19 in favour of the
  sales/lettings-specific variants.
- **Prefer relationships over `*_id` attributes.** Several `subject_id`-style attributes were
  deprecated on 2026-03-06 in favour of the relationship object.
- **Errors** come back as a JSON:API `errors[]` array under `application/vnd.api+json`, never as
  RFC 9457 problem+json. A `401` means the token is missing or wrong, `403` means the token's
  account cannot see that resource, `406`/`415` mean you sent the wrong Accept/Content-Type.
  See `errors/street-co-problem-types.yml`.
- **Stay incremental with webhooks where you can.** `property.archived` and `property.unarchived`
  fire on the account webhook surface (`asyncapi/street-co-webhooks.yml`), but subscriptions are
  configured inside the CRM, not through the API.

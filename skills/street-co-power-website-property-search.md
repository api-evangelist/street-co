---
name: Power an agency website property search with the Street Property Feed
description: Build sales and lettings search on an estate agency's own website from the read-only Street.co.uk Property Feed API, including area and feature facets.
api: openapi/street-co-property-feed-api-openapi.yml
base_url: https://street.co.uk/api/property-feed/v1
operations:
  - get-sales-search
  - get-lettings-search
  - get-propertyId
  - get-areas
  - get-features
generated: '2026-07-26'
method: generated
---

# Power an agency website property search with the Street Property Feed

Use this for the public-facing side of an agency: the search results page, the property detail
page, and the filter facets. This is the API to reach for instead of the Open API when you only
need marketed stock — it is read-only and carries no client data.

## Before you start

- `Authorization: Bearer <token>`, `Accept: application/vnd.api+json`. The token is generated in
  the Street CRM under **Settings > Applications** and must be the Property Feed token, not the
  Public API token.
- Base URL `https://street.co.uk/api/property-feed/v1`; demo environment
  `https://demo.street.co.uk/api/property-feed/v1`.
- Rate limit: **600 requests per minute**, all verbs (everything here is a GET).
- On WordPress, Street recommends the Property Hive plugin with its Property Import add-on rather
  than a bespoke build.

## Steps

1. **Build the facets once per page load (and cache them).** `get-areas` returns the agency's own
   area vocabulary — these are agent-entered in the Street UI, so they are the labels the agency
   actually uses. `get-features` returns the feature list for feature filters.
2. **Run the search.** `get-sales-search` for sales, `get-lettings-search` for lettings. Both take
   the same filter set: `filter[areas]`, `filter[postcode]` (first or partial postcode),
   `filter[bedrooms]`, `filter[min_bedrooms]`, `filter[min_price]`, `filter[max_price]`,
   `filter[status]` (comma-separated for multiples), `filter[branch]` (a branch UUID),
   `filter[features]`, `filter[tags]`, `filter[include_land]` (default false) and
   `filter[include_archived]`.
3. **Sort and page.** `sort` takes a field name; prefix it with `-` for descending. Page with
   `page[number]` and `page[size]`, and drive "next page" from the `links.next` URL the response
   already builds for you.
4. **Render the detail page** with `get-propertyId`, passing `include=` for the related entities
   your template needs (branch, media, rooms and so on) so one request fills the whole page.

## Rules

- **Percent-encode the brackets** in `filter[...]`, `page[number]` and `page[size]`.
- **Read `included`, not nested objects.** JSON:API returns related resources once in the
  top-level `included` array; use a JSON:API client (`swisnl/json-api-client`,
  `woohoolabs/yang` in PHP) rather than reassembling by hand.
- **`has_parking` is deprecated** (2026-01-08) — it is not used in the CRM, so do not build a
  parking facet on it.
- **`allows_pets` exists on the lettings listing object** (added 2025-01-23) if you need a pets
  filter in the UI.
- **This feed is marketing data only.** Applicants, offers, tenancies and client accounting are
  not here — that is the Street Open API, and it needs a different token and a customer
  relationship.
- Errors are JSON:API `errors[]`; `422` on a search means an invalid filter combination, `401`
  means the token is missing or wrong for this feed.

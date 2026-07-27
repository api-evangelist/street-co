---
name: Generate a Spectre property report and collect its leads
description: Create a Spectre property report for an address, retrieve the finished report with its PDF, and pull the leads it generated.
api: openapi/street-co-spectre-api-openapi.yml
base_url: https://api.spectre.uk.com/v1
operations:
  - get-property-reports-user
  - post-property-reports-reports
  - get-property-reports-reports
  - get-property-reports-report
  - get-property-reports-leads
  - post-property-reports-leads
  - post-email-contacts
  - get-email-segments
  - post-email-segments
generated: '2026-07-26'
method: generated
---

# Generate a Spectre property report and collect its leads

Use this for the lead-generation side of Street: Spectre produces branded property reports that
agencies use to win instructions, and it captures the leads those reports create.

## Before you start

- Spectre is a **separate gate** from the Street Open API. Tokens are issued by the Spectre team —
  email `apis@spectre.uk.com`. A Street CRM token will not work here.
- `Authorization: Bearer <token>`, `Accept: application/vnd.api+json`,
  `Content-Type: application/vnd.api+json`.
- Base URL `https://api.spectre.uk.com/v1`. There is no published staging host for Spectre, so you
  are working against production — be careful with writes.
- No rate limit is published for Spectre; treat the Street Open API's ceilings as a sane default.

## Steps

1. **Confirm the account** with `get-property-reports-user`. It returns the current user and, via
   `include=accounts,company,company.reportTemplates`, the company and the report templates you
   are allowed to use — fetch this before creating anything.
2. **Create the report** with `post-property-reports-reports`.
3. **Poll or re-read** with `get-property-reports-report` for a single report id, or
   `get-property-reports-reports` to list. Use `include=pdf` to get the rendered document.
4. **Harvest leads** with `get-property-reports-leads`, and push a lead you captured elsewhere in
   with `post-property-reports-leads`.
5. **Feed marketing** with `post-email-contacts`, `get-email-segments` and
   `post-email-segments` when the lead should enter an email campaign.

## Rules

- **Marketing consent is not optional.** Adding a contact via `post-email-contacts` or a segment
  puts a real person into UK marketing flows. Only do it with a recorded opt-in.
- **No idempotency key.** A retried `post-property-reports-reports` produces a second report and a
  retried lead POST produces a duplicate lead — list first, then decide.
- **Paging and includes are JSON:API.** `page[size]`, `page[number]`, and `include=` with
  comma-separated relationship paths; check each endpoint in the reference for what it supports.
- **Errors** are standard HTTP codes with a JSON:API `errors[]` array — the docs call out `400`,
  `401`, `403`, `404`, `406`, `415` and `500`, e.g. `{"errors":[{"title":"Unauthorized","code":"401"}]}`.

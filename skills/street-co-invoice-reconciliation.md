---
name: Reconcile Street invoices and mark them paid
description: Pull agency invoices with their line items out of Street.co.uk, match them against received payments, and mark an invoice paid.
api: openapi/street-co-open-api-openapi.yml
base_url: https://street.co.uk/open-api/v1
operations:
  - get-invoices
  - get-invoices-invoice_id
  - patch-invoices-invoiceId
  - get-properties-propertyId
  - get-branches
generated: '2026-07-26'
method: generated
---

# Reconcile Street invoices and mark them paid

Use this to bridge Street.co.uk's client accounting to a finance system: read what the agency has
invoiced, match it to money received, and write the paid date back.

## Before you start

- `Authorization: Bearer <token>`; `Accept: application/vnd.api+json` and
  `Content-Type: application/vnd.api+json` on the PATCH.
- Writes are limited to **100 requests per minute**.
- This is money. Build and rehearse against `https://demo.street.co.uk/open-api/v1` with a
  sandbox token from `apis@street.co.uk` before touching a live account.

## Steps

1. **List invoices** with `get-invoices`, paging with `page[number]` / `page[size]` (max 100).
2. **Pull the line items.** Pass `include=line_items` — added 2026-02-18, it returns the fees on
   the invoice, filtered by invoice type (`upfront` or `completion`). Note the `line_items`
   relationship is an **array**, corrected from a singular object on 2026-02-25; older client code
   that assumed a single object is wrong.
3. **Read one invoice** with `get-invoices-invoice_id` when you need the full detail, and
   `get-properties-propertyId` with `include=invoices` when you are working property-first.
4. **Mark it paid** with `patch-invoices-invoiceId`: the body is `data.type = "invoice"`, `data.id`
   the invoice UUID, and `data.attributes.paid_at` — a required RFC 3339 date-time, e.g.
   `2026-02-24T14:30:00Z`. That single attribute is the entire supported mutation.

## Rules

- **Only mark paid what you have actually reconciled.** `paid_at` is the agency's accounting
  record; a wrong value is a real accounting error, not a data-quality nit. If a payment is
  partial or disputed, do not PATCH — surface it to a human.
- **No idempotency key.** A retried PATCH is safe in effect (it re-sets the same `paid_at`), but a
  retried PATCH with a *different* timestamp silently rewrites the record. Compute `paid_at` once
  and reuse it across retries.
- **Listen for `invoice.created`.** That webhook (announced 2026-01-20) fires when a sales invoice
  is generated and is the right trigger for this flow — see `asyncapi/street-co-webhooks.yml`.
  Subscriptions are configured inside the CRM, not through the API.
- Errors are JSON:API `errors[]`: `422` when `paid_at` is missing or malformed, `404` when the
  invoice id does not belong to the token's account, `409` on a state conflict.

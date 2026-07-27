---
name: Read tenancies and raise a maintenance request
description: Walk a Street.co.uk lettings book — tenancies, tenants, landlords and inspections — and raise a maintenance request against the right property.
api: openapi/street-co-open-api-openapi.yml
base_url: https://street.co.uk/open-api/v1
operations:
  - get-tenancies
  - get-tenancies-tenancy_id
  - get-tenants
  - get-tenants-tenantId
  - get-landlords
  - get-landlords-landlordId
  - post-maintenance-requests
  - get-maintenance-jobs
  - get-maintenance-job
  - get-inspections
  - get-move-outs
generated: '2026-07-26'
method: generated
---

# Read tenancies and raise a maintenance request

Use this for property-management work: understanding who lives where under what tenancy, and
getting a repair into the agency's workflow with the right priority.

## Before you start

- `Authorization: Bearer <token>` with `Accept: application/vnd.api+json`; add
  `Content-Type: application/vnd.api+json` for the POST.
- Reads are limited to 600/minute, writes to 100/minute.
- A Public (Open) API token exposes real client data — tenants, landlords, tenancy financials.
  Handle it as personal data under UK GDPR, and prefer the staging environment
  (`https://demo.street.co.uk/open-api/v1`) while building.

## Steps

1. **List the book** with `get-tenancies` and page through it (`page[size]` up to 100). Use
   `include=` to pull the property, owner and tenants alongside each tenancy in one request.
2. **Open one tenancy** with `get-tenancies-tenancy_id` for the full agreement detail, including
   the holding deposit and tenancy-agreement objects.
3. **Resolve the people.** `get-tenants` / `get-tenants-tenantId` for the tenant side (note
   `tenant_type` distinguishes an individual from a company tenant, added 2025-11-06), and
   `get-landlords` / `get-landlords-landlordId` for the landlord side.
4. **Raise the repair** with `post-maintenance-requests`: `data.type = "maintenance-request"`,
   `attributes.priority` is one of `low`, `medium`, `high`, `urgent`, `emergency`;
   `attributes.reported_by` is one of `tenant`, `landlord`, `agent`, `contractor`; plus `summary`,
   `description` and `reported_at`. The `relationships.property` binding is required — a request
   with no property has nowhere to land.
5. **Track the work** with `get-maintenance-jobs` and `get-maintenance-job`; the agency turns
   requests into jobs inside the CRM.
6. **Check the compliance trail** with `get-inspections` (inspection events also fire webhooks)
   and `get-move-outs` when a tenancy is ending.

## Rules

- **Set `priority` honestly.** `emergency` and `urgent` drive real out-of-hours workflows for the
  managing agent; an agent that inflates priority burns the agency's trust in the integration.
- **No idempotency key exists.** If `post-maintenance-requests` times out, list
  `get-maintenance-jobs` / re-query before resending, or you will raise the same repair twice.
- **Escalate, don't act.** There is no API to instruct a contractor, authorise spend, or end a
  tenancy — the write surface here is limited to raising the request. Anything beyond that
  belongs to a human in the CRM.
- Errors are JSON:API `errors[]` objects: `422` for validation (bad enum value, missing
  relationship), `403` when the token's account does not manage that property, `409` for a state
  conflict.

---
name: Capture a lead into Street and schedule the follow-up
description: Push a website or portal enquiry into the Street.co.uk CRM, attach a note, and book a dated follow-up against the right person or property.
api: openapi/street-co-open-api-openapi.yml
base_url: https://street.co.uk/open-api/v1
operations:
  - post-enquiries
  - get-enquiries
  - get-enquiries-enquiryId
  - get-people
  - patch-people-personId
  - post-notes
  - post-follow-ups
  - post-activity
generated: '2026-07-26'
method: generated
---

# Capture a lead into Street and schedule the follow-up

Use this when an enquiry arrives from an agency's own website, a chatbot, or a portal, and it
must land in the Street CRM with the right person, note and follow-up attached.

## Before you start

- `Authorization: Bearer <token>`, `Content-Type: application/vnd.api+json`,
  `Accept: application/vnd.api+json`.
- Write operations are rate limited to **100 requests per minute** (POST/PUT/PATCH/DELETE).
- Test against `https://demo.street.co.uk/open-api/v1` first — the staging token comes from
  `apis@street.co.uk`.

## Steps

1. **Create the enquiry** with `post-enquiries`. The JSON:API body is
   `data.type = "enquiry"`, with `attributes.email_address` and `attributes.message` required;
   `first_name`, `last_name`, `telephone_number` and `custom_source` are optional. Keep
   `custom_source` to **25 characters or fewer** — it is the field that tells the agency where the
   lead came from. `relationships` is required: bind the enquiry to the property or branch it
   concerns.
2. **Read it back** with `get-enquiries-enquiryId` (or list with `get-enquiries`) to resolve the
   person record Street created or matched.
3. **Enrich the person** with `patch-people-personId` only if you have better contact detail than
   the agency already holds. Look them up first with `get-people` — do not create duplicates.
4. **Attach context** with `post-notes`, relating the note to the property, applicant or person so
   negotiators see it in the right place.
5. **Book the follow-up** with `post-follow-ups`: `data.type = "follow-up"`,
   `attributes.due_date` required (a date), optional `attributes.note`, and a `relationships`
   block that must be one of property, sales applicant, lettings applicant, sale, or valuation.
6. **Log the touch** with `post-activity` if you want the interaction itself on the timeline.

## Rules

- **There is no idempotency key.** If a POST times out, do NOT resend it blindly — call the
  matching GET (`get-enquiries` filtered to the window, `get-people`) and confirm whether the
  record landed. Retrying creates a duplicate lead.
- **Consent is real data.** `person.marketing-preferences.updated` is a live webhook event and
  `marketing_consent` / `contact_preferences` are first-class fields. Never set marketing consent
  on a person's behalf without an explicit opt-in from the enquirer — this is UK GDPR territory.
- **422 means the payload was understood but rejected** (validation); **400** means malformed;
  **409** means a conflict with current state. Read the JSON:API `errors[]` array for `title`,
  `code` and `detail`.
- Every request body must be JSON:API shaped — a bare flat object returns `415` or `400`.

# NeverBounce (neverbounce)

NeverBounce is an email verification and list cleaning service (now part of ZeroBounce) that validates individual email addresses in real time and cleans bulk lists by checking syntax, mailbox existence, role addresses, disposable addresses, catch-all domains, and deliverability to reduce bounce rates for marketing, sales, and transactional senders. The NeverBounce v4 REST API at https://api.neverbounce.com/v4/ provides endpoints for single email checks, list jobs (create, parse, start, status, results, download), account info, and webhooks, with JSON responses over HTTPS. Authentication uses a per-integration API key (format `secret_xxxx...`) passed as the `key` parameter or in the Authorization header.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/neverbounce/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/neverbounce/refs/heads/main/apis.yml)

## Scope

- **Type:** Index

## Tags

- Email Verification
- Email Validation
- Email Hygiene
- Deliverability
- Marketing
- List Cleaning
- ZeroBounce

## Timestamps

- **Created:** 2026-05-11
- **Modified:** 2026-05-11

## APIs

### NeverBounce API v4

RESTful JSON API for email verification. Provides single email verification (`/single/check`), bulk job verification (`/jobs/create`, `/jobs/parse`, `/jobs/start`, `/jobs/status`, `/jobs/results`, `/jobs/download`), account info, and POE (Proof of Engagement) endpoints. Authentication uses a per-integration API key (`secret_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`) passed via the `key` query/body parameter or `Authorization: Bearer` header.

- **Human URL:** [https://developers.neverbounce.com/docs/api-getting-started](https://developers.neverbounce.com/docs/api-getting-started)
- **Base URL:** `https://api.neverbounce.com/v4`

#### Tags

- Email Verification
- REST
- JSON
- Deliverability

#### Properties

- [Documentation](https://developers.neverbounce.com/docs/api-getting-started)
- [Verifying an  Email](https://developers.neverbounce.com/docs/verifying-an-email)
- [Verifying a  List](https://developers.neverbounce.com/docs/verifying-a-list)
- [Git Hub  S D Ks](https://github.com/NeverBounce)
- [Postman Collection](collections/neverbounce.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/neverbounce.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/neverbounce)
- [Website](https://www.neverbounce.com)
- [Documentation](https://developers.neverbounce.com/)
- [GitHub Organization](https://github.com/NeverBounce)
- [Pricing](https://www.neverbounce.com/pricing)
- [Sign Up](https://app.neverbounce.com/register)
- [L L Ms Txt](https://developers.neverbounce.com/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

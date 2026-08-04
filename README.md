# NeverBounce (neverbounce)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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

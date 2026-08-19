---
name: neverbounce-verify-single-email
description: >-
  Verify one email address in real time with NeverBounce and interpret the result code,
  flags and suggested correction correctly — including the HTTP-200-error trap that makes
  naive clients read a failure as a success.
api: NeverBounce API v4
base_url: https://api.neverbounce.com/v4.2
spec: openapi/neverbounce-single-api-openapi.yml
operations:
  - single-check
  - account-info
generated: '2026-08-13'
method: generated
source: >-
  openapi/neverbounce-single-api-openapi.yml,
  https://developers.neverbounce.com/reference/single-check,
  https://developers.neverbounce.com/reference/error-handling
---

# Verify a single email address

Use this for **interactive** verification only — a form submit, a signup, a button click.
NeverBounce states plainly that walking an existing list one address at a time through this
endpoint may get the account locked and API access disabled. For a list, use
`neverbounce-verify-a-list`.

## Before you call

- Authentication is a static API key prefixed `secret_`, passed as the `key` parameter.
  A `public_` widget key will not work here.
- **Every call costs one credit**, including duplicates and syntactically bad input, and
  there is no idempotency key. Deduplicate before calling; a retry is a second charge.
- Check the balance first if you are about to run a burst: call `account-info` and read
  `credits_info.paid_credits_remaining`.

## Steps

1. Call **`single-check`** — `GET /single/check` — with:
   - `key` — your `secret_` API key
   - `email` — the address to verify
   - `address_info=1` (optional) to get the parsed address back
   - `credits_info=1` (optional) to get the credit counters back in the same response
   - `timeout` (optional, seconds) to cap how long real-time verification runs before
     returning `unknown`. Total request time can still exceed it — network latency is not
     counted.

2. **Read `status` before you read anything else.** This API returns application errors
   with HTTP 200:

   | `status` | meaning | what to do |
   |---|---|---|
   | `success` | verified | continue to step 3 |
   | `auth_failure` | key rejected | stop; check the key is a V4 `secret_` key |
   | `throttle_triggered` | rate limited | back off and retry; no `Retry-After` is sent |
   | `temp_unavail` | partial outage | retry with backoff, check status.neverbounce.com |
   | `bad_referrer` | origin not in Trusted Domains | fix app settings; do not retry |
   | `general_failure` | bad request | read `message`; do **not** blind-retry |

   Branching on the HTTP status code alone will read a rate-limited or unauthenticated
   response as a successful verification.

3. Interpret `result`:
   - `valid` — deliverable
   - `invalid` — not deliverable, safe to reject
   - `disposable` — a throwaway mailbox provider
   - `catchall` — the domain accepts everything, so deliverability is unknowable
   - `unknown` — verification could not complete (often a timeout)

4. Read `flags[]` for detail (`has_dns`, `academic_host`, `historical_response`, and
   others). `historical_response` means the answer came from NeverBounce's Hybrid
   historical data rather than a live check; send
   `request_meta_data[leverage_historical_data]=0` to force classic real-time verification.

5. If `suggested_correction` is non-empty, it holds a typo fix (for example a mistyped
   domain). Offer it back to the user rather than silently substituting it.

## Encoding gotchas

- `GET` and `POST` are interchangeable. `PUT`/`DELETE` are not supported.
- With `application/x-www-form-urlencoded`, booleans must be `1`/`0`, never `true`/`false`.
- Plus-addressed emails must be percent-encoded as `%2B` in form-encoded requests, or the
  `+` decodes to a space and you verify the wrong address.
- Do not call this from a browser. There is no CORS and the key would be exposed; use the
  JavaScript widget (`components/neverbounce-components.yml`) instead.

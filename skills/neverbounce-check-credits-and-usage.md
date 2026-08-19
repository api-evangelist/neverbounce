---
name: neverbounce-check-credits-and-usage
description: >-
  Read a NeverBounce account's remaining credits and in-flight job counts before spending
  money, and know which of the published ceilings you are about to hit.
api: NeverBounce API v4
base_url: https://api.neverbounce.com/v4.2
spec: openapi/neverbounce-account-api-openapi.yml
operations:
  - account-info
  - jobs-search
  - single-check
generated: '2026-08-13'
method: generated
source: >-
  openapi/neverbounce-account-api-openapi.yml,
  https://developers.neverbounce.com/reference/account-info,
  https://developers.neverbounce.com/reference/usage-guidelines,
  plans/neverbounce-plans-pricing.yml
---

# Check credits and usage before spending

NeverBounce bills per verification credit, and there is no idempotency key anywhere in the
API — a retried `/single/check` is a second charge. Read the balance before a burst.

## Steps

1. **`account-info`** — `GET /account/info?key=` — free, not billable. Returns:
   - `credits_info.paid_credits_remaining` / `free_credits_remaining`
   - `credits_info.paid_credits_used` / `free_credits_used`
   - `job_counts.completed`, `under_review`, `queued`, `processing`

2. **Check headroom against the published ceilings** before creating work:
   - `job_counts.queued + job_counts.processing` must stay under **10 concurrent jobs**.
   - The account may run **50 jobs per day**; `account-info` does not expose today's run
     count, so track it yourself or reconcile with `jobs-search` filtered by
     `job_status`.
   - Job creation rate is capped at **10 jobs per 100,000 items per hour**. Exceeding it
     can lock the account.

3. **Estimate the spend.** One credit per address verified, including duplicates and
   bad-syntax rows. Published rates run from $0.008/email at 1,000 credits down to
   $0.002/email at 2,000,000 (see `plans/neverbounce-plans-pricing.yml`). If the balance
   will not cover the list, stop before creating the job.

4. **Inline balance during single verification.** If you are already calling
   `single-check`, add `credits_info=1` and the same counters come back on the
   verification response — one call instead of two.

5. **Free analysis before a billable run.** Create a job with `run_sample=1` to get a
   `bounce_estimate` and result-code breakdown from `jobs-status` without paying for the
   full run.

## Error handling

`account-info` returns the same envelope as everything else: HTTP 200 with a `status`
field. `auth_failure` here is the fastest way to confirm a key is a valid V4 `secret_` key
before you use it anywhere else.

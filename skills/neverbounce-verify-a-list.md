---
name: neverbounce-verify-a-list
description: >-
  Run a bulk email list through NeverBounce end to end — create, parse, sample, start,
  poll and download — while staying inside the published concurrency, daily-run and payload
  limits that get accounts locked when ignored.
api: NeverBounce API v4
base_url: https://api.neverbounce.com/v4.2
spec: openapi/neverbounce-jobs-api-openapi.yml
operations:
  - jobs-create
  - jobs-parse
  - jobs-start
  - jobs-status
  - jobs-results
  - jobs-download
  - jobs-search
  - jobs-delete
  - account-info
generated: '2026-08-13'
method: generated
source: >-
  openapi/neverbounce-jobs-api-openapi.yml,
  overlays/neverbounce-jobs-overlay.yaml,
  https://developers.neverbounce.com/reference/jobs-create,
  https://developers.neverbounce.com/reference/usage-guidelines
---

# Verify a list of emails

## Sizing the work first

These are NeverBounce's own rules, and breaking them is an account-lockout risk, not a
soft limit:

- **10 concurrent jobs**, **50 job runs per day** per account.
- **No more than 10 jobs per 100,000 items per hour.**
- Under 1 million addresses: submit **one** job, not several small ones. One 50k job beats
  five 10k jobs.
- Over 1 million: split into **1-million-item chunks**, one job each.
- `supplied_data` payloads cap at **25MB**; over that you get HTTP 413. Switch
  `input_location` to `remote_url` and let NeverBounce fetch the file.

## Steps

1. **`jobs-create`** — `POST /jobs/create`. Required: `input_location`
   (`remote_url` or `supplied`) and `input`. Useful options:
   - `filename` — what shows in the dashboard
   - `auto_parse` — index immediately
   - `auto_start` — run immediately after parsing
   - `run_sample` — run a free analysis instead of a billable full run
   - `allow_manual_review` — opt in to manual review (since 4.2, API jobs are **not**
     eligible by default)
   - `request_meta_data[leverage_historical_data]=0` — force real-time-only verification
   - `callback_url` + `callback_headers` — see step 5

   Save the returned `job_id`. Job creation is **not idempotent**: re-submitting the same
   list creates a second job and a second billable run.

2. **`jobs-parse`** — `POST /jobs/parse` with `job_id`, if you did not set `auto_parse`.
   Indexing must finish before the job can start.

3. **Optional free analysis.** Create with `run_sample=1` (or watch for
   `job_sample_finished`) and read `bounce_estimate` and the `total.*` counters from
   `jobs-status` before committing credits to the full run.

4. **`jobs-start`** — `POST /jobs/start` with `job_id`, if you did not set `auto_start`.

5. **Wait for completion.** Two options, and the callback one is strongly preferred:
   - **Callbacks** (4.2+): pass `callback_url` at creation. NeverBounce POSTs
     `{"job_id":<int>,"event":"<name>"}` for `job_parsing_started`,
     `job_parsing_finished`, `job_sample_started`, `job_sample_finished`,
     `job_run_started`, `job_stats_updated`, `job_review_completed`, `job_run_finished`,
     `job_failed` and `job_deleted`. Expect `job_stats_updated` **frequently** while a job
     runs — debounce it. There is no signature: authenticate the callback with a secret you
     supply yourself in `callback_headers`.
   - **Polling** `jobs-status` — `GET /jobs/status?job_id=` — reading `percent_complete`
     and `job_status`. Still supported as a fallback.

6. **Handle failure.** If `job_status` is `failed`, read `failure_reason` from
   `jobs-status` (added in 4.2). NeverBounce does not publish the reason-code enumeration,
   so log the raw value rather than switching on it.

7. **Collect results.** Two surfaces:
   - **`jobs-results`** — `GET /jobs/results?job_id=` — paged JSON. Page with `page` and
     `items_per_page`; read `total_results` and `total_pages`. Segment with `valids`,
     `invalids`, `catchalls`, `unknowns`, `disposables`. Each row has `data` (your original
     columns, echoed back — the join key into your own system) and `verification`.
   - **`jobs-download`** — `GET /jobs/download?job_id=` — the whole set as a CSV over
     `application/octet-stream`. Extra flags: `include_duplicates`, `email_status`. Use
     this for anything large; do not page a million rows through JSON.

8. **`jobs-delete`** — `POST /jobs/delete` with `job_id` when the data should no longer be
   retrievable. After this the job is gone for both verification and download, and a
   `job_deleted` callback fires.

`jobs-search` — `GET /jobs/search` — finds existing jobs by `job_id`, `filename` or
`job_status`, paged the same way. Use it to reconcile before creating a duplicate job.

## Error handling

Every application error arrives as **HTTP 200** with a non-`success` `status`
(`auth_failure`, `throttle_triggered`, `temp_unavail`, `bad_referrer`,
`general_failure`). Check `status` on every response. HTTP 413 on create means the payload
exceeded 25MB. See `errors/neverbounce-problem-types.yml`.

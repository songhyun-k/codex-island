# Homebrew tap clones → PostHog (daily cron)

`brew install` against a third-party tap performs a `git clone` of the
tap repo. GitHub exposes 14 days of clone history per repo via
`/repos/{owner}/{tap}/traffic/clones`, after which the data is gone.

The workflow at
[`ericjypark/homebrew-tap/.github/workflows/clones-to-posthog.yml`](https://github.com/ericjypark/homebrew-tap/blob/main/.github/workflows/clones-to-posthog.yml)
runs daily at 02:17 UTC, fetches yesterday's clone row, and pushes a
single `homebrew_tap_daily` event to PostHog. Backfill mode
(`workflow_dispatch` with `backfill=true`) walks all 14 days currently
in the API. Idempotent via `$insert_id`.

## Status

- ✅ Workflow committed and active.
- ✅ `POSTHOG_KEY` + `POSTHOG_HOST` secrets set on the tap repo.
- ✅ Initial 14-day backfill completed (2026-04-30 → 2026-05-03 had
  non-zero traffic and is now in PostHog).
- ⚠️ **`TRAFFIC_TOKEN` secret NOT yet set** — the daily cron will
  fail until this is added. See "Why a separate token" below.

## Why a separate token

GitHub Actions' built-in `GITHUB_TOKEN` cannot read the traffic API.
Traffic data requires the fine-grained permission **Administration:
Read**, which is not in the list of scopes available to
`GITHUB_TOKEN` in workflow YAML
(`actions/checks/contents/deployments/.../statuses` only).

So the workflow needs a fine-grained PAT exposed as `TRAFFIC_TOKEN`.

## Adding TRAFFIC_TOKEN (one-time, ~2 min)

1. Open <https://github.com/settings/personal-access-tokens/new>
2. Configure:
   - **Token name**: `homebrew-tap traffic stats`
   - **Expiration**: 1 year (mark calendar to renew)
   - **Repository access**: "Only select repositories" → `ericjypark/homebrew-tap`
   - **Permissions** → Repository permissions:
     - **Administration: Read-only**
     - (everything else stays "No access")
3. Click **Generate token** and copy the value.
4. Set as a secret on the tap repo:
   ```sh
   gh secret set TRAFFIC_TOKEN --repo ericjypark/homebrew-tap --body 'github_pat_...'
   ```
5. Trigger to verify:
   ```sh
   gh workflow run clones-to-posthog.yml --repo ericjypark/homebrew-tap -f backfill=true
   gh run watch "$(gh run list --repo ericjypark/homebrew-tap --workflow=clones-to-posthog.yml --limit 1 --json databaseId --jq '.[0].databaseId')" --exit-status --repo ericjypark/homebrew-tap
   ```

## Caveats

- **`brew update` also clones the tap.** If a user installed once and
  `brew update`s daily, they show up every day. Treat
  `day_unique_count` as the more honest signal — it's the number of
  unique IPs that hit the tap that day.
- **GitHub returns at most 14 days of history.** The cron preserves
  data going forward, but anything older than `today - 14` is
  permanently gone unless already captured.
- The first cron run after setup will only see the last 24h. Re-run
  with `backfill=true` once after enabling to grab the trailing 14
  days too.

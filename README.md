# OutLawZ Facebook Automation

GitHub home for OutLawZ Facebook post assets, captions, run records, and the status dashboard.

## Publishing rules

- Metricool brand: `7508377` (`net1outlawzz`)
- Network: Facebook only
- Timezone: `Asia/Karachi`
- Planned cadence: daily, flexible morning target around 08:00 PKT
- Scheduling only: never publish immediately
- A run is successful only after querying Metricool and confirming the exact post text, media, Facebook provider, and scheduled time.
- Keep previous assets and run history. Do not delete them during migration.
- Dropbox is read-only legacy archive only; no new uploads.

## Repository layout

- `assets/YYYY-MM-DD/morning/`: generated post image and caption
- `runs/`: append-only per-run status records
- `docs/status.json`: current dashboard data
- `docs/index.html`: single-page status dashboard

## Status dashboard

The dashboard reads `docs/status.json`. The GitHub Actions workflow deploys the `docs` directory when it changes; GitHub Pages must be configured to use **GitHub Actions** as its source. Do not put credentials, private tokens, or private post data in the public dashboard.

## Automation integration status

The existing **OutLawZ Morning Post** automation has been updated to use GitHub for new files and to remove Dropbox writes. It remains enabled on a daily flexible morning schedule.

The current run generated a PNG and caption. The caption was committed, but the connected GitHub tools cannot upload the generated binary PNG in this session. Therefore, no media URL could be verified and Metricool scheduling was stopped. The dashboard records this as `blocked`; it must not show success until Metricool confirms caption, media, Facebook provider, and scheduled time.

Recommended run record fields: `runId`, `startedAt`, `finishedAt`, `status`, `topic`, `caption`, `imagePath`, `captionPath`, `githubCommitUrl`, `metricoolPostId`, `scheduledAt`, `provider`, `steps`, `errors`, and `nextRunAt`. Each step should include a status and timestamp. Keep history append-only.

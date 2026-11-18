# OutLawZ Facebook Automation

GitHub home for OutLawZ Facebook post assets, captions, run records, and the status dashboard.

## Publishing rules

- Metricool brand: `7508377` (`net1outlawzz`)
- Network: Facebook only
- Timezone: `Asia/Karachi`
- Planned cadence: daily at 08:00 PKT, after the existing morning automation is restored
- Scheduling only: never publish immediately
- A run is successful only after querying Metricool and confirming the exact post text, media, Facebook provider, and scheduled time.
- Keep previous assets and run history. Do not delete them during migration.
- Dropbox must not be used.

## Repository layout

- `assets/`: generated post images and captions, organized by run date
- `runs/`: append-only per-run status records
- `docs/status.json`: current dashboard data
- `docs/index.html`: single-page status dashboard

## Status dashboard

The dashboard is a static page reading `docs/status.json`. Enable GitHub Pages with the **GitHub Actions** source and deploy the `docs` directory to publish it. Do not put credentials, private tokens, or private post data in the public dashboard.

## Automation integration status

This repository was empty when connected. The dashboard and its data contract are being established first. The existing Codex automations still need to be updated to remove Dropbox, commit generated PNG/TXT assets to this repository, schedule through Metricool, query Metricool for verification, and append a run record. No publishing automation is considered migrated until that integration is in place.

Recommended run record fields: `runId`, `startedAt`, `finishedAt`, `status`, `topic`, `caption`, `imagePath`, `githubCommitUrl`, `metricoolPostId`, `scheduledAt`, `provider`, `steps`, `errors`, and `nextRunAt`. Each step should include a status and timestamp. Keep history append-only.

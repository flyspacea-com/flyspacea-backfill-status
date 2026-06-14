# FlySpaceA — Historical Backfill Status

A tiny static status page for the one-time historical Space-A schedule backfill.

**Live page:** https://flyspacea-com.github.io/flyspacea-backfill-status/

## What this is

`index.html` fetches `status.json` (refreshed every 60s) and renders progress,
data-loaded counts, Gemini usage/cost, and recent pipeline-run health.

`status.json` is regenerated on the operator's workstation by
`scripts/backfill-stats.py` in the main `flyspacea` repo and pushed here on a
loop by `scripts/backfill-dashboard.sh --publish --watch`.

## Privacy / sanitization

This page is intentionally **public but sanitized**. `status.json` contains only
aggregate, non-identifying numbers. It deliberately excludes GCP project IDs,
bucket names, Cloud Run execution IDs, accounts, hostnames, and file paths.
Historical Space-A flights are loaded SQL-only and stay invisible in the app by
design; no per-flight detail is published here.

## Updating

The page is data-driven — there is normally nothing to edit here. To change the
layout, edit `index.html`. The data shape is documented by the keys in
`status.json`.

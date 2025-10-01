# OSINT Visualizer (Live APIs)

A lightweight, browser-only OSINT dashboard that pulls live data from multiple government and corporate registries. The UI lets investigators search for a term, toggle data sources, and see aggregated metrics rendered on a radial “spire” chart.

> **Heads-up:** the previous version of this project shipped with fully mocked data. The application now connects to real APIs, so you must supply valid API keys/tokens before searching.

## Features

- Search across multiple OSINT endpoints (FEC, GovInfo, OpenCorporates) directly from the browser
- Per-source toggles with live hit counts, average confidence, and grouped result cards
- Interactive radial visualization showing relative hit volume and average confidence by source
- Client-side storage of API keys in `localStorage` via the in-app **API Keys** dialog
- Graceful error handling for missing credentials, timeouts, and partial failures

## Supported APIs & keys

| Source          | API documentation | Credential name | Notes |
|-----------------|-------------------|-----------------|-------|
| FEC             | https://api.open.fec.gov/developers/ | `api_key` | A demo key (`DEMO_KEY`) is bundled for quick tests. Production usage should register its own key.
| GovInfo         | https://api.govinfo.gov/docs/ | `api_key` | Also accepts `DEMO_KEY`, but register for higher limits.
| OpenCorporates  | https://api.opencorporates.com/documentation/API-Reference | `api_token` | Requires a personal API token (no demo token provided).

Additional sources can be added by extending the `SOURCE_CONFIG` object in `index.html` with a new color, metadata, and fetcher function.

## Getting started

1. Clone the repository and open `index.html` in any modern browser, or serve it locally (e.g. `python -m http.server`).
2. Click **API Keys** and paste valid credentials for each source you plan to query. Keys are stored only in your browser’s `localStorage`.
3. Enter a search term (person, company, keyword, etc.) and press **Search**.
4. Toggle sources on/off with the chips to focus on subsets of the data. The metrics panel and radial chart update instantly.

## Key storage & security

- Keys never leave the browser; there is no backend component.
- Clearing an input in the **API Keys** dialog removes it from `localStorage`.
- Use caution when deploying to shared machines—clear stored keys after use.

## Development notes

- All UI and data-fetching logic lives in `index.html` for ease of hosting (e.g. GitHub Pages).
- Requests include built-in timeouts and show contextual warnings if any source fails or lacks a key.
- Confidence scores are derived from API-specific metadata (where available) or heuristics to keep the visualization meaningful.

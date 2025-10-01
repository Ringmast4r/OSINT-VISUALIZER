OSINT Visualizer (Mock Demo)

Live demo: https://ringmast4r.github.io/OSINT-VISUALIZER/

Overview

This is a mock demo of an OSINT visualizer tool, built to show how the final product could look. No real API keys or live data are included — all data is synthetic. This allows safe public hosting on GitHub Pages without exposing secrets.

Features:

A search box where users type in a name, company, keyword, or IP address.

Colored source chips (like FEC, GovInfo, OpenCorporates, etc.) that users can toggle on/off.

A radial “spire” chart where each source has a ring:

The height (line width) of the ring corresponds to the number of mock hits from that source.

The arc length of the ring corresponds to the average “confidence” for that source.

Each source has its own color.

A metrics strip showing per-source hits and average confidence.

Grouped results cards under each source showing mock items (title, summary, time, etc.).

Fully client-side; no backend, no API calls (so no CORS issues or key exposure).

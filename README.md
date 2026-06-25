# Sentinel Log - Splunk Web Traffic Analytics & Anomaly Dashboard

A Splunk-based analytics project that ingests web server access logs and surfaces both traffic insights and security anomalies — brute-force login attempts, traffic spikes, and server error spikes — through SPL queries and an interactive dashboard.

## What it does

- Ingests Apache-style access logs into Splunk
- Runs SPL queries to surface:
  - Top visited pages
  - Traffic trends over time
  - Brute-force login attempts (MITRE T1110)
  - Abnormal traffic spikes from a single source (MITRE T1498)
  - Server error spikes (operational health)
- Combines all of the above into a single dashboard

## Dashboard

![Dashboard Screenshot](screenshots/dashboard.png)

## Project Structure
sentinel-log-splunk/

├── README.md

├── data/

│   └── access_logs.log

├── spl-queries/

│   ├── 01_top_pages.spl

│   ├── 02_traffic_timechart.spl

│   ├── 03_brute_force_detection.spl

│   ├── 04_traffic_spike_detection.spl

│   └── 05_error_spike_detection.spl

├── dashboard/

│   └── dashboard_export.json

├── docs/

│   ├── setup_guide.md

│   └── mitre_mapping.md

└── screenshots/## Quick Start

1. Upload `data/access_logs.log` into Splunk (sourcetype=access_combined)
2. Run each query in `spl-queries/`
3. Save results as dashboard panels
4. Explore the anomalies baked into the sample dataset

## Sample Data Anomalies

1. A traffic spike from a single IP (~800 requests in 30 minutes)
2. A brute-force login attempt (150 failed logins + 1 successful login)
3. A server error spike (~100 HTTP 500 errors within an hour)

## Tech Used

- Splunk Enterprise (Search & Reporting, Dashboard Studio)
- SPL (Search Processing Language)

## License

MIT

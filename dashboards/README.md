# RouteWarden Grafana Dashboard & Alerting

This document outlines the official Grafana threat intelligence dashboard and alerting configurations for the RouteWarden ecosystem.

> [!NOTE]
> **Single Source of Truth**: To avoid configuration drift and outdated templates, all observability assets (dashboard JSON, Loki configs, Grafana Alloy pipelines, and alerting YAML rules) are maintained and versioned in the [`routewarden/cli`](https://github.com/routewarden/cli) repository under [`observability/`](https://github.com/routewarden/cli/tree/main/observability).

- **Official Documentation**: [https://routewarden.github.io/cli/dashboard](https://routewarden.github.io/cli/dashboard)
- **Authoritative Source**: [`github.com/routewarden/cli/tree/main/observability/grafana`](https://github.com/routewarden/cli/tree/main/observability/grafana)

---

## Direct Download Links (Canonical)

You can download the latest production templates directly from the CLI repository:

| Asset | Format | Raw URL |
|---|---|---|
| **Threat Intelligence Dashboard** | JSON | [`routewarden-overview.json`](https://raw.githubusercontent.com/routewarden/cli/main/observability/grafana/dashboards/routewarden-overview.json) |
| **Security Alerting Rules** | YAML | [`alerting.yaml`](https://raw.githubusercontent.com/routewarden/cli/main/observability/grafana/provisioning/alerting/alerting.yaml) |
| **Grafana Datasource Config** | YAML | [`datasources.yaml`](https://raw.githubusercontent.com/routewarden/cli/main/observability/grafana/provisioning/datasources/datasources.yaml) |
| **Environment Configuration** | ENV | [`routewarden.env`](https://raw.githubusercontent.com/routewarden/cli/main/observability/routewarden.env) |

---

## Included Panels & Visualizations

1. **Key Security Counters**: Blocked Attacks, Total Inspected Events, Whitelist Bypasses, and Attack Ratio percentage.
2. **Multi-Series Threat Timelines**: Visualizes `BLOCK` (red), `ALLOW` (green), `THROTTLED` (amber), and `BYPASS` (blue) over time.
3. **Verdict & HTTP Status Distributions**: Donut charts showing traffic action and status codes (`403`, `404`, `429`, `200`).
4. **Threat Geography & GeoIP Intelligence**:
   - **Global Attack Origins Map (Geomap)**: Live world map plotting attack clusters by ISO 3166-1 alpha-2 country codes.
   - **Top Attacking Countries**: Ranked horizontal bar gauge of top origin nation-states.
   - **Country Threat Share**: Donut breakdown of hostile traffic distribution across origin countries.
5. **Layer 4 & Layer 7 Multi-Protocol Convergence**:
   - **L4 vs L7 Threat Convergence Over Time**: Stacked multi-series tracking HTTP web gateway blocks vs Layer 4 TCP (SSH) bans vs UDP (DNS) drops.
   - **Protocol Breakdown**: Donut chart of traffic across `http`, `ssh`, `dns`, `dht`, `tcp`, `udp`.
   - **Transport Split**: Bar gauge comparing TCP vs UDP traffic volume.
6. **Threat Analysis & Attack Vector Profiling**:
   - **Top Attacked Targets**: Ranked bar chart of targeted endpoints (`/.env`, `/.git/config`, `/wp-login.php`, etc.).
   - **Top Offender IPs & GeoIP**: Ranked client IPs annotated with GeoIP country identifiers (`[US]`, `[DE]`, `[LAN]`).
   - **Top Blocked Patterns**: Signatures and rules triggering enforcement actions.
   - **Malicious User-Agents & Attack Scanners**: Ranked bar gauge identifying offensive scanners (`Nuclei`, `Nikto`, `sqlmap`, `Masscan`, `curl`, `bots`).
   - **Attacked HTTP Methods**: Donut breakdown of HTTP request verbs in attacks (`GET`, `POST`, `HEAD`, `CONNECT`).
7. **Interactive Incident Triage & Live Security Feed**:
   - **🚨 Interactive Threat Incident Triage Table**: Structured forensic grid with one-click IP lookups for **AbuseIPDB**, **VirusTotal**, **Shodan**, and **Loki Threat Hunter**.
   - **📜 Real-Time Attack Log Stream**: Low-latency, expandable log stream with full structured metadata (`country_name`, `flag_emoji`, `rule_id`, `reason`).
8. **Interactive Filter Variables**: Top-bar multi-select dropdowns for **Gateway**, **Verdict**, **Country**, **Protocol**, and **Transport**.
9. **Forensic Header Links**: Direct navigation to Grafana Explore Threat Hunter, AbuseIPDB Search, and Documentation.

---

## Automated Alerting & Notification Channels

Pre-configured alerting rules in [`alerting.yaml`](https://raw.githubusercontent.com/routewarden/cli/main/observability/grafana/provisioning/alerting/alerting.yaml):
- **DDoS / Attack Rate Spike**: Warning when block rate exceeds $10\,\text{req/s}$.
- **Sensitive Path Probing**: Critical alert on attempts to access `/.env`, `/.git`, or `/.aws`.
- **Layer 4 Brute-Force Surge**: High alert on $>15$ connection drops/bans in 3 minutes.
- **Active Exploitation Tools**: Detection of offensive scanners (`sqlmap`, `nuclei`, `nikto`, `masscan`).
- **Contact Points**: Ready-to-use receivers for **Slack**, **Discord**, **PagerDuty**, and **Webhooks**.

---

## How to Deploy / Import

### Option 1: Automated CLI Deployment (Recommended)
If using the RouteWarden developer CLI (`rwarden`):
```bash
# Launch a complete, pre-wired Grafana + Loki + Alloy stack automatically:
rwarden dashboard up

# Or launch with alerting pre-enabled:
rwarden dashboard up --enable-alerting

# Or export all observability configuration files directly to disk:
rwarden dashboard export ./observability
```

### Option 2: Grafana Web UI
1. Download [`routewarden-overview.json`](https://raw.githubusercontent.com/routewarden/cli/main/observability/grafana/dashboards/routewarden-overview.json).
2. Open your Grafana instance in your browser.
3. Navigate to **Dashboards > New > Import**.
4. Upload the downloaded JSON file or paste its raw content.
5. Select your Loki datasource from the dropdown prompt and click **Import**.

### Option 3: Grafana HTTP API
```bash
curl -s https://raw.githubusercontent.com/routewarden/cli/main/observability/grafana/dashboards/routewarden-overview.json | \
curl -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <GRAFANA_SERVICE_ACCOUNT_TOKEN>" \
  -d "{\"dashboard\": $(cat -), \"overwrite\": true}" \
  https://grafana.example.com/api/dashboards/db
```

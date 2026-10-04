# RouteWarden Grafana Dashboard

This directory contains the canonical, pre-built **Grafana** dashboard template for the RouteWarden ecosystem.

- **Dashboard File**: [`routewarden-overview.json`](./routewarden-overview.json)
- **Title**: `RouteWarden — Threat & Security Intelligence`
- **Datasource**: Grafana Loki
- **Official Documentation**: [https://routewarden.github.io/cli/dashboard](https://routewarden.github.io/cli/dashboard)

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

## Public & Shared Dashboards

RouteWarden's stack is ready for public sharing and embedding out-of-the-box:
- **Zero-Login Anonymous Access**: Default anonymous viewer access allows instant visibility on status pages and NOC/SOC displays without login prompts.
- **Public Dashboards**: Enabled via `GF_FEATURE_TOGGLES_ENABLE=publicDashboards` to generate public share links from the dashboard menu.
- **Secure Portal Embedding**: Enabled via `GF_SECURITY_ALLOW_EMBEDDING=true` for embedding in company intranets or customer portals via `<iframe>`.

---

## Automated Alerting & Notification Channels

RouteWarden includes pre-configured alerting rules in [`alerting.yaml`](./alerting.yaml):
- **DDoS / Attack Rate Spike**: Warning when block rate exceeds $10\,\text{req/s}$.
- **Sensitive Path Probing**: Critical alert on attempts to access `/.env`, `/.git`, or `/.aws`.
- **Layer 4 Brute-Force Surge**: High alert on $>15$ connection drops/bans in 3 minutes.
- **Active Exploitation Tools**: Detection of offensive scanners (`sqlmap`, `nuclei`, `nikto`, `masscan`).
- **Contact Points**: Ready-to-use receivers for **Slack**, **Discord**, **PagerDuty**, and **Webhooks**.

---

## How to Import

### Option 1: Grafana Web UI
1. Open your Grafana instance in your browser.
2. Navigate to **Dashboards > New > Import**.
3. Upload [`routewarden-overview.json`](./routewarden-overview.json) or paste its raw JSON content.
4. Select your Loki datasource from the dropdown prompt and click **Import**.

### Option 2: Grafana HTTP API
```bash
curl -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <GRAFANA_SERVICE_ACCOUNT_TOKEN>" \
  -d "{\"dashboard\": $(cat routewarden-overview.json), \"overwrite\": true}" \
  https://grafana.example.com/api/dashboards/db
```

### Option 3: Automated CLI Deployment
If using the RouteWarden developer CLI (`rwarden`):
```bash
# Launch a complete, pre-wired Grafana + Loki + Alloy stack automatically:
rwarden dashboard up

# Or export all observability configuration files directly to disk:
rwarden dashboard export ./observability
```

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
4. **Top Attacked Targets**: Ranked bar chart of targeted endpoints (`/.env`, `/.git/config`, `/wp-login.php`, etc.).
5. **Top Offender IPs & GeoIP**: Ranked client IPs with country flag emojis and country names.
6. **Top Blocked Patterns**: Signatures and rules triggering enforcement actions.
7. **Live Security Event Feed**: Low-latency, expandable log stream with full JSON metadata.

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

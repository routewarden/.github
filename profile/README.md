<div align="center">

  <img src="https://raw.githubusercontent.com/routewarden/traefik-warden/main/assets/icon.svg" alt="RouteWarden Logo" width="140" height="140" />

  # RouteWarden

  <p><strong>Open-source, high-performance security middleware and edge defense tools.</strong></p>

  <p>
    <a href="https://routewarden.github.io/docs/"><img src="https://img.shields.io/badge/Docs-VitePress%20Wiki-6366f1.svg?style=for-the-badge" alt="Documentation Site" /></a>
    <a href="https://routewarden.github.io/docs/?playground=open"><img src="https://img.shields.io/badge/Live%20Demo-Interactive%20Playground-0ea5e9.svg?style=for-the-badge" alt="Interactive Playground" /></a>
    <a href="https://github.com/routewarden/traefik-warden"><img src="https://img.shields.io/badge/Traefik%20Plugin-traefik--warden-blue.svg?style=for-the-badge&logo=traefik" alt="Traefik Plugin" /></a>
    <a href="https://github.com/routewarden/caddy-warden"><img src="https://img.shields.io/badge/Caddy%20Module-caddy--warden-1f883d.svg?style=for-the-badge&logo=caddy" alt="Caddy Module" /></a>
    <a href="https://github.com/routewarden/traefik-warden/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge" alt="MIT License" /></a>
  </p>

</div>

---

### About RouteWarden

RouteWarden builds lightweight, high-performance perimeter defense middleware for modern reverse proxies and container environments.

The goal is straightforward: intercept automated scanners, directory traversal, sensitive file probing, and path evasion attacks before requests reach your backend services.

---

### Projects

#### [`traefik-warden`](https://github.com/routewarden/traefik-warden)
A security middleware plugin for [Traefik](https://traefik.io):
- **Scanner and Probe Defense**: Blocks automated scans looking for `.env`, configuration backups, credentials, and exposed admin panels.
- **Anti-Evasion Engine**: Normalizes complex path variations including multi-layer URL encoding (`%252e`), semicolon matrix parameters (`/;param/.env`), backslashes, and null bytes.
- **IP & CIDR Allowlisting**: Supports granular client IP filtering with `X-Forwarded-For`, `X-Real-IP`, or socket `RemoteAddr`.
- **Flexible Responses**: Return standard `404 Not Found` cloaking, `403 Forbidden`, custom JSON/HTML pages, Cloudflare Turnstile / hCaptcha challenges, silent TCP drops, or gzip bombs.
- **Pure Go**: Built with standard library Go for seamless Yaegi runtime compatibility without external dependencies.

#### [`caddy-warden`](https://github.com/routewarden/caddy-warden)
A native security module for the [Caddy](https://caddyserver.com) web server:
- **Native Caddy Middleware**: Plugs directly into the Caddy v2 HTTP pipeline and Caddyfile syntax.
- **Shared Protection Engine**: Uses RouteWarden's signature path normalization and zero-config sensitive path protection.
- **Declarative Caddyfile Directives**: Easy to configure alongside your existing proxy definitions.
- **High Throughput**: Minimal latency overhead, built to match Caddy's asynchronous architecture.

---

### Documentation & Resources

| Resource | Description |
|---|---|
| **[Interactive Playground](https://routewarden.github.io/docs/?playground=open)** | Test normalization rules, patterns, and response handling live in your browser. |
| **[Documentation](https://routewarden.github.io/docs/traefik/)** | Full guides, configuration reference, and architecture details. |
| **[Getting Started](https://routewarden.github.io/docs/traefik/getting-started)** | Quickstart setup with Docker Compose, Kubernetes, and Caddyfile. |
| **[Anti-Evasion Engine](https://routewarden.github.io/docs/core/anti-evasion)** | How path normalization and traversal protection work under the hood. |
| **[Recipes & Examples](https://routewarden.github.io/docs/examples/overview)** | Setup examples for **Immich**, [Zero-Trust Webooks](https://routewarden.github.io/docs/examples/case-study-webhooks), [Vaultwarden](https://routewarden.github.io/docs/examples/case-study-vaultwarden) and [Wordpress](https://routewarden.github.io/docs/examples/case-study-cms-shield). |

---

### Ecosystem

- **[`traefik-warden`](https://github.com/routewarden/traefik-warden)**: Traefik middleware plugin written in pure Go.
- **[`caddy-warden`](https://github.com/routewarden/caddy-warden)**: Caddy v2 HTTP middleware module.

---

### Contributing & Community

RouteWarden is open source and community-driven. We welcome contributions, bug reports, and suggestions.

- Read our [Contributing Guide](https://github.com/routewarden/.github/blob/main/.github/CONTRIBUTING.md) to get started.
- To report security issues, please review our [Security Policy](https://github.com/routewarden/.github/blob/main/.github/SECURITY.md).
- Star and follow our repositories on GitHub for updates.


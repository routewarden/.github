<div align="center">

  <img src="https://raw.githubusercontent.com/routewarden/traefik-warden/main/assets/icon.svg" alt="RouteWarden Logo" width="140" height="140" />

  # RouteWarden

  <p><strong>Open-source, high-performance security middleware and edge defense tools.</strong></p>

  <p>
    <a href="https://routewarden.github.io/traefik-warden/"><img src="https://img.shields.io/badge/Docs-VitePress%20Wiki-6366f1.svg?style=for-the-badge" alt="Documentation Site" /></a>
    <a href="https://github.com/routewarden/traefik-warden"><img src="https://img.shields.io/badge/Traefik%20Plugin-traefik--warden-blue.svg?style=for-the-badge&logo=traefik" alt="Traefik Plugin" /></a>
    <a href="https://github.com/routewarden/traefik-warden/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge" alt="MIT License" /></a>
  </p>

</div>

---

### 🛡️ About RouteWarden

**RouteWarden** is dedicated to building ultra-fast, robust, and zero-trust perimeter defense middleware for modern cloud and container architectures. 

Our mission is to safeguard modern reverse proxies, microservices, and container clusters from automated bot recon, credential discovery, directory traversal, and path-evasion attacks—**before malicious requests ever reach your backends.**

---

### 🚀 Flagship Project: [`traefik-warden`](https://github.com/routewarden/traefik-warden)

Our flagship middleware plugin for [Traefik](https://traefik.io) reverse proxy and ingress controller:

- 🛡️ **Anti-Probing & Scanner Defense**: Instantly intercept automated vulnerability crawlers looking for exposed secrets, configuration files, and unprotected admin panels.
- 📁 **Zero-Config File Protection**: Pre-configured protection against leaks of `.env*`, `.git`, `.aws`, `.sql`, `.bak`, `.conf`, `.yaml`, server logs, debug routes, and more.
- ⚡ **Anti-Evasion Engine**: Normalizes multi-layer URL encoding (`%252e%252e`), semicolon matrix parameters (`/;param/.env`), Windows backslashes (`\`), and null bytes (`%00`).
- 🌐 **IP & CIDR Subnet Whitelisting**: Granular bypass policies for corporate VPNs, office IPs, and developer subnets with support for `X-Forwarded-For`, `X-Real-IP`, and socket `RemoteAddr`.
- 🎭 **Multi-Mode Response Engine**:
  - `404 Not Found` (stealth mode cloaking) & `403 Forbidden`
  - Branded HTML / JSON API payloads
  - Interactive **Cloudflare Turnstile** & **hCaptcha** proof-of-work challenges
  - Silent TCP drops (`silentDrop`)
  - Active defense **Gzip Bomb** (`gzipBomb`) to stall automated vulnerability scanners.
-  Pure Go & Yaegi-native with **zero external dependencies**.

---

### 📚 Quick Links & Resources

| Resource | Description |
|---|---|
| 📖 **[Documentation & Wiki](https://routewarden.github.io/traefik-warden/)** | Full configuration guide, architecture walkthrough, and cookbooks. |
| ⚡ **[Getting Started](https://routewarden.github.io/traefik-warden/guide/getting-started)** | Quickstart installation with Docker Compose and Kubernetes IngressRoute. |
| 🔒 **[Anti-Evasion Engine](https://routewarden.github.io/traefik-warden/reference/anti-evasion)** | Deep-dive into URL normalization and traversal protection specs. |
| 🧪 **[Cookbooks & Case Studies](https://routewarden.github.io/traefik-warden/examples/overview)** | Production recipes for Immich, WordPress, Vaultwarden, Webhooks, and Prometheus. |

---

### 📦 Ecosystem & Repositories

- **[`traefik-warden`](https://github.com/routewarden/traefik-warden)**: Core Traefik middleware plugin written in pure Go.
- **[`routewarden-docs`](https://github.com/routewarden/routewarden-docs)**: Interactive VitePress documentation and case study cookbook.
- **[`.github`](https://github.com/routewarden/.github)**: Organization profile and global community templates.

---

### 🤝 Contributing & Community

RouteWarden is open source and community-driven. We welcome contributions, bug reports, and suggestions!

- Check out our [Contributing Guide](https://github.com/routewarden/.github/blob/main/.github/CONTRIBUTING.md) to get involved.
- For security vulnerabilities, review our [Security Policy](https://github.com/routewarden/.github/blob/main/.github/SECURITY.md).
- Follow the latest releases and updates on GitHub!

# Contributing to RouteWarden

Thank you for your interest in contributing to RouteWarden! We welcome contributions of all kinds: bug fixes, performance improvements, documentation enhancements, tests, and new features.

---

## Code of Conduct

All contributors and participants are expected to maintain an inclusive, respectful, and welcoming environment for everyone.

---

## How Can I Contribute?

### 1. Reporting Bugs
- Search existing issues to ensure the bug hasn't already been reported.
- Open an issue describing the problem in detail.
- Include your environment details (Gateway/Reverse proxy version, OS/Docker, RouteWarden configuration) and steps to reproduce.

### 2. Suggesting Enhancements
- Open an issue describing the proposed feature or improvement.
- Provide motivation and context on why this would benefit RouteWarden users across gateways.

### 3. Pull Requests
- Fork the repository and create a new branch from `main`.
- For Go projects (`traefik-warden`, `caddy-warden`): follow standard formatting (`go fmt` / `go vet`), keep external dependencies minimal, and ensure tests pass (`go test -v -race ./...`).
- For Lua projects (`nginx-warden`): follow Lua best practices, ensure PCRE JIT compatibility, and run the test runner (`./t/run_tests.sh`).
- Add or update unit and integration tests to verify your changes.
- Write clean, descriptive commit messages.
- Submit your PR with a clear description of the changes made.

---

## Security Disclosures

If you discover a security vulnerability, please refer to our [Security Policy](SECURITY.md). Do not submit security vulnerabilities via public pull requests or issues.

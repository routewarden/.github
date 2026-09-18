# Contributing to RouteWarden

Thank you for your interest in contributing to RouteWarden! We welcome contributions of all kinds: bug fixes, performance improvements, documentation enhancements, tests, and new features.

---

## Code of Conduct

All contributors and participants are expected to maintain an inclusive, respectful, and welcoming environment for everyone.

---

## How Can I Contribute?

### 1. Reporting Bugs
- Search existing issues to ensure the bug hasn't already been reported.
- Open an issue using the Bug Report template.
- Include your environment details (Traefik version, OS/Docker, plugin configuration) and steps to reproduce.

### 2. Suggesting Enhancements
- Open an issue describing the proposed feature or improvement.
- Provide motivation and context on why this would benefit RouteWarden users.

### 3. Pull Requests
- Fork the repository and create a new branch from `main`.
- Follow Go standard formatting (`go fmt` / `go vet`).
- Keep external dependencies minimal (core plugins must remain standard-library-only to ensure Yaegi compatibility).
- Add or update unit tests to verify your changes.
- Ensure all tests pass (`go test -v -race ./...`).
- Write clean, descriptive commit messages.
- Submit your PR with a clear description of the changes made.

---

## Security Disclosures

If you discover a security vulnerability, please refer to our [Security Policy](SECURITY.md). Do not submit security vulnerabilities via public pull requests or issues.

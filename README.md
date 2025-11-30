# .github-prompts
> Centralized GitHub Copilot instruction library that keeps every `frasermolyneux` repository aligned.

`No GitHub Actions workflows configured`
[![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-Not%20Configured-lightgrey)](https://github.com/frasermolyneux/.github-prompts/actions)

## 📌 Overview
Reusable instruction files under `instructions/` keep application, infrastructure, and documentation repos synchronized without duplicating prose, while `docs/` captures the prompt architecture so contributors can extend the library confidently before touching `instructions/*.instructions.md`.

## 🧱 Technology & Frameworks
- `Markdown (GitHub Flavored Markdown 2023 spec)`
- `YAML 1.2 front matter`
- `GitHub Actions composite prompt design (2025 guidance)`

## 📚 Documentation Index
- [docs/library-overview.md](https://github.com/frasermolyneux/.github-prompts/blob/main/docs/library-overview.md) – Mission, layout, and consumption model for the shared prompt library.
- [docs/authoring-new-instructions.md](https://github.com/frasermolyneux/.github-prompts/blob/main/docs/authoring-new-instructions.md) – Template plus checklist for creating additional `*.instructions.md` files.

## 🚀 Getting Started
**Highlights**
- Central repository for Copilot-ready prompts scoped via YAML front matter.
- `.github/prompts/` hosts composite prompts such as `update-readme` for multi-step changes.
- Documentation-first workflow ensures every new pattern ships with discoverable guidance.

**Sample Usage (optional)**
```markdown
---
applyTo: '**/*.cs'
---

## Context
- Keep .NET controllers, DTOs, and clients aligned across repos.

## Guidance
- Register typed HTTP clients via `IHttpClientFactory`.
- Enforce async suffixing with `CancellationToken` support.
- Return typed envelopes like `ApiResponse<T>`.
```

## 🛠️ Developer Quick Start
```shell
git clone https://github.com/frasermolyneux/.github-prompts.git
cd .github-prompts
code .
```

## 🤝 Contributing
Please read the [contributing](https://github.com/frasermolyneux/.github-prompts/blob/main/CONTRIBUTING.md) guidance; this is a learning and development project.

## 🔐 Security
Please read the [security](https://github.com/frasermolyneux/.github-prompts/blob/main/SECURITY.md) guidance; I am always open to security feedback through email or opening an issue.

## 📄 License
Distributed under the [GNU General Public License v3.0](https://github.com/frasermolyneux/.github-prompts/blob/main/LICENSE).

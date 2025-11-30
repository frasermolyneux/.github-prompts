# .github-prompts
> Centralized GitHub Copilot prompts and task templates for every `frasermolyneux` repository.

<!-- Badges -->
![Reference Library](https://img.shields.io/badge/Copilot%20Prompts-Reference%20Library-6f42c1)

## 📌 Overview
Reusable instruction files live under `instructions/` so app, infra, and documentation repos can share the same Copilot guidance without duplicating prose. The new `docs/` folder captures how the library is structured and how to author additional entries, giving contributors a single place to understand the prompt architecture before updating `instructions/*.instructions.md`.

## ⚙️ Workflow Status
| Workflow               | Status                                                                             | Purpose                                                                                       |
| ---------------------- | ---------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Repository maintenance | ![badge](https://img.shields.io/badge/GitHub%20Actions-Not%20Configured-lightgrey) | This repo only publishes reference content, so consuming projects run the automation instead. |

## 📚 Documentation Index
- [docs/library-overview.md](https://github.com/frasermolyneux/.github-prompts/blob/main/docs/library-overview.md) – Explains the mission, layout, and consumption model for the prompt library.
- [docs/authoring-new-instructions.md](https://github.com/frasermolyneux/.github-prompts/blob/main/docs/authoring-new-instructions.md) – Template and checklist for writing new `*.instructions.md` files.

## 🚀 Quickstart & Key Features
**Setup**
```shell
git clone https://github.com/frasermolyneux/.github-prompts.git
cd .github-prompts
code .
```

**Sample Usage**
```markdown
---
applyTo: '**/*.cs'
---

## Context
- Keep .NET clients, DTOs, and APIs aligned across repositories.

## Guidance
- Register typed HTTP clients via `IHttpClientFactory`.
- Enforce async suffixing and `CancellationToken` flow.
- Return typed envelopes like `ApiResponse<T>`.
```

**Highlights**
- Drop-in prompts scoped via YAML front matter so each repo only loads relevant guidance.
- Composite prompts in `.github/prompts/` (e.g., `update-readme.prompt.md`) orchestrate multi-step changes with consistent acceptance criteria.
- Documentation-driven workflow keeps instruction updates discoverable and reviewable across the org.

## 🧩 Related Projects
- [frasermolyneux/actions](https://github.com/frasermolyneux/actions) – Composite GitHub Actions that rely on the same instructions when building and deploying workloads.
- [frasermolyneux/portal-repository](https://github.com/frasermolyneux/portal-repository) – Backend/API repo that consumes these prompts to align controller, DTO, and Terraform changes.
- [frasermolyneux/api-client-abstractions](https://github.com/frasermolyneux/api-client-abstractions) – API client SDKs that reuse the shared C# guidance and documentation patterns defined here.

## 🤝 Contributing

Please read the [contributing](CONTRIBUTING.md) guidance; this is a learning and development project.

## 🔐 Security

Please read the [security](SECURITY.md) guidance; I am always open to security feedback through email or opening an issue.

## 📄 License
Distributed under the [GNU General Public License v3.0](https://github.com/frasermolyneux/.github-prompts/blob/main/LICENSE).

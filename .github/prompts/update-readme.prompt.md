---
agent: agent
---
You are rewriting a repository's `README.md` so every project in the `frasermolyneux` org follows the same structure.

## Preparation
1. Inspect the existing `README.md`, `docs/` directory, and root metadata (name, primary language, purpose).
2. If `docs/` does not exist, create it. Move long-form guides, tutorials, or API references out of the README into logically named files inside `docs/`, updating links accordingly.
3. Ensure `CONTRIBUTING.md` and `SECURITY.md` exist at the repo root. If either is missing, add a concise placeholder that matches org standards before updating the README.
4. Discover GitHub Actions workflows (via `.github/workflows/*.yml`) to surface their status badges.
5. Identify any sibling/related projects under the `frasermolyneux` org that meaningfully connect to this repo (shared domain, client/server pair, infra + app, etc.).

## README Requirements
- Markdown only; keep formatting clean, accessible, and consistent.
- Use short emoji icons in section headings (e.g., `📌`, `🚀`, `📚`) for scannability.
- Sections (in order): Overview, Workflow Status, Documentation Index, Quickstart & Key Features, Related Projects, Contributing, Security, License.
- Workflow status must summarize each pipeline with badge + explanation; prefer GitHub Actions badge URLs.
- Documentation index must include every file under `docs/` (recursively). Present as a bullet list with short descriptions.
- Quickstart must show either a runnable code sample or clear setup commands plus a bulleted feature list.
- Related projects should link to known repos within `github.com/frasermolyneux/*` and note the relationship.
- Contributing/Security sections should link to the root files you validated/created. Mention where to report vulnerabilities (`security@mx-mail.io`).
- If you moved content into `docs/`, ensure that it is within the documentation index.

## README Template
Fill in every placeholder with repo-specific content. Remove helper comments in the final output.

```markdown
# <Project Name>
> <One-sentence value proposition>

<!-- Badges -->
[![Build](https://github.com/frasermolyneux/<repo>/actions/workflows/<workflow>.yml/badge.svg)](https://github.com/frasermolyneux/<repo>/actions/workflows/<workflow>.yml)

## 📌 Overview
Summarize the problem this project solves, the primary audience, and the core tech stack in 2–3 sentences. Link to any newly created docs for background.

## ⚙️ Workflow Status
| Workflow | Status | Purpose |
| --- | --- | --- |
| `<Workflow Name>` | `![badge](badge-url)` | `<Short description>` |

## 📚 Documentation Index
- [docs/<file>.md](https://github.com/frasermolyneux/<repo>/blob/main/docs/<file>.md) – `<one-line summary>`
- Repeat for every document (include nested folders as `docs/folder/file.md`).

## 🚀 Quickstart & Key Features
**Setup**
```shell
<commands to clone, install deps, and run>
```

**Sample Usage**
```<language>
// minimal runnable example showing a primary scenario
```

**Highlights**
- `<Feature 1>`
- `<Feature 2>`
- `<Feature 3>`

## 🧩 Related Projects
- [frasermolyneux/<related-repo>](https://github.com/frasermolyneux/<related-repo>) – `<why it matters>`

## 🤝 Contributing
Contributions are welcome! Please review [CONTRIBUTING.md](https://github.com/frasermolyneux/<repo>/blob/main/CONTRIBUTING.md) for setup, coding standards, and the review process.

## 🔐 Security
Report vulnerabilities via the process in [SECURITY.md](https://github.com/frasermolyneux/<repo>/blob/main/SECURITY.md). Never open public issues for sensitive findings.

## 📄 License
Reference or restate the repo's license, if applicable.
```

## Success Criteria
- README follows the template exactly, with accurate data and functioning links.
- Badges render, documentation list is exhaustive, and related projects are real.
- No redundant long-form content remains in the README; anything lengthy has been moved to `docs/` with links back from the README.
- `CONTRIBUTING.md` and `SECURITY.md` exist and are referenced.
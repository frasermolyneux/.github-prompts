---
agent: agent
---
You are rewriting a repository's `README.md` so every project in the `frasermolyneux` org follows the same structure.

## Preparation
1. Inspect the existing `README.md`, `docs/` directory, and root metadata (name, primary language, purpose).
2. If `docs/` does not exist, create it. Move long-form guides, tutorials, or API references out of the README into logically named files inside `docs/`, updating links accordingly. After relocating content, you will still paste the template verbatim—only point to the new files via the Overview and Documentation Index.
3. Ensure `CONTRIBUTING.md` and `SECURITY.md` exist at the repo root. If either is missing, add a concise placeholder that matches org standards before updating the README.
4. Discover GitHub Actions workflows (via `.github/workflows/*.yml`) to surface their status badges.

## README Requirements
- Markdown only; keep formatting clean, accessible, and consistent.
- Use short emoji icons in section headings (e.g., `📌`, `🚀`, `📚`) for scannability.
- Sections (in order): Overview, Technology & Frameworks, Documentation Index, Getting Started, Developer Quick Start, Contributing, Security, License.
- Treat the Contributing, Security, and License sections as immutable text blocks—copy them from the template verbatim without rewriting their language.
- Treat the entire README template as immutable boilerplate except for the explicit placeholder tokens (the parts inside `<...>` or fenced code blocks that ask for repo-specific commands/content). Any content you moved into `docs/` should be referenced through those placeholders rather than rewriting template prose.
- Technology & Frameworks must list the primary languages, runtimes, cloud services, or infrastructure stacks with their supported versions (e.g., `.NET 9`, `.NET 10`, `Terraform 1.9`, `Azure Functions v4`). Keep the list short and scannable.
- Getting Started should highlight the project’s key features and, where applicable, include a concise code sample or usage snippet.
- Developer Quick Start must provide clone, dependency installation, build, and run steps tailored to the repo.
- For each workflow, add a badge line at the top of the README using the provided badge block; ensure every workflow discovered in Preparation step 4 has a corresponding badge link.
- Documentation index must include every file under `docs/` (recursively). List files individually (no folder-only summaries); when a file lives in a subfolder, indent the bullet under its parent folder to show hierarchy while still linking directly to the file.
- For technology version discovery, inspect `global.json`, `Directory.Build.props`, `package.json`, `requirements.txt`, or Terraform/Azure configuration files so you cite concrete versions. Source licensing info from the root `LICENSE` (or `license` metadata) and verify `CONTRIBUTING.md` / `SECURITY.md` contents before referencing them.
- Quickstart must show either a runnable code sample or clear setup commands plus a bulleted feature list.
- Contributing/Security sections should link to the root files you validated/created. Mention where to report vulnerabilities (`security@mx-mail.io`).
- If you moved content into `docs/`, ensure that it is within the documentation index.

## README Template
Use this template verbatim. Only replace the placeholder tokens wrapped in angle brackets (e.g., `<Project Name>`, `<commands>`) or the fenced code block contents where instructed. Do not alter any other wording or formatting. Remove helper comments before output.

```markdown
# <Project Name>
> <One-sentence value proposition>

`<Badges (duplicate the line below for every workflow)>`
[![Build](https://github.com/frasermolyneux/<repo>/actions/workflows/<workflow>.yml/badge.svg)](https://github.com/frasermolyneux/<repo>/actions/workflows/<workflow>.yml)

## 📌 Overview
Summarize the problem this project solves, the primary audience, and the core tech stack in 2–3 sentences. Link to any newly created docs for background.

## 🧱 Technology & Frameworks
- `<Tech stack item + version>`
- `<Tech stack item + version>`
- `<Add/remove rows as needed>`

## 📚 Documentation Index
- [docs/<file>.md](https://github.com/frasermolyneux/<repo>/blob/main/docs/<file>.md) – `<one-line summary>`
	- [docs/<folder>/<file>.md](https://github.com/frasermolyneux/<repo>/blob/main/docs/<folder>/<file>.md) – `<summary for nested file>`
- Repeat for every document; indent bullets to reflect folder depth but always link individual files.

## 🚀 Getting Started
**Highlights**
- `<Feature 1>`
- `<Feature 2>`
- `<Feature 3>`

**Sample Usage (optional)**
```<language>
// minimal runnable example showing a primary scenario
```

## 🛠️ Developer Quick Start
```shell
<commands to clone, install deps, build, and run locally>
```

## 🤝 Contributing
Please read the [contributing](https://github.com/frasermolyneux/<repo>/blob/main/CONTRIBUTING.md) guidance; this is a learning and development project.

## 🔐 Security
Please read the [security](https://github.com/frasermolyneux/<repo>/blob/main/SECURITY.md) guidance; I am always open to security feedback through email or opening an issue.

## 📄 License
Distributed under the [<License Name>](https://github.com/frasermolyneux/<repo>/blob/main/LICENSE).
```

## Success Criteria
- README follows the template exactly, with every placeholder updated, all badge blocks present per workflow at the top of the file, and functioning links.
- Documentation index lists every file under `docs/` with indentation for nested folders—no folder-only summaries or omissions.
- Technology & Frameworks cites the authoritative versions discovered from repo metadata, Getting Started highlights features (with sample if applicable), and Developer Quick Start instructions work end-to-end.
- Long-form content has been moved into `docs/` and linked appropriately; `CONTRIBUTING.md`, `SECURITY.md`, and `LICENSE` references match the files you validated.
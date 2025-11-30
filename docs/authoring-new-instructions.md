# Authoring New Instruction Files

## Prerequisites
- Confirm the scenario already exists in a shipping repository; this library documents proven patterns, not proposals.
- Identify which files should receive the guidance and define a tight glob expression for the `applyTo` front matter.

## File Template
```
---
applyTo: 'path/glob/**'
---

## Context
Explain what problem the guidance solves.

## Guidance
- Use imperative bullets ("Register typed clients via IHttpClientFactory").
- Reference concrete APIs, commands, or file paths that already work.
- Keep entries between 20-50 lines for fast ingestion by agents.
```

## Review Checklist
- Titles describe the technology or workflow clearly (`csharp.instructions.md`, `terraform-platform-workloads.instructions.md`).
- Sections follow Markdown `##` headings with short bullet lists.
- All code snippets are ASCII, and indentation inside tables/blocks uses two spaces.
- Cross-reference existing docs only when necessary; files should remain understandable in isolation.

Submit a pull request that updates both the new instruction file and any related documentation (like the README or `docs/` index) so consumers can discover the change quickly.
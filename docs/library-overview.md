# Prompt Library Overview

## Purpose
- Provide a single source of truth for GitHub Copilot instructions that every `frasermolyneux` repository can import verbatim.
- Keep prompts concise, stable, and scoped so automated agents do not need to search across repositories for guidance.
- Document only patterns that already ship in production repositories to avoid aspirational guidance.

## Layout
- `instructions/` houses every prompt file. Each entry targets its audience via YAML front matter, such as `applyTo: "**/*.cs"` for .NET guidance or `applyTo: "terraform/**"` for platform Terraform stacks.
- `.github/prompts/` contains reusable higher-level prompts (for example `update-readme.prompt.md`) that orchestrate multi-step changes across repositories.
- Root metadata (`README.md`, `LICENSE`, `CONTRIBUTING.md`, `SECURITY.md`) mirrors what downstream projects expect when they sync this repo into their workspace.

## Consumption
1. Each workspace adds this repo under `.github-prompts/` (sometimes alongside other prompt libraries) and references the relevant instruction files from its Copilot configuration.
2. Composite prompts (like the Update README workflow) are invoked via `@instructions` blocks so every workspace uses the same acceptance criteria.
3. When a consuming repository adds a new pattern, update or add an instruction file here first so future workspaces inherit the behavior automatically.

Keep instruction files self-contained: an agent should understand the domain without opening other files. If a topic grows, add a new instruction file with a narrower `applyTo` glob instead of expanding an existing one beyond 50 lines.
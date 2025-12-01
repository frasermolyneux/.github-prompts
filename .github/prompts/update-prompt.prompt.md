---
agent: agent
---
## Mission
- Refresh or author prompts in `.github-prompts` so every `frasermolyneux` repo receives the same high-signal Copilot guidance.
- Capture the minimum knowledge an AI agent needs to ship code without rereading the whole repository.

## Prep Checklist
- Run a single glob search for `**/.github/prompts` to reuse any existing conventions (tone, headings, length).
- Skim `README.md`, `docs/`, and root config to learn the architecture, workflows, and domain terms before editing.
- When a prompt already exists, merge rather than replace; preserve accurate guidance and only rewrite stale or missing pieces.

## Writing the Prompt
- Keep the body 20-50 short lines using `##` headings plus terse bullets, mirroring `update-readme.prompt.md` style.
- Lead with context: what the repo delivers, how it is structured (layers, services, pipelines), and why those choices matter.
- Document developer workflows that require specific commands (build, test, deploy, debugging) including exact CLI invocations.
- Highlight cross-cutting conventions: naming schemes, dependency injection patterns, envelopes (e.g., `ApiResponse<T>`), Terraform layout, Azure auth, etc.
- Reference concrete files or folders (`instructions/csharp.instructions.md`, `terraform/environments/{env}`, `.github/workflows/*.yml`) so agents know where to look for proof.
- Call out external integrations (Azure resources, APIs, messaging) and describe how data moves between components.

## Output Expectations
- Make every bullet actionable (“Run `dotnet test` with `--filter Category=Smoke`”) rather than generic advice.
- Avoid aspirational guidance; only document patterns that the current codebase already follows.
- Mention required tools, secrets, or environment variables so agents avoid dead ends.
- When the repo spans multiple stacks, segment guidance per stack with subheadings or grouped bullets.

## Final Steps
- Close with a reminder asking the user what needs clarification so the prompt can iterate.
- Before saving, reread the entire file as if it will be pasted verbatim into another project; trim redundancies.
- Confirm instructions remain ASCII-only and self-contained (no dependency on other files).
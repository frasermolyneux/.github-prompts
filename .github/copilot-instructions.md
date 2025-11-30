# Copilot Instructions

## Mission
- Treat this repo as a portable prompt library: every workspace imports these guides verbatim, so clarity and stability beat experimentation.
- Keep files self-contained so agents can understand a domain without chasing context from other repos.
- Write only what is already true in shipping projects; these instructions are reference material, not wish lists.

## Layout & Scope
- All guidance lives under `instructions/*.instructions.md`; each file begins with YAML front matter (`applyTo:` glob) that limits which files receive the prompt.
- Use specific globs such as `**/*.cs` or `terraform/**` so rules never bleed into unrelated stacks when the library is copied elsewhere.
- Organize the body with `##` headings and short bullet lists; aim for 20–50 lines so downstream prompts stay under token caps.

## Writing Playbook Entries
- Lead with context (“what problem this solves”) followed by concrete how-to bullets and examples from real codebases.
- Favor direct imperatives (“Register typed clients via `IHttpClientFactory`”) over prose paragraphs.
- Mirror terminology from the consuming repositories (e.g., `ApiResponse<T>`, `platform-workloads`) so agents can match patterns quickly.
- When documenting commands, capture the exact invocation that already works (`dotnet`, `terraform`, etc.) rather than pseudo-code.

## Current Reference Files
- `instructions/csharp.instructions.md` captures the .NET client patterns: layered namespaces, async suffixing with `CancellationToken`, envelopes like `ApiResponse<T>`, Polly retries, dependency injection, and centralized auth helpers.
- `instructions/terraform-platform-workloads.instructions.md` describes the Azure Terraform flow: platform-workloads registration, `terraform/environments/{env}` layout, `modules/` reuse, naming such as `rg-{workload}-{environment}-uksouth`, and OIDC-only authentication in GitHub Actions.
- Use these as templates when drafting new guides so tone, formatting, and depth remain consistent.

## Quality Checks
- Before committing, re-read the file as if it will be pasted directly into an agent prompt—remove any redundant wording or ambiguous verbs.
- Confirm that every requirement can be enforced in practice; delete or restate anything that depends on manual discipline you cannot guarantee.
- Stick to ASCII, two-space indentation inside tables/code blocks, and Markdown that renders cleanly in GitHub preview.

## Maintenance Tips
- When a consuming repo adopts a new pattern, add or adjust the corresponding `.instructions.md` in this library immediately so future workspaces inherit it.
- If a topic grows large, create another instruction file with a tighter `applyTo` glob instead of overloading an existing guide.
- Update `README.md` only when repository-wide behavior changes (for example, adding a new instruction category or tooling requirement).

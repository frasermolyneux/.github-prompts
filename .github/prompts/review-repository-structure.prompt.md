---
agent: ask
---

## Mission
- Evaluate a `frasermolyneux` repository against the shared layout followed by `portal-repository`, `api-client-abstractions`, and `actions`.
- Report findings only; never change files.

## Prep Checklist
- Read root `README.md`, `CONTRIBUTING.md`, `SECURITY.md`, `LICENSE`, and `version.json`.
- Inspect `.github/` for `copilot-instructions.md`, optional `prompts/`, and workflow definitions.
- List top-level folders to confirm `src/`, `docs/`, `scripts/`, `terraform/`, or action folders exist.

## Required Structure
- Root docs: `README.md` plus a populated `docs/` tree like `portal-repository/docs/api-design-v2.md`.
- Governance files: `CONTRIBUTING.md`, `SECURITY.md`, `LICENSE`, and `version.json` at the repo root.
- Source hierarchy: application code under `src/` (e.g., `portal-repository/src`, `api-client-abstractions/src`) or composite action folders for `actions`.
- Infrastructure: Terraform isolated in `terraform/` (as in `portal-repository/terraform`) or explicitly documented if absent.
- Automation: scripts in `scripts/` and `.github/workflows/*.yml` plus `.github/copilot-instructions.md` to guide agents.
- Prompt library: `.github/prompts/` when the repo needs reusable prompts; note the gap if missing.

## Output
- For each repository under review, print a bold header (e.g., `**portal-repository**`) followed by one Markdown table.
- Each table must include a header row `|Check|Status|Comment|` and a separator row `|---|---|---|` so chat renders a proper table.
- Status must use `✅` for pass and `❌` for fail; explain failures briefly ("Missing SECURITY.md").
- Use one row per Required Structure bullet so stakeholders can compare repos quickly.
- Keep tables tight—do not add extra prose between rows or outside the required columns.

## Review Rules
- Base judgments on the current tree only; do not assume pending work.
- When a folder is intentionally absent (for example, no Terraform in the `actions` repo), mark `FAIL` and state the rationale so owners can decide next steps.
- Keep the response under 200 words and avoid remediation instructions—just report compliance.

## Final Step
- Ask which checklist items need clarification so the standard can keep improving.

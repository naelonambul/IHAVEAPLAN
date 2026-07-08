# AGENTS.md

This repository contains reusable planning templates for LLM and coding agents.

## File naming

Use this convention:

- `README.md` is the human-facing repository entrypoint.
- `AGENTS.md` is the agent-facing repository entrypoint.
- Workflow templates use lowercase kebab-case names.
- Unit folders use lowercase kebab-case names; inside each unit, keep conventional uppercase `README.md` and `SUMMARY.md`, and lowercase prompt/context files.

Current workflow templates:

- `brainstorm.md`
- `research-summary.md`
- `plan.md`
- `work-units.md`
- `unit-00-example/`

## Workflow

Start from the user's certainty level:

- Vague idea, unstable wedge, or many unexplored options: use `brainstorm.md`.
- Direction chosen but decisions need evidence: use `research-summary.md`.
- Direction and evidence are settled: use `plan.md`.
- Approved plan ready for execution breakdown: use `work-units.md`.
- TDD task-folder structure needed: copy `unit-00-example/`.

When applying these templates to another project, copy filled planning files into that project's root unless the project already has a docs convention. Copy unit folders to `tasks/unit-NN-short-name/` or the project's equivalent task directory.

## Style rules

Keep outputs:

- project-agnostic
- concise
- validation-oriented
- explicit about assumptions, risks, and open questions

Preserve the separation between files:

- `brainstorm.md` explores a problem and chooses a tentative direction.
- `research-summary.md` records evidence and rejected options.
- `plan.md` defines executable implementation scope and checkpoints.
- `work-units.md` breaks an approved plan into agent-sized work units.
- `unit-00-example/` provides a concrete TDD folder shape for one executable unit.

# IHAVEAPLAN

Procedural planning templates for automation-oriented LLMs and coding agents.

This repository exists for a simple reason:

> When an automation LLM needs a plan, it should have somewhere concrete to start.

The core file is [`plan.md`](./plan.md). It is a reusable implementation-plan template designed to help an automation LLM turn vague goals, product requirements, issues, or design notes into an executable plan with scope, decisions, milestones, validation, risks, and definition of done.

When the idea is still vague — no settled wedge, unstable hypotheses, too many options, no first milestone — [`brainstorm.md`](./brainstorm.md) is an **optional** front door. It is **problem-first** (reframe the idea as a problem: whose pain, why the current workaround is insufficient), exploratory, and disposable: it compares candidate directions and produces the research questions to carry forward, without making implementation decisions.

When technical choices need evidence, [`research-summary.md`](./research-summary.md) can be used to capture findings, rejected options, risks, and references before or alongside the plan.

When the plan is approved, [`work-units.md`](./work-units.md) can be used to break that plan into executable work units for agents.

For a concrete TDD unit-folder shape, copy [`unit-00-example/`](./unit-00-example/).

## What This Is

`IHAVEAPLAN` is not a framework, library, or application.

It is a procedural document set for LLM-driven software implementation work. It is meant to be copied, adapted, and filled in by automation agents before execution begins.

Use it when you want a plan that answers:

- What are we building?
- What is in scope and out of scope?
- What decisions are already finalized?
- What interfaces and contracts matter?
- What should be validated before implementation?
- What milestones reduce uncertainty first?
- What risks, open questions, and completion criteria exist?

## Recommended Workflow

Use the documents in this order. **You can enter at any stage** — start where your
certainty actually is, and skip stages that are already settled.

0. [`brainstorm.md`](./brainstorm.md) *(optional)* - Start here when the idea is
   vague: explore candidate directions/wedges, constraints, and first milestones,
   pick a tentative direction, and produce research questions. Skip it when the
   direction and wedge are already clear.
1. [`research-summary.md`](./research-summary.md) - Capture evidence, rejected options, risks, and technical findings when decisions need research. (Seed §1 from the research questions produced by `brainstorm.md`.)
2. [`plan.md`](./plan.md) - Turn requirements and research into an implementation plan.
3. [`work-units.md`](./work-units.md) - Break the approved plan into executable units with dependencies and validation.
4. [`unit-00-example/`](./unit-00-example/) - Copy for each TDD work unit and fill in `context.md`, `prompt-test.md`, `prompt-impl.md`, and `SUMMARY.md`.
5. [`unit-00-example/SUMMARY.md`](./unit-00-example/SUMMARY.md) - Record reviewer evaluation, validation evidence, findings, and downstream readiness after the unit is implemented.

Where to start:

- **Vague idea, unstable wedge, too many options** → `brainstorm.md`.
- **Direction chosen, decisions need evidence** → `research-summary.md`.
- **Direction and evidence are settled** → `plan.md`.

`brainstorm.md` is deliberately lighter than `research-summary.md`, requires no
citations, and makes no final decisions — it only chooses a direction to
investigate and hands off the questions.

## For LLMs and Agents

If you are an LLM or coding agent and a user asks you to make a plan, read [`plan.md`](./plan.md) first.

Then:

0. If the user only has a vague idea — no chosen wedge, unstable hypotheses, many unexplored options — start with [`brainstorm.md`](./brainstorm.md) to choose a tentative direction and produce research questions **before** planning. Do not jump from a vague idea straight to `plan.md`. Skip this step when the direction is already clear.
1. Use [`research-summary.md`](./research-summary.md) first if the plan depends on technical research, external systems, platform behavior, libraries, standards, or unstable facts.
2. Replace placeholders with project-specific details.
3. Identify assumptions, unknowns, and source documents.
4. Define the goal, scope, contracts, and data flow.
5. Create milestones in dependency order.
6. Put validation before implementation.
7. Make risks, decision points, and open questions explicit.
8. Do not treat a milestone or unit as complete until its checkpoint is satisfied.

The template is intentionally strict because weak plans usually fail at the boundaries: unclear scope, undocumented assumptions, missing failure cases, unstable interfaces, and no measurable definition of done.

## For Human Operators

Human operators can seed an agent workflow by copying the templates into a project:

```bash
cp plan.md ./your-project/plan.md
```

To start from a vague idea (optional), copy the brainstorm front door first:

```bash
cp brainstorm.md ./your-project/brainstorm.md
```

Then have the LLM fill it out before implementation, attaching the result to an issue, PR, design review, or project handoff when useful.

To capture research behind the plan:

```bash
cp research-summary.md ./your-project/research-summary.md
```

To split an approved plan into implementation chunks:

```bash
cp work-units.md ./your-project/work-units.md
```

To create a TDD work-unit folder:

```bash
cp -R unit-00-example ./your-project/tasks/unit-01-your-unit-name
```

You can also ask an LLM to use it directly:

```text
Read https://github.com/naelonambul/IHAVEAPLAN/blob/main/plan.md
and create an implementation plan for this project.
```

## Planning Principles

This template is built around a few practical rules:

- Reduce uncertainty early.
- Define observable behavior before implementation.
- Write validation before production work.
- Keep interfaces and contracts explicit.
- Schedule foundations before dependent work.
- Treat failure paths, retries, recovery, and edge cases as first-class work.
- Record open questions instead of hiding them inside implementation.

## Repository Contents

| File | Purpose |
| --- | --- |
| [`AGENTS.md`](./AGENTS.md) | Repo-level guidance for coding agents and automation LLMs |
| [`brainstorm.md`](./brainstorm.md) | *Optional* front door for a vague idea: explore candidate directions/wedges, constraints, and first milestones, choose a tentative direction, and emit research questions |
| [`research-summary.md`](./research-summary.md) | Template for research findings, evidence-backed decisions, rejected options, risks, and references |
| [`plan.md`](./plan.md) | Reusable implementation-plan template |
| [`work-units.md`](./work-units.md) | Template for breaking a plan into executable work units |
| [`unit-00-example/`](./unit-00-example/) | Example TDD unit folder with context, RED prompt, GREEN + REFACTOR prompt, and reviewer summary |
| [`README.md`](./README.md) | Repository overview and usage guide |

## Adjusting

Changes should make the templates easier for automation LLMs to follow.

Good adjustments usually:

- improve planning clarity
- make the template easier for LLMs to follow
- add missing implementation checkpoints
- improve validation, risk, or decision sections
- keep the template technology-agnostic

Avoid project-specific assumptions unless they are presented as replaceable examples.

## License

No license has been added. This repository is currently a public reference for automation LLM workflows, not a packaged library.

# IHAVEAPLAN

An implementation plan template for LLMs, agents, and humans who need a clear plan before building.

This repository exists for a simple reason:

> When an LLM needs a plan, it should have somewhere concrete to start.

The core file is [`plan.example.md`](./plan.example.md). It is a reusable implementation-plan template designed to help an LLM turn vague goals, product requirements, issues, or design notes into an executable plan with scope, decisions, milestones, validation, risks, and definition of done.

## What This Is

`IHAVEAPLAN` is not a framework, library, or application.

It is a planning document template for software implementation work. It is meant to be copied, adapted, and filled in before execution begins.

Use it when you want a plan that answers:

- What are we building?
- What is in scope and out of scope?
- What decisions are already finalized?
- What interfaces and contracts matter?
- What should be validated before implementation?
- What milestones reduce uncertainty first?
- What risks, open questions, and completion criteria exist?

## For LLMs and Agents

If you are an LLM or coding agent and a user asks you to make a plan, read [`plan.example.md`](./plan.example.md) first.

Then:

1. Replace placeholders with project-specific details.
2. Identify assumptions, unknowns, and source documents.
3. Define the goal, scope, contracts, and data flow.
4. Create milestones in dependency order.
5. Put validation before implementation.
6. Make risks, decision points, and open questions explicit.
7. Do not treat a milestone as complete until its checkpoint is satisfied.

The template is intentionally strict because weak plans usually fail at the boundaries: unclear scope, undocumented assumptions, missing failure cases, unstable interfaces, and no measurable definition of done.

## For Humans

Copy the template into your project:

```bash
cp plan.example.md PLAN.md
```

Then fill it out before starting implementation, attaching it to an issue, PR, design review, or project handoff.

You can also ask an LLM to use it directly:

```text
Read https://github.com/naelonambul/IHAVEAPLAN/blob/main/plan.example.md
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
| [`plan.example.md`](./plan.example.md) | Reusable implementation-plan template |
| [`README.md`](./README.md) | Repository overview and usage guide |

## Contributing

Issues and pull requests are welcome if they make the template more useful across projects.

Good contributions usually:

- improve planning clarity
- make the template easier for LLMs to follow
- add missing implementation checkpoints
- improve validation, risk, or decision sections
- keep the template technology-agnostic

Avoid project-specific assumptions unless they are presented as replaceable examples.

## License

No license has been added yet. Add an explicit open-source license before relying on this repository for public reuse terms.

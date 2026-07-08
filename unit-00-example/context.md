# Unit 00 - [Unit Name] - Context

## Why

[Explain why this unit exists. Link it to `plan.md`, `work-units.md`, a milestone, issue, PRD, design decision, bug, or risk.]

## Goal

[State the observable behavior, contract, or integration this unit must deliver.]

## Current State

[Describe the repository baseline before this unit starts.]

- Existing files or modules:
  - `[path]` - [current responsibility]
- Existing tests:
  - `[path]` - [what is already covered]
- Existing gaps:
  - [Missing behavior, missing contract, missing fixture, broken flow, or known risk]

## Design Decided by Planning

[Record decisions that the test and implementation agents should not reopen.]

- [Decision 1]
- [Decision 2]
- [Decision 3]

## Scope

This unit includes:

- [Behavior, API, fixture, migration, config, or user-facing slice]
- [Validation artifact]
- [Documentation or handoff artifact]

This unit excludes:

- [Deferred behavior]
- [Dependent unit]
- [Planning question that must not be solved ad hoc]

## Dependencies

Required before this unit starts:

- [Prior unit / contract / decision / fixture / environment]

Downstream units that depend on this:

- [Unit ID / feature / integration]

## Invariants

These rules must remain true:

- [Existing suite or behavior stays green]
- [No incompatible contract change]
- [No hidden dependency on live or unstable systems]
- [Privacy, security, performance, or compatibility rule]

## Validation Strategy

Validation should cover:

- Valid input or happy path
- Invalid input
- Missing or partial input
- Boundary values
- Duplicate or repeated execution
- Retry, timeout, fallback, or unavailable dependency if relevant
- Regression coverage for any existing behavior this unit touches

## Fixtures and Test Assets

Required assets:

- [Fixture / golden output / mock / stub / sample file]

Asset rules:

- [How to refresh stale fixtures]
- [How to gate integration fixtures that require a special host, device, or service]
- [How to avoid relying on live unstable systems in blocking tests]

## References

- [`plan.md`](../plan.md)
- [`research-summary.md`](../research-summary.md)
- [`work-units.md`](../work-units.md)
- [Requirement, issue, design doc, API doc, or research note]

## Escalation Triggers

Stop and return to planning if:

- A required contract must change outside this unit's scope.
- A fixture or external dependency makes the validation nondeterministic.
- The implementation needs a new user-facing behavior not listed in scope.
- The failing test reveals that the planned behavior contradicts existing accepted behavior.

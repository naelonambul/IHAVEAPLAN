# Unit 00 - Example TDD Work Unit

This folder is a reusable example structure for one TDD work unit.

Use it after `PLAN.md` and `work-units.md` have identified a concrete unit of work. Copy this folder, rename it to the real unit number and slug, then replace placeholders in each file.

```bash
cp -R unit-00-example unit-01-your-unit-name
```

## Folder Contract

Each unit folder should contain:

| File | Purpose |
| --- | --- |
| `context.md` | Planning context, current state, decisions, dependencies, and invariants |
| `prompt-test.md` | RED prompt: failing validation first, with only minimal sentinel stubs if needed |
| `prompt-impl.md` | GREEN + REFACTOR prompt: implement against the red tests, then clean up safely |
| `SUMMARY.md` | Reviewer evaluation, validation evidence, findings, follow-up, and commit history |

Optional files after execution:

| File | Purpose |
| --- | --- |
| `RESULTS.md` | Fixture, benchmark, or manual verification results |
| `ESCALATION.md` | Blocking issue that must return to planning |

## Execution Order

1. Read `context.md`.
2. Run the `prompt-test.md` work.
3. Confirm the build still compiles and the new behavioral tests fail for the expected reason.
4. Run the `prompt-impl.md` work.
5. Confirm the target suite and full relevant suite pass.
6. Record summary, risks, and follow-up work.

## TDD Rules

- The test step may add stubs only to make the build compile.
- Stub bodies must return sentinel values or throw typed `notImplemented` errors. Do not use crash-only placeholders such as `fatalError`.
- The implementation step must confirm the new suite is red before writing production logic.
- Tests are the specification once the RED commit lands.
- Production code should be the minimum needed to turn the approved validation green.
- Refactoring happens only while tests remain green.
- Any change to test expectations during implementation must be justified in the commit body or summary.

## Naming

Use stable numeric prefixes so dependencies are easy to scan:

```text
unit-01-domain-behavior
unit-02-integration-boundary
unit-03-user-facing-flow
```

Commit message examples:

```text
test(unit-01): failing specs for domain behavior (Red)
feat(unit-01): domain behavior green
refactor(unit-01): extract shared parser
```

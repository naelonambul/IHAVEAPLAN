# Unit 00 - Example TDD Work Unit

This folder is a reusable example structure for one TDD work unit.

Use it after `plan.md` and `work-units.md` have identified a concrete unit of
work. Copy this folder, rename it to the real unit number and slug, then apply the
project's `planning-contract.md`. Approve `context.md` before execution and
replace every placeholder in snapshotted files.

```bash
cp -R unit-00-example unit-01-your-unit-name
```

## Folder Contract

Each unit folder should contain:

| File | Purpose |
| --- | --- |
| `context.md` | Authoritative versioned execution contract: identity, provenance, boundaries, dependencies, instructions, validation, and approvals |
| `prompt-test.md` | Derived RED instructions; cannot override `context.md` |
| `prompt-impl.md` | Derived GREEN + REFACTOR instructions; cannot override `context.md` |
| `SUMMARY.md` | Generated reviewer evaluation and execution evidence |

Optional files after execution:

| File | Purpose |
| --- | --- |
| `RESULTS.md` | Fixture, benchmark, or manual verification results |
| `ESCALATION.md` | Blocking issue that must return to planning |

## Execution Order

1. Approve `context.md`; derive prompts and record their digests.
2. Snapshot and verify the contract, source revision, sources, dependencies, boundaries, shared resources, approvals, and artifact digests.
3. Run `prompt-test.md` and accept RED only when it matches the contract's behavioral failure semantics.
4. Run `prompt-impl.md` against the unchanged approved contract.
5. Capture the required targeted and full-suite GREEN evidence.
6. Record summary, provenance, risks, and follow-up work.

## TDD Rules

- The test step may add stubs only to make the build compile.
- Stub bodies must return sentinel values or throw typed `notImplemented` errors. Do not use crash-only placeholders such as `fatalError`.
- The implementation step must confirm the new suite is red before writing production logic.
- Tests are executable evidence for the approved unit contract; they do not supersede it.
- Production code should be the minimum needed to turn the approved validation green.
- Refactoring happens only while tests remain green.
- Any change to a contracted test expectation requires the reapproval or replanning declared in `context.md`; a commit note alone is insufficient.

## Naming

Use stable numeric prefixes so dependencies are easy to scan:

```text
unit-01-domain-behavior
unit-02-integration-boundary
unit-03-user-facing-flow
```

Inside each unit folder, keep conventional uppercase `README.md` and `SUMMARY.md`, and lowercase `context.md`, `prompt-test.md`, and `prompt-impl.md`.

Commit message examples:

```text
test(unit-01): failing specs for domain behavior (Red)
feat(unit-01): domain behavior green
refactor(unit-01): extract shared parser
```

# Test Subagent Prompt - Unit 00: [Unit Name] (RED)

You write failing validation first.

Read `context.md`, `plan.md`, and `work-units.md` before making changes. Your job is to specify behavior with tests, fixtures, contracts, or acceptance specs. Do not implement production behavior in this step.

## Repo

[Repository path, package/app structure, test framework, language/runtime, and relevant commands.]

Example:

```bash
[build command]
[targeted test command]
```

## Precondition

- [ ] Required prior units or decisions are present.
- [ ] Existing relevant tests pass before adding new RED tests, or known failures are documented.
- [ ] The intended public/internal API shape is clear enough to test.

## API Under Specification

Define or evolve the smallest API needed for the tests.

If the API does not exist yet, add minimal stubs so the build compiles. Stub bodies must return sentinel values or throw a typed `notImplemented` error. Do not use crash-only placeholders such as `fatalError`, `todo!`, or equivalent.

```text
[Type / function / endpoint / file / schema under specification]
[Expected inputs]
[Expected outputs]
[Error states]
```

Stub expectations:

- [Stub behavior that makes the test fail predictably]
- [Files where stubs may be placed]
- [Files that must not be touched]

## Test Assets

Create or update only the assets required to express the behavior.

- [Mock / fake / fixture / golden output]
- [Spec file for a future UI, device, host, or integration test]
- [Disabled or gated integration test with a clear enable condition]

Asset rules:

- Fixtures must be deterministic.
- Golden outputs must be reviewable.
- Live services should be behind mocks, recordings, or non-blocking smoke checks.
- Integration tests that require special infrastructure must be explicitly tagged, skipped, or documented.

## Required Suites

Create or update the following validation.

### A. [Suite Name]

Location: `[test path]`

Cover:

1. [Happy path]
2. [Invalid input]
3. [Missing or partial input]
4. [Boundary value]
5. [Duplicate / repeated execution]
6. [Failure, timeout, retry, fallback, or unavailable dependency]
7. [Regression for existing behavior]

### B. [Contract / Integration / Spec Suite]

Location: `[test path or spec path]`

Cover:

1. [Boundary contract]
2. [Fixture or golden comparison]
3. [Gated integration path]

## Red-State Requirement

After this step:

- [ ] The project builds.
- [ ] The new suite fails for the expected reason.
- [ ] Existing unrelated tests are not broken.
- [ ] Production behavior was not implemented beyond sentinel stubs.
- [ ] Any temporary stub is named and easy to find.

## Done Criteria

- [ ] Required test files, fixtures, and specs are committed.
- [ ] Targeted build command succeeds.
- [ ] Targeted test command is RED for the new behavior.
- [ ] Failure output clearly points to the missing behavior.
- [ ] No production logic was added.
- [ ] Commit message uses the unit prefix.

Commit message:

```text
test(unit-00): failing specs for [unit behavior] (Red)
```

## Handoff to Implementation

Include in the commit body or handoff note:

- Which tests are expected to fail.
- Which stubs are temporary.
- Which existing suites must stay green.
- Any fixture, host, device, service, or environment requirement.

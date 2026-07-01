# Implementation Subagent Prompt - Unit 00: [Unit Name] (GREEN + REFACTOR)

You implement the minimum production change needed to turn the approved RED validation green, then refactor with tests green.

Read `context.md` and `prompt-test.md` before writing production code. The RED tests are the current specification.

## Pre-Green Verification

Before implementation:

- [ ] Run the targeted test command from `prompt-test.md`.
- [ ] Confirm the new suite is RED for the expected reason.
- [ ] Confirm unrelated existing failures, if any, are documented.
- [ ] Identify all temporary stubs added by the test step.

Do not proceed if the suite is already green without implementation. That means the RED step did not specify the behavior correctly or the behavior already exists.

## Green

Implement only what the tests require.

Required production work:

1. [Production behavior]
2. [Contract, schema, migration, config, or resource update]
3. [Integration wiring]
4. [Error, retry, fallback, or recovery behavior]

Keep the first green pass small. Avoid unrelated cleanup, broad rewrites, or speculative abstractions.

## Constraints

- Preserve existing public contracts unless this unit explicitly owns a breaking change.
- Do not weaken or delete tests to make the suite pass.
- If a test expectation is objectively wrong, update it only with a clear explanation in the commit body or summary.
- Keep unstable dependencies behind seams, fakes, fixtures, or gated integration checks.
- Keep performance, security, privacy, compatibility, and migration rules from `context.md`.
- Remove or replace all sentinel stubs introduced during the RED step.

## Refactor

After the targeted suite is green:

- [ ] Extract duplicated logic only when it removes real complexity.
- [ ] Name important rules or boundary decisions.
- [ ] Keep behavior unchanged while refactoring.
- [ ] Re-run the targeted suite after each meaningful refactor.
- [ ] Re-run the full relevant suite before completion.

Possible refactors:

- [Pure helper or parser]
- [Shared fixture loader]
- [Single choke point for validation or error mapping]
- [Small documentation update for future units]

## Validation Commands

Run:

```bash
[targeted test command]
[full relevant test command]
[lint / typecheck / build command]
```

If a command cannot run locally, document why and list the closest completed validation.

## Done Criteria

- [ ] Targeted suite is GREEN.
- [ ] Full relevant suite is GREEN, or known unrelated failures are documented.
- [ ] New behavior has success, failure, and edge-case coverage.
- [ ] Temporary stubs are gone or replaced by real behavior.
- [ ] Public contracts, fixtures, and docs are updated.
- [ ] No dependent unit needs hidden setup to start.
- [ ] Summary or handoff notes are written if the unit changed contracts, fixtures, migrations, or release behavior.

Commit messages:

```text
feat(unit-00): [unit behavior] green
refactor(unit-00): [small structural improvement]
```

## Completion Summary

When finished, report:

- What changed.
- What validation passed.
- What contracts or fixtures changed.
- What remains out of scope.
- Any follow-up needed by downstream units.

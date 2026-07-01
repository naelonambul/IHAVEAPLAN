# Unit 00 - [Unit Name] - Summary

## Status

| Field | Value |
| --- | --- |
| Unit | [Unit 00 - Unit Name] |
| Reviewer | [Reviewer / Agent / Team] |
| Review Date | [YYYY-MM-DD] |
| Result | [Approved / Approved with follow-up / Changes requested / Blocked] |
| Source Context | [`context.md`](./context.md) |
| Test Prompt | [`prompt-test.md`](./prompt-test.md) |
| Implementation Prompt | [`prompt-impl.md`](./prompt-impl.md) |

## Work Completed

[Summarize what was actually changed. Keep this factual and tied to the unit scope.]

- [Behavior, contract, fixture, migration, config, or documentation completed]
- [Implementation detail worth preserving for handoff]
- [Explicitly completed out-of-band cleanup, if any]

## Reviewer Evaluation

The reviewer should assess whether the implementation satisfies the planned unit, not whether unrelated improvements are possible.

| Area | Rating | Notes |
| --- | --- | --- |
| Scope control | [Pass / Concern / Fail] | [Did the work stay inside the unit?] |
| TDD discipline | [Pass / Concern / Fail] | [Was RED verified before GREEN?] |
| Correctness | [Pass / Concern / Fail] | [Does behavior match the tests and context?] |
| Failure coverage | [Pass / Concern / Fail] | [Are invalid, missing, boundary, retry, or fallback paths covered?] |
| Contract stability | [Pass / Concern / Fail] | [Did public interfaces, schemas, or fixtures change safely?] |
| Maintainability | [Pass / Concern / Fail] | [Is the implementation understandable and appropriately factored?] |
| Downstream readiness | [Pass / Concern / Fail] | [Can dependent units start without hidden setup?] |

## Findings

List review findings in severity order.

| Severity | Finding | File / Area | Required Action |
| --- | --- | --- | --- |
| [P0 / P1 / P2 / P3] | [Issue or risk] | [Path / component] | [Fix, follow-up, or accepted risk] |

Severity guide:

- **P0:** blocks completion or breaks a critical path.
- **P1:** should be fixed before dependent units or release work.
- **P2:** valid follow-up that does not block this unit.
- **P3:** minor polish, documentation, or future improvement.

If there are no findings, write:

```text
No blocking review findings.
```

## Validation Evidence

Record the exact checks that were run.

| Check | Command / Method | Result | Notes |
| --- | --- | --- | --- |
| Targeted suite | `[command]` | [Pass / Fail / Not run] | [Output summary] |
| Full relevant suite | `[command]` | [Pass / Fail / Not run] | [Output summary] |
| Build / typecheck / lint | `[command]` | [Pass / Fail / Not run] | [Output summary] |
| Manual or visual check | [Method] | [Pass / Fail / Not run] | [Evidence] |

If a check was not run, explain why and identify the closest completed validation.

## Files Changed

| Type | Files |
| --- | --- |
| Modified | `[path]` |
| Added | `[path]` |
| Removed | `[path]` |

## Contract, Fixture, or Data Changes

Document changes that downstream units must know about.

- [Public API, schema, file format, migration, config, fixture, golden output, or generated asset]
- [Compatibility note]
- [Refresh or update rule]

If none, write:

```text
No contract, fixture, or data changes.
```

## Out of Scope

Confirm what this unit intentionally did not do.

- [Deferred behavior]
- [Dependent unit]
- [Known non-goal]

## Risks and Follow-Up

| Risk / Follow-up | Owner | Needed By | Blocks |
| --- | --- | --- | --- |
| [Risk or task] | [Owner] | [Unit / date] | [Yes / No / Unit IDs] |

## Commit History

```text
test(unit-00): failing specs for [unit behavior] (Red)
feat(unit-00): [unit behavior] green
refactor(unit-00): [small structural improvement]
```

## Final Reviewer Decision

[Approved / Approved with follow-up / Changes requested / Blocked]

Reviewer note:

[Short final assessment. Include why the unit is or is not ready for downstream work.]

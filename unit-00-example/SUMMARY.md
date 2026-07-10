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
| Contract Version | [1.0] |
| Snapshot / Contract Digest | [Snapshot ID and context.md SHA-256] |
| Source Revision | [Full immutable commit ID / VCS revision] |

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

## Observed GREEN Evidence and Behavioral RED Result

Record the runtime results StageRelay observed against the contract's expected
RED and required GREEN evidence specification.

| Contract validation ID | Phase | Exact command / method | Exit / result | Named check and evidence |
| --- | --- | --- | --- | --- |
| [VAL-RED-01] | RED | `[command]` | [Observed result] | [Expected identifier, allowed failure class, signature; confirm no forbidden class] |
| [VAL-GREEN-01] | GREEN | `[command]` | [Observed result] | [Passing identifiers and retained output] |
| [VAL-REG-01] | GREEN | `[command]` | [Observed result] | [Suite counts / retained output] |
| [VAL-QUAL-01] | GREEN | `[command]` | [Observed result] | [Build/lint/typecheck evidence] |

If a check was not run, explain why and identify the closest completed validation.

## Handoff Provenance Verification

| Item | Expected identity | Observed identity | Result |
| --- | --- | --- | --- |
| Governing source digests | [Medium/large values from `context.md`, or not applicable] | [Observed SHA-256 values / not applicable] | [Pass / Fail / N/A] |
| Dependency identities | [Medium/large required identities, or not applicable] | [Observed identities / not applicable] | [Pass / Fail / N/A] |
| Supplemental artifact hashes | [Optional StageRelay manifest values] | [Observed hashes / not recorded] | [Pass / Fail / N/A] |
| Boundaries and approvals | [Contract requirements] | [Observed approvals/actions] | [Pass / Fail] |

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

## Lesson Carried Forward

[One insight from this unit worth carrying into future units — a pattern that worked, a dead-end to avoid, or a decision to reuse. Write "None" if nothing notable.]

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

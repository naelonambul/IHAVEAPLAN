# Unit 00 - [Unit Name] - Execution Contract

This file is the sole authoritative execution handoff for this unit. Complete
the fields required by the selected profile under the project's
`planning-contract.md`, then obtain explicit human approval before StageRelay
imports it. Derived prompts may restate this contract but may not override it.

## Contract Identity and Approval

Required for every profile.

| Field | Value |
| --- | --- |
| `contract_version` | `1.0` |
| `planning_profile` | [small / medium / large] |
| `unit_id` | [unit-NN-stable-slug] |
| `objective` | [One observable outcome] |
| `approval_state` | [draft / approved / superseded] |
| `approved_by` | [Human identity or accountable role] |
| `approved_at` | [ISO 8601 timestamp with offset] |

## Source Baseline

Required for every profile.

| Field | Value |
| --- | --- |
| Target repository | [Canonical repository identity and path] |
| Source revision | [Full commit ID or other immutable VCS revision] |

### Medium/Large planning-source provenance

Required for medium and large; small may omit this subsection. Hash the exact
approved bytes of every governing source.

| Path | Authority role | State / version | SHA-256 |
| --- | --- | --- | --- |
| `[project-relative plan path]` | Governing project scope and decisions | [approved / version] | `[64 lowercase hex]` |
| `[project-relative work-unit breakdown path]` | Governing decomposition and shared constraints | [approved / version] | `[64 lowercase hex]` |
| `[research or requirement source]` | [Referenced evidence or governing role] | [state / version] | `[digest]` |

If a governing source conflicts with this contract, stop and return to planning.
StageRelay does not resolve the contradiction. StageRelay computes the
authoritative `context.md` SHA-256 externally when creating its snapshot.

## Optional Planning Context

Optional for every profile. Omit it when the objective, scope, instructions, and
invariants already provide enough context.

### Current state

- Existing files or modules: `[path]` - [current responsibility]
- Existing tests: `[path]` - [what is covered]
- Known gap: [missing behavior, contract, fixture, flow, or risk]

### Decisions fixed by planning

- [Decision the executor must not reopen]

## Scope and Boundaries

Required for every profile.

### Included behavior and deliverables

- [Behavior, API, fixture, migration, config, or user-facing slice]
- [Validation or documentation deliverable]

### Excluded behavior

- [Deferred behavior, dependent unit, or question not solved during execution]

### Path and operation boundaries

| Boundary | Value |
| --- | --- |
| Allowed paths | [Exact project-relative paths or globs] |
| Forbidden paths | [Exact paths/globs, or reviewed `none`] |
| Allowed operations | [Read/write/test/build actions] |
| Forbidden operations | [Destructive, external-write, deploy, secret, or other limits] |

More permissive system access does not grant permission to exceed these
boundaries.

## Medium/Large Dependencies and Concurrency

Required for medium and large; small may omit this section.

| Dependency unit / artifact | Required immutable identity | Evidence before start |
| --- | --- | --- |
| [unit ID / artifact / reviewed `none`] | [Snapshot digest / commit ID / contract digest / none] | [Manifest check / none] |

| Named shared resource | Access | Conflicts with | Coordination rule |
| --- | --- | --- | --- |
| [schema / migration chain / fixture / service / reviewed `none`] | [exclusive / shared-read / none] | [Unit IDs / none] | [Serialize, lock, or none] |

Downstream units: [Unit IDs, reviewed `none`, or omit when not needed]

## Implementation Instructions and Invariants

Required for every profile. These instructions are authoritative;
`prompt-impl.md` may expand them without changing their meaning.

1. [Minimum production behavior]
2. [Owned interface, schema, configuration, resource, or documentation update]
3. [Required integration/error/retry/recovery behavior]

Invariants:

- [Existing behavior or suite that must remain green]
- [Compatibility, privacy, security, performance, or migration rule]
- [No hidden dependency on live or unstable systems]

## Validation and Completion Requirements

Required for every profile. Commands are exact and run from [working directory].
Environment prerequisites: [deterministic prerequisites or reviewed `none`].

| ID | Phase | Exact command | Completion criterion |
| --- | --- | --- | --- |
| [VAL-RED-01] | RED | `[targeted command]` | [Matches the expected RED below] |
| [VAL-GREEN-01] | GREEN | `[targeted command]` | [Named checks pass with expected result] |
| [VAL-REG-01] | GREEN | `[full relevant suite or reviewed none]` | [No regressions / not applicable reason] |
| [VAL-QUAL-01] | GREEN | `[build/lint/typecheck or reviewed none]` | [Expected result / not applicable reason] |

### Expected RED

For work without an intended behavioral RED, record
`not-applicable: <reviewed reason>` and identify the baseline validation above.
The remaining RED fields may then be omitted.

| Field | Expected value |
| --- | --- |
| Validation ID | [VAL-RED-01 / not-applicable reason] |
| Test/check identifier | [Fully qualified test, assertion, contract check, or diagnostic ID] |
| Allowed behavioral failure class | [Assertion mismatch / typed notImplemented sentinel / approved compile-time contract failure] |
| Expected exit/result | [Exact exit code or structured result] |
| Required output signature | [Stable substring/diagnostic or `not-required: <reason>`] |
| Forbidden failure classes | setup; discovery/collection; unrelated import/compile; configuration; fixture loading; timeout; dependency availability; infrastructure |

StageRelay accepts observed RED only when the named check fails for the allowed
behavior, the result and signature match, and no forbidden class appears.
Already GREEN, a different assertion, or an ambiguous failure stops execution.

### Required GREEN Evidence Specification

This table defines what StageRelay must later observe and retain. It does not
claim that execution-time results already exist.

| Criterion / validation ID | Expected successful result | Required runtime record |
| --- | --- | --- |
| [VAL-GREEN-01] | [Exit/result and named passing checks] | [StageRelay summary/manifest or artifact path] |
| [VAL-REG-01] | [Exit/result and suite counts, or not applicable] | [StageRelay summary/manifest or artifact path] |
| [VAL-QUAL-01] | [Exit/result and relevant output, or not applicable] | [StageRelay summary/manifest or artifact path] |

Completion requires StageRelay to record observed GREEN evidence satisfying this
specification, remove temporary RED stubs, and verify all included behavior and
completion criteria.

## Approval, Replanning, and Escalation

The approval identity above is required for every profile. Medium and large units
add conditional approval gates where applicable; small may omit this table.

| Conditional approval point | Approver | Required before | Approval record |
| --- | --- | --- | --- |
| [Breaking contract / migration / destructive action / release / reviewed `none`] | [Identity / role] | [Action / none] | [Record / none] |

Update and reapprove this contract before changing its identity, source baseline,
scope/boundaries, authoritative instructions/invariants, validation and RED/GREEN
requirements, profile-required dependencies/resources, or approval rules.

Replanning is required for changes to the objective, accepted behavior,
architecture, dependency graph, cross-unit contracts, security/privacy posture,
destructive actions, or governing plan scope. Project-specific triggers:

- [Material trigger]

Stop and return to planning when a material trigger occurs, a required identity
does not match, a boundary must be crossed, RED has a forbidden or ambiguous
cause, required approval is missing, or repeated validation does not converge.

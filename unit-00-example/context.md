# Unit 00 - [Unit Name] - Execution Contract

This file is the authoritative execution handoff for this unit. Complete it under
the project's `planning-contract.md`, replace every placeholder, and
obtain approval before snapshot or execution. Derived prompts may restate this
contract but may not override it.

## Contract Identity and Approval

| Field | Value |
| --- | --- |
| `contract_version` | `1.0` |
| `planning_profile` | [small / medium / large] |
| `unit_id` | [unit-NN-stable-slug] |
| `objective` | [One observable outcome] |
| `handoff_prepared_by` | [Human / agent / process identity] |
| `handoff_prepared_at` | [ISO 8601 timestamp with offset] |
| `approval_state` | [draft / approved / superseded] |
| `approved_by` | [Human identity or accountable role] |
| `approved_at` | [ISO 8601 timestamp with offset] |

## Source Baseline and Governing Sources

| Field | Value |
| --- | --- |
| Target repository | [Canonical repository identity and path] |
| Source revision | [Full commit ID or immutable VCS revision] |
| Dirty state | [false / true] |
| Included dirty paths | [none / exact paths included in the snapshot] |

Every governing source must be approved or otherwise identified by its role and
hashed as snapshotted. Add rows as needed.

| Path | Authority role | State / version | SHA-256 |
| --- | --- | --- | --- |
| `[project-relative plan path]` | Governing project scope and decisions | [approved / version] | `[64 lowercase hex]` |
| `[project-relative work-unit breakdown path]` | Governing decomposition and shared constraints | [approved / version] | `[64 lowercase hex]` |
| `[research path or none]` | Referenced evidence only | [reviewed / none] | `[digest or none]` |
| `[requirement/design source]` | [Governing or referenced role] | [approved / version] | `[digest]` |

If these sources conflict with this contract, stop and return to planning. Do not
select a source ad hoc. `context.md` is hashed externally by the execution
snapshot manifest and must not contain its own digest.

## Objective, Current State, and Decisions

### Current state

[Describe the repository baseline before this unit starts.]

- Existing files or modules: `[path]` - [current responsibility]
- Existing tests: `[path]` - [what is covered]
- Known gap: [missing behavior, contract, fixture, flow, or risk]

### Decisions fixed by planning

- [Decision the executor must not reopen]
- [Decision the executor must not reopen]

## Scope and Boundaries

### Included behavior and deliverables

- [Behavior, API, fixture, migration, config, or user-facing slice]
- [Validation artifact]
- [Documentation or handoff artifact]

### Excluded behavior

- [Deferred behavior or dependent unit]
- [Planning question that must not be solved during execution]

### Path and operation boundaries

| Boundary | Value |
| --- | --- |
| Allowed paths | [Exact project-relative paths or globs] |
| Forbidden paths | [Exact paths/globs; use `none` only after review] |
| Allowed operations | [Read/write/test/build actions] |
| Forbidden operations | [Destructive, external-write, deploy, secret, or other limits] |

More permissive access does not grant permission to exceed these boundaries.

## Dependencies and Concurrency

Use `none` only when reviewed and genuinely empty. A mutable unit name alone is
not a dependency identity.

| Dependency unit / artifact | Required immutable identity | Evidence before start |
| --- | --- | --- |
| [unit ID or artifact] | [Snapshot digest / commit ID / contract digest] | [Command or manifest check] |

| Named shared resource | Access | Conflicts with | Coordination rule |
| --- | --- | --- | --- |
| [schema / migration chain / fixture / service / none] | [exclusive / shared-read / none] | [Unit IDs / none] | [Lock, serialization, or none] |

Downstream units: [Unit IDs or none]

## Implementation Instructions

These are authoritative. `prompt-impl.md` may expand them into an operational
sequence without changing their meaning.

1. [Minimum production behavior]
2. [Owned interface, schema, migration, configuration, or resource update]
3. [Integration/error/retry/recovery behavior]
4. [Required documentation or fixture update]

Invariants:

- [Existing behavior or suite that must remain green]
- [Compatibility, privacy, security, performance, or migration rule]
- [No hidden dependency on live or unstable systems]

## Validation and Completion Contract

### Commands

Commands are exact and run from [working directory]. Environment prerequisites:
[deterministic prerequisites or `none`].

| ID | Phase | Exact command | Completion criterion |
| --- | --- | --- | --- |
| [VAL-RED-01] | RED | `[targeted command]` | [Matches the RED contract below] |
| [VAL-GREEN-01] | GREEN | `[targeted command]` | [Named checks pass with expected result] |
| [VAL-REG-01] | GREEN | `[full relevant suite]` | [No regressions] |
| [VAL-QUAL-01] | GREEN | `[build/lint/typecheck command]` | [Expected exit/result] |

### Expected RED

For non-behavior-changing small work only, write
`not-applicable: <reviewed reason>` and name the baseline validation above.

| Field | Expected value |
| --- | --- |
| Validation ID | [VAL-RED-01] |
| Test/check identifier | [Fully qualified test, assertion, contract check, or diagnostic ID] |
| Allowed behavioral failure class | [Assertion mismatch / typed notImplemented sentinel / approved compile-time contract failure] |
| Expected exit/result | [Exact exit code or structured result] |
| Required output signature | [Stable substring/diagnostic or `not-required: <reason>`] |
| Forbidden failure classes | setup; discovery/collection; unrelated import/compile; configuration; fixture loading; timeout; dependency availability; infrastructure |

RED is valid only when the named check fails for the allowed behavior, the result
and signature match, and no forbidden class appears. Already GREEN, a different
assertion, or an ambiguous failure must halt and escalate.

### Required GREEN evidence

| Criterion / validation ID | Required evidence | Retention location |
| --- | --- | --- |
| [VAL-GREEN-01] | [Command, exit/result, named passing checks, output signature] | [`SUMMARY.md` section / artifact path] |
| [VAL-REG-01] | [Command, exit/result, suite counts or named checks] | [`SUMMARY.md` section / artifact path] |
| [VAL-QUAL-01] | [Command, exit/result, relevant output] | [`SUMMARY.md` section / artifact path] |

Completion requires all included behavior and acceptance criteria to be observed,
all required GREEN evidence to be retained, temporary RED stubs to be removed,
and downstream work to require no hidden setup.

## Approval Points and Change Control

| Approval point | Approver | Required before | Evidence |
| --- | --- | --- | --- |
| Unit contract | [Human identity / role] | Snapshot and execution | [Approval record] |
| [Breaking contract / migration / destructive action / release / none] | [Identity / role] | [Action] | [Approval record] |

Any change to identity, provenance, scope/boundaries, dependencies/resources,
implementation instructions, validation/RED/GREEN criteria, approvals, or derived
artifact contents/digests requires a new contract digest and reapproval.

Replanning is required for changes to the objective, accepted behavior,
architecture, dependency graph, cross-unit contracts, security/privacy posture,
destructive actions, or governing plan scope. Project-specific triggers:

- [Trigger]
- [Trigger]

## Derived and Copied Artifact Provenance

These artifacts are non-authoritative. Hash their exact snapshotted bytes after
derivation; update this table and reapprove if their contents change.

| Artifact | Classification | Derived/copied from | SHA-256 |
| --- | --- | --- | --- |
| `prompt-test.md` | Derived RED instructions | `context.md` contract version/digest recorded by snapshot | `[64 lowercase hex]` |
| `prompt-impl.md` | Derived GREEN + REFACTOR instructions | `context.md` contract version/digest recorded by snapshot | `[64 lowercase hex]` |
| `README.md` | Copied explanatory guidance | `[template source revision and path]` | `[64 lowercase hex]` |

`SUMMARY.md`, `RESULTS.md`, and `ESCALATION.md` are generated after handoff and
are recorded in execution evidence rather than approved as planning inputs.

## Escalation Triggers

Stop and return to planning when any replan trigger occurs, a dependency identity
does not match, a digest fails, a boundary must be crossed, RED fails for a
forbidden/ambiguous reason, required approval is missing, or repeated validation
does not converge.

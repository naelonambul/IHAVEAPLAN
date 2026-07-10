# Planning-to-Execution Contract

This document defines the normative contract between IHAVEAPLAN planning and an
execution layer. Contract version `1.0` is documentation-oriented: one approved
work-unit `context.md` is the execution authority, and its structured sections
below are the schema. An execution layer may parse or transcribe them into its own
manifest, but must not infer missing values.

## 1. Authority and artifact flow

```text
research-summary.md (evidence)
  -> plan.md (approved project scope and decisions)
  -> work-units.md (approved decomposition, graph, and shared constraints)
  -> tasks/unit-NN-name/context.md (approved per-unit contract)
       -> prompt-test.md (derived RED instructions)
       -> prompt-impl.md (derived GREEN + REFACTOR instructions)
       -> execution snapshot
            -> SUMMARY.md / RESULTS.md / ESCALATION.md (execution records)
```

The approved unit `context.md` is the only authoritative execution handoff. It
must contain the common core contract or reference immutable, digest-verified
governing sources for details. A path without a revision and digest is not an
immutable reference.

Authority is intentionally separated:

| Artifact | Role | Authority rule |
| --- | --- | --- |
| `research-summary.md` | Evidence and rejected options | Referenced planning input; authoritative only for a unit field that explicitly cites it |
| `plan.md` | Project goals, scope, decisions, and checkpoints | Governing planning source once approved |
| `work-units.md` | Unit identities, dependency graph, sequencing, and shared constraints | Governing decomposition source once approved |
| Unit `context.md` | Versioned per-unit contract | Authoritative execution input once approved |
| `prompt-test.md`, `prompt-impl.md` | Operational instructions derived from the unit contract | Must not add or override scope, behavior, authority, or approval rules |
| `README.md`, unit `README.md` | Explanatory usage guidance | Non-normative |
| `SUMMARY.md`, `RESULTS.md`, `ESCALATION.md` | Execution evidence or escalation records | Generated after handoff; never retroactively change the approved contract |

If artifacts conflict, execution stops. The planner must reconcile the governing
sources, update the unit contract and affected derived prompts, refresh digests,
and obtain any required reapproval. The execution layer does not choose a winner.

## 2. Common core contract

Every approved unit uses the sections and tables in
[`unit-00-example/context.md`](./unit-00-example/context.md). Placeholder text,
unknown values, and mutable-only references are invalid in an approved contract.
Use `none` when a field is applicable but empty, and `not-applicable: <reason>`
only where this document permits it.

Versions use `MAJOR.MINOR`. An execution layer must reject an unsupported major
version. A minor version may add backward-compatible fields or constraints; it
must not change the meaning of an existing field. Any version change requires
the unit reapproval described in §5.

The common core records:

- `contract_version` (`1.0`) and `planning_profile`;
- handoff preparer identity/time plus approval state, approver identity, and approval timestamp;
- stable unit identifier and objective;
- source repository revision and clean/dirty state;
- governing source paths, SHA-256 digests, and authority roles;
- allowed and forbidden paths plus behavioral and operational boundaries;
- dependencies with immutable required identities;
- concurrency policy and named shared resources;
- authoritative implementation instructions;
- exact validation commands, completion criteria, RED contract, and GREEN evidence;
- human approval points and fields that trigger reapproval or replanning; and
- copied/derived artifact provenance and SHA-256 digests.

Field requirement classes are:

| Class | Fields |
| --- | --- |
| Required for every approved unit | Contract/profile identity; unit identity/objective; handoff and approval identity/time; repository revision and dirty state; governing-source roles/digests; included/excluded scope; path and operation boundaries; implementation instructions; exact validation/completion criteria; GREEN evidence; approval and change-control rules; derived/copied artifact provenance/digests |
| Required, with explicit `none` allowed | Dependencies; downstream units; named shared resources; forbidden paths after review; environment prerequisites |
| Conditionally required | Dirty-path inventory when dirty; RED contract for behavior-changing/TDD work; output signature when result alone is ambiguous; graph and staged approvals for large work; project-specific approval gates when regulated, destructive, breaking, migratory, security/privacy-sensitive, or release-affecting |
| Optional | Referenced research/evidence not used as authority; post-execution `RESULTS.md`; additional non-normative references |

Digest bytes exactly as snapshotted, using lowercase SHA-256 hex. The source
repository revision identifies the implementation baseline (normally a full Git
commit ID). If planning or target files are intentionally dirty, record
`dirty: true`, list the included paths, and hash their snapshotted bytes; a
revision alone does not describe those changes.

Do not include the unit contract's own digest inside itself. The execution layer
computes the `context.md` digest when it creates the snapshot manifest. Digests of
copied or derived sibling artifacts belong in the unit contract and are verified
before execution.

## 3. Profiles

Profiles change how much of the common contract may be explicitly empty; they do
not create different formats.

| Requirement | Small | Medium | Large |
| --- | --- | --- | --- |
| Units | Exactly one bounded unit | One or more units | Multiple units |
| Core identity, provenance, boundaries, instructions, validation, approval | Required | Required | Required |
| Dependencies | `none` allowed | Explicit identities or `none` | Explicit identities and graph in `work-units.md` |
| RED/GREEN contract | Required for behavior-changing/TDD work; otherwise an explicit `not-applicable` reason and baseline validation | Required | Required per executable unit |
| Concurrency/shared resources | `none` allowed | Explicit resources or `none` | Explicit per-unit resources plus portfolio constraints |
| Approval | Unit-contract approval | Unit-contract approval and named conditional approval points | Staged plan/decomposition/unit approvals and named conditional approval points |

Choose the smallest profile that truthfully represents the work. Complexity
labels such as S/M/L do not select a profile; graph and governance needs do.

## 4. RED and GREEN semantics

An expected RED is a behavioral failure, not merely a non-zero command. For every
RED command, record:

- the exact command and expected test/check identifier;
- the allowed behavioral failure class (for example, assertion mismatch or a
  typed `notImplemented` sentinel);
- expected exit code or structured result;
- an output signature when needed to disambiguate the failure; and
- forbidden failure classes: setup, discovery/collection, import, compilation
  unless an approved compile-time contract test is the target, configuration,
  fixture loading, timeout, dependency availability, and infrastructure failure.

RED is accepted only when every required identifier is observed, the result and
signature match, and no forbidden class is present. An already-GREEN check, a
different assertion, or an ambiguous timeout is not an acceptable RED.

GREEN evidence must identify the contract criterion, exact command, exit/result,
required passing test/check identifiers, and retained output or artifact location.
It must include the targeted validation and the full relevant regression/build/
lint checks named by the contract. Missing evidence is not equivalent to passing.

## 5. Approval and change control

The contract declares approval points and names the approving human or role.
At minimum, a human approves the unit contract before snapshot/execution. Medium
and large work must also name conditional approvals for breaking contracts,
migrations, security/privacy boundaries, destructive actions, release, or other
project-specific gates. Large work records staged approval of the plan,
decomposition, and executable units.

Changes to any of the following require a new contract digest and human
reapproval before execution continues:

- contract version, planning profile, unit identity, or objective;
- governing sources, revision, dirty-state inventory, or digests;
- scope, allowed/forbidden paths, boundaries, dependencies, or shared resources;
- implementation instructions, validation commands, RED/GREEN expectations, or
  completion criteria;
- approval points or derived-artifact contents/digests.

Replanning is required when the objective, accepted behavior, architecture,
dependency graph, cross-unit contract, security/privacy posture, destructive
action, or approved plan scope must change. Evidence-only additions to
`SUMMARY.md` do not change the contract. When uncertain, halt and escalate; do not
infer permission from an adjacent field.

## 6. Snapshot and handoff verification

Before execution, the handoff producer and consumer verify:

1. contract version is supported and approval state is `approved`;
2. the repository revision/dirty inventory matches the intended baseline;
3. every governing, copied, and derived artifact exists and matches its digest;
4. all required fields for the selected profile are concrete;
5. dependencies match their required immutable identities and are complete;
6. no active unit conflicts on a named exclusive shared resource;
7. requested paths and actions are inside boundaries; and
8. approval gates required before the next action are satisfied.

The snapshot manifest records the unit-contract digest, all copied artifact
digests, source revision, dependency identities, contract version, timestamp, and
handoff producer identity. A mismatch invalidates the snapshot; it is not repaired
by guessing or silently re-hashing mutable content.

## 7. Legacy migration

Existing unit folders remain readable planning records, but they are not contract
`1.0` merely because their headings resemble the new template. To migrate:

1. copy the `1.0` sections from `unit-00-example/context.md`;
2. select the truthful profile and assign a stable unit ID;
3. identify approved governing sources and compute their digests;
4. transcribe known scope, dependencies, instructions, and validation commands;
5. specify RED/GREEN semantics from reviewed intent and observed validation;
6. classify prompts as derived, compute copied-artifact digests, and reconcile
   any conflict with the new contract; and
7. obtain human approval.

Do not invent a historical revision, approval, dependency identity, RED failure,
or provenance digest. If it cannot be established, leave the legacy unit
unmigrated or return it to planning for evidence and approval.

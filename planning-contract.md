# Planning-to-Execution Contract

This document defines the normative contract between IHAVEAPLAN and StageRelay.
Contract version `1.0` is documentation-oriented: one human-approved work-unit
`context.md` is the sole authoritative execution handoff. StageRelay may parse or
transcribe it into a runtime manifest, but must not infer missing required values.

## 1. Authority and lifecycle

```text
research-summary.md (evidence)
  -> plan.md (approved project scope and decisions)
  -> work-units.md (approved decomposition and shared constraints)
  -> tasks/unit-NN-name/context.md (approved per-unit contract)
       -> prompt-test.md (derived RED instructions)
       -> prompt-impl.md (derived GREEN + REFACTOR instructions)
       -> StageRelay snapshot and execution
            -> SUMMARY.md / RESULTS.md / ESCALATION.md (observed records)
```

Authority is separated by lifecycle:

| Artifact | Owner and role | Authority rule |
| --- | --- | --- |
| `research-summary.md` | IHAVEAPLAN evidence and rejected options | Referenced planning input; authoritative only where the unit contract explicitly cites it |
| `plan.md` | IHAVEAPLAN project goals, scope, decisions, and checkpoints | Governing planning source once approved |
| `work-units.md` | IHAVEAPLAN unit identities, dependency graph, sequencing, and shared constraints | Governing decomposition source once approved |
| Unit `context.md` | IHAVEAPLAN execution requirements | Sole authoritative execution handoff once human-approved |
| `prompt-test.md`, `prompt-impl.md` | Supplemental instructions derived from the unit contract | Must not add or override scope, behavior, authority, or approval rules |
| `README.md`, unit `README.md` | Explanatory guidance | Non-authoritative |
| StageRelay snapshot manifest | Runtime snapshot identity and metadata | Records the externally computed `context.md` digest and may record supplemental artifact hashes |
| `SUMMARY.md`, `RESULTS.md`, `ESCALATION.md` | StageRelay execution results or escalation records | Observed after handoff; never retroactively change the approved contract |

IHAVEAPLAN owns planning inputs, implementation boundaries, validation commands,
expected RED semantics, and the required GREEN evidence specification. StageRelay
owns runtime snapshot metadata and observed RED/GREEN results. Planning documents
must not claim that observed GREEN evidence exists before execution.

If a governing planning source conflicts with the approved unit contract,
StageRelay stops; it does not choose a winner. Planning must reconcile the source
documents, update the contract and affected prompts, and obtain human reapproval.
A derived prompt that contradicts `context.md` also stops execution. A byte-only
change to a non-authoritative prompt or README does not change approved intent or
independently require contract reapproval.

## 2. Version and common shape

Every approved unit uses the sections in
[`unit-00-example/context.md`](./unit-00-example/context.md). The three profiles
share that shape, but sections marked for medium/large may be omitted by small
units. Placeholder text and unknown values are invalid for fields required by the
selected profile. Use `none` for a reviewed empty required field and
`not-applicable: <reason>` only where the template permits it.

Versions use `MAJOR.MINOR`. StageRelay must reject an unsupported major version.
A minor version may add backward-compatible fields or constraints but must not
change an existing field's meaning. A contract version change requires human
reapproval before import.

StageRelay computes the authoritative SHA-256 of `context.md` externally when it
creates a snapshot. That digest and other runtime snapshot metadata do not belong
inside `context.md`. StageRelay may hash copied prompts, READMEs, or other
supplemental artifacts in its manifest for integrity or diagnostics, but those
hashes do not make the artifacts authoritative.

## 3. Profiles and required fields

Choose the smallest profile that truthfully represents the work. Complexity
labels such as S/M/L do not select a profile.

### Small

Small is exactly one bounded unit. It requires only:

- contract version and planning profile;
- stable unit ID and objective;
- approval state, human approver, and approval time;
- target repository and immutable source revision;
- included and excluded scope;
- allowed and forbidden paths or operations;
- implementation instructions and invariants;
- exact validation commands and completion criteria;
- expected RED semantics, or an explicit reviewed `not-applicable` reason;
- the required GREEN evidence specification; and
- material replanning and escalation triggers.

A small unit may omit governing-document digests, downstream-unit and dependency
graph metadata, shared-resource tables, staged approvals, prompt provenance, and
portfolio governance. Include any of them only when the actual risk requires it;
if several are required, medium is usually the more truthful profile.

### Medium

Medium uses the small core and additionally requires:

- governing planning-source roles and SHA-256 digests;
- explicit dependency identities, or reviewed `none`;
- named shared resources and concurrency rules, or reviewed `none`; and
- conditional human approval gates for breaking contracts, migrations,
  destructive actions, security/privacy boundaries, release, or similar risks.

### Large

Large uses the medium requirements across multiple units and additionally
requires:

- an explicit dependency graph in `work-units.md`;
- portfolio-level concurrency and named shared-resource constraints; and
- staged human approval of the plan, decomposition, and executable units.

## 4. RED and GREEN semantics

An expected RED is a planned behavioral failure, not merely a non-zero command.
For every RED command, the contract records:

- the exact command and expected test/check identifier;
- the allowed behavioral failure class, such as an assertion mismatch or typed
  `notImplemented` sentinel;
- expected exit code or structured result;
- an output signature when needed to disambiguate the failure; and
- forbidden failure classes: setup, discovery/collection, import, compilation
  unless an approved compile-time contract test is the target, configuration,
  fixture loading, timeout, dependency availability, and infrastructure failure.

StageRelay accepts observed RED only when every required identifier is observed,
the result and signature match, and no forbidden class is present. Already GREEN,
a different assertion, or an ambiguous timeout is not acceptable RED.

The planning-time required GREEN evidence specification identifies each contract
criterion, exact command, expected successful result, required passing test/check
identifiers, and the runtime record or artifact StageRelay must retain. It covers
the targeted validation and every regression, build, lint, or other check named
by the contract. During execution, StageRelay records observed GREEN evidence
against that specification. Missing observed evidence is not a passing result.

## 5. Approval and change control

A human must approve the completed unit contract before StageRelay imports it.
Medium and large profiles also declare conditional or staged approval points
required by §3.

Changing any authoritative execution requirement requires updating `context.md`,
human reapproval, and a new StageRelay snapshot. This includes:

- contract version, planning profile, unit identity, or objective;
- source repository or revision and, when required, governing-source digests;
- scope, allowed/forbidden paths, operational boundaries, dependencies, or
  shared-resource rules;
- implementation instructions, invariants, validation commands, RED semantics,
  required GREEN evidence specification, or completion criteria; and
- approval points or material replanning/escalation triggers.

Changing only a non-authoritative prompt, README, or runtime record does not
require contract reapproval. If such a change exposes a contradiction or changes
intended behavior, update and reapprove `context.md` instead.

Replanning is required when the objective, accepted behavior, architecture,
dependency graph, cross-unit contract, security/privacy posture, destructive
action, or approved plan scope must change. Observed evidence added to
`SUMMARY.md` does not change the contract. When uncertain, halt and escalate.

## 6. StageRelay import, snapshot, and execution

Before execution, StageRelay verifies:

1. contract major version is supported;
2. explicit human approval is present;
3. every field required by the selected profile is concrete;
4. the target repository and immutable revision match;
5. medium/large governing sources and dependencies match their required digests
   or identities;
6. medium/large concurrency and shared-resource constraints permit execution;
7. requested paths and actions are inside the approved boundaries; and
8. approval gates required before the next action are satisfied.

StageRelay computes and records the `context.md` SHA-256, source revision,
contract version, snapshot timestamp, and runtime handoff identity. It records
dependency identities and governing-source digests when the profile requires
them. It may also record hashes of supplemental copied or derived artifacts; a
supplemental hash mismatch is an integrity signal, not permission to reinterpret
the approved contract.

During execution, StageRelay records observed RED and observed GREEN evidence
against the contract's expectations. A contract contradiction, unsupported
version, missing approval, boundary violation, required identity mismatch, or
forbidden/ambiguous RED invalidates the handoff and stops execution.

## 7. Legacy migration

Existing unit folders remain readable planning records, but are not contract
`1.0` merely because their headings resemble the current template. To migrate:

1. copy the `1.0` shape from `unit-00-example/context.md`;
2. select the truthful profile and assign a stable unit ID;
3. establish the target repository revision and profile-required planning-source
   provenance;
4. transcribe known scope, boundaries, instructions, and validation commands;
5. specify expected RED and the required GREEN evidence specification from
   reviewed intent;
6. reconcile derived prompts with the contract; and
7. obtain human approval before StageRelay import.

Do not invent a historical revision, approval, dependency identity, RED failure,
or provenance digest. If required information cannot be established, leave the
legacy unit unmigrated or return it to planning.

# [Project Name] - Work Unit Breakdown

| Field | Value |
| --- | --- |
| Status | [Draft / Approved / Superseded] |
| Date | [YYYY-MM-DD] |
| Owner | [Owner / Team / Agent] |
| Source of Truth | [PLAN.md / PRD / issue / design doc] |
| Phase / Release | [Phase, milestone, or release name] |
| Methodology | [TDD / incremental delivery / agent handoff / other] |

---

## 0. Purpose

This document breaks an approved implementation plan into small, executable work units.

Use this after `PLAN.md` exists. The plan explains what should be built and why. This file explains how to split the work into independently executable units with clear dependencies, validation, and completion criteria.

Each work unit should be small enough for one focused implementation pass, but large enough to deliver a meaningful behavior, interface, or integration step.

---

## 1. Inputs and Assumptions

This work-unit breakdown is based on:

- [Approved implementation plan]
- [Product requirement / design source]
- [Architecture or interface decision]
- [Existing repository baseline]
- [Known constraints]

Before execution begins, confirm:

- [ ] The source plan has been reviewed.
- [ ] Work units map back to plan milestones or requirements.
- [ ] Dependencies are explicit.
- [ ] No unit requires hidden prerequisite work.
- [ ] Validation expectations are known before implementation starts.

---

## 2. Execution Protocol

Use the following loop for every unit:

1. Define the smallest observable behavior.
2. Write or update validation first.
3. Confirm the validation fails for the expected reason.
4. Implement the minimum production change.
5. Refactor only while validation stays green.
6. Update docs, fixtures, and handoff notes.
7. Mark the unit complete only after its checkpoint passes.

If agents are used, keep roles explicit:

- **Planning Agent:** keeps scope, dependencies, and sequencing coherent.
- **Test Agent:** writes failing tests, fixtures, contracts, or acceptance checks first.
- **Implementation Agent:** implements the unit against the approved validation.
- **Review Agent:** checks regressions, integration risk, and definition of done.

---

## 3. Execution Tracks

Group units that can move in parallel without blocking each other.

- **Track A - [Track Name]:** [Unit IDs in dependency order]
- **Track B - [Track Name]:** [Unit IDs in dependency order]
- **Track C - [Track Name]:** [Unit IDs in dependency order]

Recommended start order:

1. [Unit ID] - [Reason this should start first]
2. [Unit ID] - [Reason this can run in parallel]
3. [Unit ID] - [Reason this reduces uncertainty]

Parallelization rules:

- Units may run in parallel only when they do not change the same contract, file boundary, database schema, migration, public API, or shared fixture in incompatible ways.
- If a unit introduces a breaking contract change, schedule it before dependent work.
- If two units need the same unresolved decision, resolve or isolate the decision before either starts.

---

## 4. Work Unit Index

| # | Unit | Milestone | Area / Module | Complexity | Depends On | Can Run In Parallel With |
| --- | --- | --- | --- | --- | --- | --- |
| 01 | [unit-name] | [M0 / M1 / Phase] | [Area] | [S / M / L] | [-] | [Unit IDs] |
| 02 | [unit-name] | [M0 / M1 / Phase] | [Area] | [S / M / L] | [01] | [Unit IDs] |
| 03 | [unit-name] | [M0 / M1 / Phase] | [Area] | [S / M / L] | [01, 02] | [Unit IDs] |

Complexity guide:

- **S:** small, localized change; low integration risk.
- **M:** moderate change; touches one or two boundaries.
- **L:** broad change; new integration, migration, external dependency, or user-facing flow.

---

## 5. Unit Detail Template

Copy this section for each unit.

For units executed by agents, also copy `unit-00-example/` into a numbered unit folder and fill in `context.md`, `prompt-test.md`, `prompt-impl.md`, and `SUMMARY.md`.

### Unit [NN] - [unit-name]

**Purpose:**  
[One sentence describing why this unit exists.]

**Scope / deliverable:**  
[Concrete behavior, interface, file, component, or workflow delivered by this unit.]

**Out of scope:**  
[Explicit non-goals, deferred behavior, or dependent work.]

**Depends on:**

- [Required prior unit, decision, fixture, contract, or environment]

**Validation first:**

- [ ] [Failing unit test / contract test / fixture / acceptance check]
- [ ] [Failure-path test]
- [ ] [Boundary or regression test]
- [ ] [Integration or smoke check if needed]

**Implementation tasks:**

- [ ] [Production change]
- [ ] [Interface or contract update]
- [ ] [Fixture, migration, config, or documentation update]
- [ ] [Integration wiring]

**Acceptance criteria:**

- [ ] [Observable success behavior]
- [ ] [Observable failure behavior]
- [ ] [Edge cases covered]
- [ ] [No regression in dependent units]

**Handoff notes:**

- [Contracts changed]
- [Follow-up required]
- [Known risks]
- [Useful commands or checks]

**Checkpoint:**

- [ ] Required validation passes.
- [ ] Dependencies remain stable.
- [ ] Documentation or fixtures are updated.
- [ ] The next dependent unit can start without hidden setup.

---

## 6. Work Units

Use the template above to define the actual units.

---

### Unit 01 - [unit-name]

**Purpose:**  
[Why this unit exists.]

**Scope / deliverable:**  
[What this unit delivers.]

**Out of scope:**  
[What this unit intentionally does not do.]

**Depends on:**

- [Dependency or "-"]

**Validation first:**

- [ ] [Validation item]

**Implementation tasks:**

- [ ] [Task]

**Acceptance criteria:**

- [ ] [Acceptance item]

**Handoff notes:**

- [Note]

**Checkpoint:**

- [ ] [Checkpoint item]

---

### Unit 02 - [unit-name]

**Purpose:**  
[Why this unit exists.]

**Scope / deliverable:**  
[What this unit delivers.]

**Out of scope:**  
[What this unit intentionally does not do.]

**Depends on:**

- [Unit 01 / decision / fixture / contract]

**Validation first:**

- [ ] [Validation item]

**Implementation tasks:**

- [ ] [Task]

**Acceptance criteria:**

- [ ] [Acceptance item]

**Handoff notes:**

- [Note]

**Checkpoint:**

- [ ] [Checkpoint item]

---

## 7. Cross-Unit Contracts

List shared contracts that multiple units depend on.

| Contract | Owned By | Used By | Change Rules |
| --- | --- | --- | --- |
| [Interface / schema / file format] | [Unit / owner] | [Units] | [Compatibility rule] |
| [State model / API / event] | [Unit / owner] | [Units] | [Compatibility rule] |

Contract rules:

- [ ] Breaking changes are scheduled before dependent work.
- [ ] Mocks, fixtures, and golden outputs are updated with the contract.
- [ ] Downstream units do not rely on undocumented behavior.

---

## 8. Shared Test Assets and Fixtures

| Asset | Purpose | Created / Updated By | Used By |
| --- | --- | --- | --- |
| [Fixture / sample input] | [Purpose] | [Unit] | [Units / tests] |
| [Golden output] | [Purpose] | [Unit] | [Units / tests] |
| [Mock / stub] | [Purpose] | [Unit] | [Units / tests] |

Asset rules:

- [ ] Fixtures are deterministic and versioned.
- [ ] Golden outputs are reviewable.
- [ ] Refresh instructions exist for assets that can become stale.
- [ ] Live or unstable systems are isolated behind mocks, fakes, or non-blocking checks.

---

## 9. Hardening and Release Units

Hardening may be scheduled as normal units or as a final coordinated pass.

| Area | Validation | Owner | Blocks Release |
| --- | --- | --- | --- |
| End-to-end flow | [Acceptance test / manual check] | [Owner] | [Yes / No] |
| Regression suite | [Command / check] | [Owner] | [Yes / No] |
| Performance | [Budget / measurement] | [Owner] | [Yes / No] |
| Security / privacy | [Review / test] | [Owner] | [Yes / No] |
| Documentation | [Docs check] | [Owner] | [Yes / No] |

Release checkpoint:

- [ ] All release-scope units are complete.
- [ ] Cross-unit contracts are stable.
- [ ] Full validation passes.
- [ ] Known risks are documented.
- [ ] Handoff, deployment, or release notes are ready.

---

## 10. Open Questions

| Question | Why It Matters | Owner | Needed By | Blocks |
| --- | --- | --- | --- | --- |
| [Question] | [Impact] | [Owner] | [Unit / date] | [Units] |

Open-question rule:

Work blocked by an open question must wait, use a reversible placeholder, or be isolated behind a contract that can change without broad rework.

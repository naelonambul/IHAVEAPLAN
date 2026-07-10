# [Project Name] — Implementation Plan

| Field           | Value                                      |
| --------------- | ------------------------------------------ |
| Status          | [Draft / Approved / Superseded]            |
| Date            | [YYYY-MM-DD]                               |
| Owner           | [Owner / Team / Agent]                     |
| Approved By     | [Human identity / role, or none while draft] |
| Approved At     | [ISO 8601 timestamp with offset, or none]  |
| Governing Sources | [PRD / Design Doc / Specification / Issue] |
| Scope           | [What this plan covers]                    |
| Methodology     | [TDD / Incremental delivery / Other]       |

---

## 0. Planning Assumptions and Inputs

This plan is based on:

* [Primary source document or approved requirement]
* [Research summary, if technical choices need evidence]
* [Architecture or design document]
* [Known constraints]
* [Existing implementation, if any]

Before execution begins, confirm:

* [ ] The latest source documents have been reviewed.
* [ ] The implementation scope is clearly bounded.
* [ ] Superseded or obsolete requirements have been identified.
* [ ] External dependencies and constraints are known.
* [ ] Success criteria are measurable.

An approved plan governs project scope and decisions, but is not by itself an
execution handoff. Executable units must be materialized and approved under
[`planning-contract.md`](./planning-contract.md).

---

## 1. Goal and Scope

### Goal

[State the primary outcome this plan should deliver.]

### In Scope

* [Capability / component / workflow]
* [Capability / component / workflow]
* [Capability / component / workflow]

### Out of Scope

* [Excluded capability]
* [Deferred enhancement]
* [Non-goal]

### Planning Principle

Prefer a sequence that reduces uncertainty early, validates assumptions with tests or checkpoints, and avoids implementing dependent work before its foundations are stable.

---

## 2. Finalized Decisions

Record decisions that should not be repeatedly revisited during execution.

| Area             | Decision   | Reason   | Revisit Trigger     |
| ---------------- | ---------- | -------- | ------------------- |
| [Architecture]   | [Decision] | [Reason] | [Condition, if any] |
| [Tooling]        | [Decision] | [Reason] | [Condition, if any] |
| [Data / storage] | [Decision] | [Reason] | [Condition, if any] |
| [Testing]        | [Decision] | [Reason] | [Condition, if any] |

Decision checkpoint:

* [ ] All blocking architectural choices are resolved.
* [ ] Any unresolved choices are explicitly listed as open questions.
* [ ] Work that depends on unresolved choices is not scheduled before the decision point.

---

## 3. Execution Rules

All implementation work follows this loop:

1. **Define behavior**

   * Identify the smallest observable behavior to implement.
   * Define expected success, failure, and edge cases.

2. **Write validation first**

   * Add tests, checks, fixtures, contracts, or acceptance criteria before implementation.
   * Confirm the validation fails for the expected reason.

3. **Implement minimally**

   * Write only enough production work to satisfy the validation.

4. **Refactor safely**

   * Improve structure only while all validations remain green.

5. **Checkpoint**

   * Confirm tests, acceptance criteria, documentation, and integration assumptions still hold.

**Reflect before each checkpoint:** score the result against the acceptance criteria, grounded in an external signal (test run, schema, contract) rather than the implementer's own judgment. On failure, capture the reason, refine, and re-validate — do not close a checkpoint on an unverified "looks done."

No milestone is complete until its checkpoint criteria are satisfied.

---

## 4. System Structure

Describe the major parts of the system and their responsibilities.

```text
[Input / Trigger]
      ↓
[Component or Stage 1]
      ↓
[Component or Stage 2]
      ↓
[Persistence / State / Output]
      ↓
[User-visible or downstream result]
```

### Component Responsibilities

| Component     | Responsibility   | Depends On   | Exposes              |
| ------------- | ---------------- | ------------ | -------------------- |
| [Component A] | [Responsibility] | [Dependency] | [Interface / output] |
| [Component B] | [Responsibility] | [Dependency] | [Interface / output] |
| [Component C] | [Responsibility] | [Dependency] | [Interface / output] |

Dependency checkpoint:

* [ ] Foundational components are scheduled before dependent components.
* [ ] Interfaces are defined before integration work begins.
* [ ] Each component has a clear owner and validation method.

---

## 5. Interfaces, Contracts, and Data Flow

Define the boundaries that other work depends on.

### Inputs

| Input   | Source   | Required Format | Validation        |
| ------- | -------- | --------------- | ----------------- |
| [Input] | [Source] | [Format]        | [Validation rule] |

### Outputs

| Output   | Destination   | Required Format | Validation        |
| -------- | ------------- | --------------- | ----------------- |
| [Output] | [Destination] | [Format]        | [Validation rule] |

### State Transitions

```text
[initial]
  └─► [received / prepared]
        └─► [processed / validated]
              ├─► [completed]
              └─► [failed / fallback / manual review]
```

Contract checkpoint:

* [ ] Inputs and outputs are explicit.
* [ ] Error states are represented, not hidden.
* [ ] Retry, fallback, and duplicate-handling behavior is defined where relevant.
* [ ] Downstream components do not rely on undocumented behavior.

---

## 6. Validation Strategy

### Validation Layers

| Layer       | Purpose                                    | Examples                                      |
| ----------- | ------------------------------------------ | --------------------------------------------- |
| Unit        | Validate isolated logic                    | [Pure function / parser / rule / calculation] |
| Integration | Validate component interaction             | [Component A with Component B]                |
| Contract    | Validate external or boundary behavior     | [Schema / API / file / message format]        |
| End-to-end  | Validate full user or system flow          | [Primary workflow]                            |
| Performance | Validate timing, scale, or resource limits | [Latency / memory / throughput]               |
| Regression  | Prevent known failures from returning      | [Bug reproduction tests]                      |

### Required Failure Coverage

Every planned feature should cover:

* Valid input
* Invalid input
* Missing or partial input
* Boundary values
* Retry or fallback path
* Duplicate or repeated execution
* Timeout or unavailable dependency
* State recovery after interruption

Validation checkpoint:

* [ ] Tests or checks exist before implementation.
* [ ] Critical paths include failure and recovery cases.
* [ ] Non-deterministic dependencies are isolated behind seams, mocks, fixtures, or stubs.
* [ ] Performance-sensitive work has measurable budgets.

---

## 7. Required Test Assets and Fixtures

Create reusable assets before or alongside the work that needs them.

| Asset                    | Purpose   | Created By  | Used In |
| ------------------------ | --------- | ----------- | ------- |
| [Fixture / sample input] | [Purpose] | [Milestone] | [Tests] |
| [Golden output]          | [Purpose] | [Milestone] | [Tests] |
| [Mock / stub]            | [Purpose] | [Milestone] | [Tests] |
| [Recorded scenario]      | [Purpose] | [Milestone] | [Tests] |

Asset checkpoint:

* [ ] Fixtures are versioned.
* [ ] Golden outputs are reviewable.
* [ ] Refresh or update process is defined where fixtures can become stale.
* [ ] Test assets do not depend on live unstable systems unless explicitly marked non-blocking.

---

## 8. Milestones

Each milestone should deliver one coherent capability and leave the system in a working state.

Milestones 0-4 below are illustrative defaults. Adjust, rename, split, or remove milestones to match the project; five milestones are not required.

---

### Milestone 0 — Foundation and Skeleton

**Purpose:** Establish the project structure, core interfaces, baseline tooling, and validation harness.

**Depends on:**

* [Approved scope]
* [Initial decisions]
* [Repository or environment setup]

**Validation first:**

* [ ] [Test or check proving the skeleton builds]
* [ ] [Test or check proving core interfaces can be exercised]
* [ ] [Test or check proving CI or local validation runs]

**Implementation:**

* [ ] Create project structure.
* [ ] Define core interfaces and boundaries.
* [ ] Add initial fixtures, mocks, or stubs.
* [ ] Configure automated validation.

**Checkpoint:**

* [ ] Build passes.
* [ ] Baseline tests pass.
* [ ] Future milestones can be implemented without restructuring the foundation.

---

### Milestone 1 — Core Flow

**Purpose:** Implement the smallest complete flow from input to output.

**Depends on:**

* Milestone 0
* [Core interface]
* [Required fixture]

**Validation first:**

* [ ] [Test normal path]
* [ ] [Test invalid input]
* [ ] [Test fallback or error state]
* [ ] [Test state transition]

**Implementation:**

* [ ] Implement input handling.
* [ ] Implement core processing.
* [ ] Implement output or persistence.
* [ ] Connect the minimum end-to-end path.

**Checkpoint:**

* [ ] The primary flow works with deterministic inputs.
* [ ] Failure paths are observable.
* [ ] No dependent advanced feature is required for the flow to complete.

---

### Milestone 2 — Integration and Reliability

**Purpose:** Connect major components and harden the system against realistic failures.

**Depends on:**

* Milestone 1
* [Integration contract]
* [Persistence or communication layer]

**Validation first:**

* [ ] [Contract test]
* [ ] [Integration test]
* [ ] [Retry / duplicate / timeout test]
* [ ] [Recovery test]

**Implementation:**

* [ ] Connect components through defined interfaces.
* [ ] Add persistence, queueing, handoff, or transport as needed.
* [ ] Implement retry, dedupe, timeout, and recovery behavior.
* [ ] Add observability for failures and state.

**Checkpoint:**

* [ ] Components communicate only through documented contracts.
* [ ] Interruptions do not corrupt state.
* [ ] Repeated execution is safe.
* [ ] Manual recovery or fallback is available where automation can fail.

---

### Milestone 3 — Feature Completion

**Purpose:** Complete the remaining required capabilities for the planned release.

**Depends on:**

* Milestone 2
* [Stable core flow]
* [Feature-specific fixtures or inputs]

**Validation first:**

* [ ] [Feature behavior test]
* [ ] [Feature edge-case test]
* [ ] [Cross-feature regression test]
* [ ] [User-facing flow test]

**Implementation:**

* [ ] Implement remaining required features.
* [ ] Add configuration, localization, permissions, or user-facing states as needed.
* [ ] Connect features to the core flow without bypassing existing contracts.
* [ ] Update documentation where behavior changes.

**Checkpoint:**

* [ ] All release-scope features are implemented.
* [ ] New behavior does not break earlier milestones.
* [ ] User-facing flows have acceptance coverage.

---

### Milestone 4 — Hardening and Release Readiness

**Purpose:** Verify the system under realistic conditions and prepare for release or handoff.

**Depends on:**

* Milestone 3
* [Complete feature set]
* [Release criteria]

**Validation first:**

* [ ] End-to-end acceptance test
* [ ] Performance or resource test
* [ ] Regression suite
* [ ] Operational or maintenance check

**Implementation:**

* [ ] Fix bugs using failing reproduction tests first.
* [ ] Tune thresholds, budgets, and configuration.
* [ ] Remove dead code, obsolete fixtures, and superseded paths.
* [ ] Finalize documentation and release notes.

**Checkpoint:**

* [ ] All required validation passes.
* [ ] No blocking defects remain.
* [ ] Known risks are documented with mitigations.
* [ ] Release, deployment, or handoff procedure is clear.

---

## 9. Execution Sequence

Use this order unless a dependency requires adjustment:

```text
1. Confirm sources, scope, and superseded material
2. Finalize decisions and unresolved questions
3. Define architecture, interfaces, and state model
4. Create validation harness and core fixtures
5. Build the smallest complete flow
6. Integrate dependent components
7. Add feature breadth
8. Harden failure paths and recovery
9. Run end-to-end acceptance
10. Prepare release or handoff
```

Do not begin a step until its required inputs and checkpoint from the previous step are satisfied.

---

## 10. Decision Points

| Decision Point | When It Occurs     | Options   | Required Evidence       | Blocks         |
| -------------- | ------------------ | --------- | ----------------------- | -------------- |
| [Decision A]   | [Milestone / step] | [Options] | [Test / spike / review] | [Work blocked] |
| [Decision B]   | [Milestone / step] | [Options] | [Test / spike / review] | [Work blocked] |

Decision handling:

* If the decision is resolved, record it in Section 2.
* If the decision remains open, isolate dependent work.
* If uncertainty is high, schedule a small spike with measurable exit criteria.

---

## 11. Risks and Mitigations

| Risk   | Impact   | Mitigation   | Validation          |
| ------ | -------- | ------------ | ------------------- |
| [Risk] | [Impact] | [Mitigation] | [Test / checkpoint] |
| [Risk] | [Impact] | [Mitigation] | [Test / checkpoint] |

Risk checkpoint:

* [ ] High-impact risks are addressed early.
* [ ] Mitigations are testable.
* [ ] Fallbacks exist for external, unstable, or user-dependent flows.

---

## 12. Operational and Maintenance Plan

Define ongoing procedures needed after the initial implementation.

| Area              | Procedure                 | Trigger              | Owner   |
| ----------------- | ------------------------- | -------------------- | ------- |
| Validation        | [Run test suite / checks] | [Every PR / release] | [Owner] |
| Fixture refresh   | [Refresh process]         | [Schedule / failure] | [Owner] |
| Monitoring        | [Signals to watch]        | [Runtime / CI]       | [Owner] |
| Incident handling | [Response process]        | [Failure condition]  | [Owner] |
| Documentation     | [Update process]          | [Behavior change]    | [Owner] |

Maintenance checkpoint:

* [ ] Stale assets have a refresh process.
* [ ] Failed checks produce actionable output.
* [ ] Known flaky or unstable validations are tracked and resolved.
* [ ] Manual fallback or recovery steps are documented.

---

## 13. Definition of Done

A milestone is done only when:

* [ ] Required behavior is implemented.
* [ ] Tests or validation were created before implementation.
* [ ] Success, failure, and edge cases pass.
* [ ] Dependencies and contracts remain stable.
* [ ] Documentation is updated.
* [ ] Performance or resource budgets are met, if applicable.
* [ ] No known blocking regressions remain.
* [ ] The next milestone can start without hidden prerequisite work.

The overall plan is complete when:

* [ ] All release-scope milestones are done.
* [ ] Full validation passes.
* [ ] End-to-end flow is verified.
* [ ] Risks and open questions are documented.
* [ ] Release, deployment, or handoff criteria are satisfied.

---

## 14. Open Questions

| Question   | Why It Matters | Owner   | Needed By          |
| ---------- | -------------- | ------- | ------------------ |
| [Question] | [Impact]       | [Owner] | [Milestone / date] |
| [Question] | [Impact]       | [Owner] | [Milestone / date] |

Open-question rule:

Work blocked by an open question must either wait, use a reversible placeholder, or be isolated behind an interface so it can change later without broad rework.

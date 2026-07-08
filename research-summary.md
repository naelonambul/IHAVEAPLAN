# [Project Name] - Research Summary

| Field | Value |
| --- | --- |
| Status | [Draft / Reviewed / Superseded] |
| Date | [YYYY-MM-DD] |
| Owner | [Researcher / Agent / Team] |
| Companion Plan | [`plan.md`](./plan.md) |
| Companion Work Units | [`work-units.md`](./work-units.md) |
| Source Materials | [PRD / design doc / issue / docs / papers / repo baseline] |

---

## 0. Purpose

This document summarizes research that informs planning and implementation.

It should not be a loose collection of links. It should explain what was investigated, what evidence was found, which decisions it supports, which options were rejected, and what risks or open questions remain.

Use this before or alongside `plan.md` when technical choices, external dependencies, product assumptions, standards, libraries, platforms, APIs, or architecture decisions need evidence.

---

## 1. Research Questions

List the questions this research is meant to answer.

| Question | Why It Matters | Needed By | Decision / Unit Impact |
| --- | --- | --- | --- |
| [Question] | [Planning or implementation impact] | [Plan section / unit / date] | [Decision, milestone, or unit] |
| [Question] | [Planning or implementation impact] | [Plan section / unit / date] | [Decision, milestone, or unit] |

Research-question checkpoint:

- [ ] Each question maps to a planning decision, risk, or work unit.
- [ ] Questions outside the current scope are explicitly deferred.
- [ ] Questions that require live verification are marked as time-sensitive.

---

## 2. Planning Decisions Supported by Research

Record decisions that this research supports.

| Area | Decision | Evidence Summary | Confidence | Revisit Trigger |
| --- | --- | --- | --- | --- |
| [Architecture] | [Decision] | [Evidence] | [High / Medium / Low] | [Condition] |
| [Tooling] | [Decision] | [Evidence] | [High / Medium / Low] | [Condition] |
| [Data / storage] | [Decision] | [Evidence] | [High / Medium / Low] | [Condition] |
| [Testing] | [Decision] | [Evidence] | [High / Medium / Low] | [Condition] |

Confidence guide:

- **High:** supported by primary docs, direct repo evidence, tests, benchmarks, or production constraints.
- **Medium:** supported by credible secondary sources or limited experiments.
- **Low:** plausible but not yet proven; requires spike, prototype, or additional source review.

Decision checkpoint:

- [ ] Decisions are reflected in `plan.md`.
- [ ] Work units depending on these decisions reference the relevant findings.
- [ ] Low-confidence decisions have a spike, fallback, or revisit trigger.

---

## 3. Superseded or Rejected Options

Record options that should not be repeatedly reconsidered unless new evidence appears.

| Option | Rejected Because | Evidence | Revisit Trigger |
| --- | --- | --- | --- |
| [Option] | [Reason] | [Source / test / constraint] | [Condition] |
| [Option] | [Reason] | [Source / test / constraint] | [Condition] |

Rejected-option checkpoint:

- [ ] Rejections are based on evidence, not preference.
- [ ] The accepted alternative is named.
- [ ] Any revisit trigger is concrete.

---

## 4. Findings by Area

Use one subsection per meaningful research area.

### [Area Name]

**Question answered:**  
[Which research question this section answers.]

**Finding:**  
[Concise summary of what was learned.]

**Evidence:**  

- [Primary source, direct experiment, benchmark, repo evidence, or credible secondary source]
- [Relevant limitation or uncertainty]

**Implementation implication:**  
[How this should affect architecture, tests, work units, sequencing, fixtures, or scope.]

**Confidence:** [High / Medium / Low]

**Affected plan or units:**

- [`plan.md` section / milestone]
- [`work-units.md` unit]
- [`unit-XX-name/context.md`]

---

### [Area Name]

**Question answered:**  
[Which research question this section answers.]

**Finding:**  
[Concise summary of what was learned.]

**Evidence:**  

- [Primary source, direct experiment, benchmark, repo evidence, or credible secondary source]
- [Relevant limitation or uncertainty]

**Implementation implication:**  
[How this should affect architecture, tests, work units, sequencing, fixtures, or scope.]

**Confidence:** [High / Medium / Low]

**Affected plan or units:**

- [`plan.md` section / milestone]
- [`work-units.md` unit]
- [`unit-XX-name/context.md`]

---

## 5. Cross-Cutting Recommendations

List recommendations that apply across multiple units or milestones.

- [Recommendation]
- [Recommendation]
- [Recommendation]

Recommendation checkpoint:

- [ ] Recommendations are actionable.
- [ ] Each recommendation maps to a plan section, work unit, test strategy, or risk mitigation.
- [ ] Recommendations do not introduce unapproved scope.

---

## 6. Risks and Mitigations

| Risk | Impact | Evidence | Mitigation | Validation |
| --- | --- | --- | --- | --- |
| [Risk] | [Impact] | [Evidence] | [Mitigation] | [Test / checkpoint / spike] |
| [Risk] | [Impact] | [Evidence] | [Mitigation] | [Test / checkpoint / spike] |

Risk checkpoint:

- [ ] High-impact risks are represented in `plan.md`.
- [ ] Risks that affect sequencing are reflected in `work-units.md`.
- [ ] Mitigations are testable or observable.
- [ ] Manual fallback or recovery paths are documented where automation can fail.

---

## 7. Evidence Quality and Freshness

| Source / Evidence | Type | Date Checked | Stability | Notes |
| --- | --- | --- | --- | --- |
| [Source] | [Primary doc / paper / benchmark / repo evidence / experiment] | [YYYY-MM-DD] | [Stable / Time-sensitive] | [Notes] |
| [Source] | [Primary doc / paper / benchmark / repo evidence / experiment] | [YYYY-MM-DD] | [Stable / Time-sensitive] | [Notes] |

Freshness rules:

- Time-sensitive facts must be rechecked before implementation if they affect correctness, compliance, pricing, availability, APIs, platform behavior, or release decisions.
- Prefer primary sources for technical, legal, medical, financial, security, standards, and platform claims.
- Clearly mark inference separately from directly supported facts.

---

## 8. Materials Gaps

List missing documents, unavailable data, unclear requirements, or incomplete evidence.

| Gap | Why It Matters | Workaround | Owner | Needed By |
| --- | --- | --- | --- | --- |
| [Missing source / data / decision] | [Impact] | [Temporary approach] | [Owner] | [Date / unit] |

Gap checkpoint:

- [ ] Gaps that block implementation are escalated to planning.
- [ ] Non-blocking gaps have reversible assumptions.
- [ ] Workarounds are visible in affected unit context files.

---

## 9. Open Questions

| Question | Why It Matters | Current Best Answer | Owner | Needed By |
| --- | --- | --- | --- | --- |
| [Question] | [Impact] | [Best current answer or unknown] | [Owner] | [Plan section / unit / date] |

Open-question rule:

Work blocked by an open research question must either wait, run a bounded spike, use a reversible placeholder, or be isolated behind a contract.

---

## 10. References

List sources with a short note explaining what each source supports.

| Source | Supports | Notes |
| --- | --- | --- |
| [Title or URL] | [Finding / decision / risk] | [Primary? date checked? limitations?] |
| [Title or URL] | [Finding / decision / risk] | [Primary? date checked? limitations?] |

Reference rules:

- Include enough context that a reviewer can understand why the source matters.
- Prefer links to primary docs, papers, standards, source code, test output, or benchmark artifacts.
- Avoid dumping links that are not tied to a finding or decision.

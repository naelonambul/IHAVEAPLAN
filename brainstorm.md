# [Idea Name] — Brainstorm

| Field         | Value                                             |
| ------------- | ------------------------------------------------- |
| Status        | [Exploratory / Direction chosen / Parked]         |
| Date          | [YYYY-MM-DD]                                       |
| Owner         | [Person / Agent / Team]                           |
| Idea (1 line) | [The vague idea in a single sentence]             |
| Next document | [`research-summary.md`](./research-summary.md) or [`PLAN.md`](./PLAN.md) |

---

## 0. Purpose

This document is the **starting point** for a vague idea — before research, before
planning. Its only job is to explore the option space, pick a **tentative**
direction, and hand a short list of **research questions** to
[`research-summary.md`](./research-summary.md).

**Problem-first, not idea-first.** Software exists to solve a problem. A raw idea
(*"[do X with Y]"*) is not yet a reason to build anything. Before exploring
solutions, **restate the idea as a problem** — whose pain, why it matters, and why
today's workaround falls short. For example, reframe an idea like
*"[use tool T on data D]"* into a problem like *"[who] needs a [safe / fast /
accurate] way to [achieve outcome] because [current workaround] is [insufficient
in some concrete way]."* Do not let this document stop at a solution statement.

This document is:

- **Optional** — skip it if the direction and wedge are already clear; go straight
  to `research-summary.md` or `PLAN.md`.
- **Exploratory and disposable** — it is allowed to be wrong. Park ideas, don't
  polish them.
- **Evidence-free** — no citations, benchmarks, or confidence ratings. That
  discipline belongs to `research-summary.md`.

This document is **not** a plan and **not** a research summary. It makes **no
final decisions**, commits to no stack, and defines no milestones for execution.
It ends by producing *questions*, not answers.

> **Usage note:** when an idea is still vague, explore it here first, choose a
> tentative direction, and write the research questions before moving into a plan.

---

## 1. The Idea (and its problem reframe)

- **Idea as stated:** [One or two sentences, in the user's own words — often a
  solution, e.g. "[do X with Y]".]
- **Why now / trigger:** [What prompted this — a pain, an opportunity, a request.]
- **Reframed as a problem:** [Restate as *"[who] needs [outcome] because [current
  workaround] is [insufficient]"*. If you can't write this yet, that gap is the
  first thing to explore. Full detail in §2.]

---

## 2. Problem Definition (problem-first)

Answer these before exploring solutions. Guesses are fine — mark what's uncertain.

- **Whose problem is it?** [Specific people, roles, or segment — not "everyone".]
- **What pain or inefficiency exists?** [The concrete cost: wasted time, money,
  errors, risk, missed opportunity.]
- **Why is the current workaround insufficient?** [What people do today, and where
  it breaks down. If there is no pain with the status quo, there may be no problem.]
- **What outcome would count as a real improvement?** [An observable better state —
  faster / cheaper / safer / more accurate, ideally roughly measurable.]
- **Problem assumptions to test** *(is the problem even real?)*: [The beliefs that,
  if wrong, mean nothing should be built — e.g. "these users actually feel this
  pain", "they would change their workflow to fix it".]

*(Solution/approach assumptions come later, in §8. Keep §2 about the problem.)*

---

## 3. Candidate Users / Markets

Who might care? Keep it a short list of guesses.

- [User / segment / market — one line on why they might care.]
- [User / segment / market — ...]
- [User / segment / market — ...]

---

## 4. Candidate Directions / Wedges

Possible entry points. Score on **gut feel only** — this is *not* evidence, just a
way to compare and pick where to look first.

| Direction / wedge | Urgency | Willingness to pay | Feasibility | Data / access | Notes |
| --- | --- | --- | --- | --- | --- |
| [Candidate A] | [H/M/L] | [H/M/L] | [H/M/L] | [H/M/L] | [gut-feel note] |
| [Candidate B] | [H/M/L] | [H/M/L] | [H/M/L] | [H/M/L] | [gut-feel note] |
| [Candidate C] | [H/M/L] | [H/M/L] | [H/M/L] | [H/M/L] | [gut-feel note] |

Add or drop criteria freely (e.g. portfolio value, competition, risk). The table
is a thinking aid, not a scorecard to defend.

**Leaning toward:** [Candidate X, tentatively — one line on why.]

---

## 5. Technical Hypotheses & Option Space

Rough technical guesses and the choices worth exploring. No commitment.

- **Approach options:** [Option 1] · [Option 2] · [Option 3]
- **Hunches:** [e.g. "probably needs X"; "Y might be enough"; "Z is likely overkill".]
- **Unknowns that would change the approach:** [What we'd need to learn.]

---

## 6. Constraints

The real-world limits that shape any direction.

- **Hardware / environment:** [What's available.]
- **Time / budget:** [Deadlines, effort ceiling.]
- **Skills / team:** [What we can realistically build/operate.]
- **Privacy / legal / compliance:** [Sensitivities, if any.]
- **Other:** [Anything non-negotiable.]

---

## 7. Candidate First Milestones

Not an execution plan — just: *what would kill the most uncertainty fastest?*
Prefer a cheap experiment or benchmark over building the whole thing.

- [Candidate milestone — the uncertainty it resolves.]
- [Candidate milestone — the uncertainty it resolves.]
- [Candidate milestone — the uncertainty it resolves.]

**Most uncertainty-reducing first step:** [The one to do first, and why.]

---

## 8. Recommended (Tentative) Direction

- **Direction:** [The chosen wedge/approach — still reversible.]
- **Why this one:** [Short reasoning against the alternatives.]
- **Parked (not rejected):** [Other candidates, kept for later if this stalls.]
- **Biggest assumptions to challenge:** [The 2–4 beliefs that, if wrong, break it.]

---

## 9. Research Questions to Carry Forward

The main output of this document. Each becomes a row in
[`research-summary.md`](./research-summary.md) §1.

| Question | Why it matters | What decision it affects |
| --- | --- | --- |
| [Question] | [What hinges on it] | [Wedge / approach / milestone] |
| [Question] | [What hinges on it] | [Wedge / approach / milestone] |
| [Question] | [What hinges on it] | [Wedge / approach / milestone] |

---

## Exit Checkpoint

Move on only when:

- [ ] The **problem** is stated problem-first (§2): whose pain, why the current
      workaround is insufficient, and what outcome would be a real improvement.
- [ ] One direction is chosen (others **parked, not deleted**).
- [ ] 3–5 concrete research questions are written above.
- [ ] The biggest assumptions to challenge are named.
- [ ] Constraints that could veto the direction are listed.

Then hand off:

- **Needs evidence first** → [`research-summary.md`](./research-summary.md) (start
  at §1 with the questions above).
- **Direction is clear and low-risk** → [`PLAN.md`](./PLAN.md) directly.

> Keep this file as a record of *why* the direction was chosen and what was parked.
> If the direction later collapses, return here rather than starting from scratch.

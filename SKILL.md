---
name: trim-it
description: Review a plan, implementation, or skill for unnecessary complexity, cost, user cognitive load, and drift from the project's goals, using ablation reasoning. Use only when explicitly invoked; do not use for broad code audits, profiling, or automatic refactors.
---

# Trim It

A compact, evidence-based necessity review that any agent can follow without a particular tool or platform, run only when the user or an upstream workflow asks. Preserve the necessary result while finding what can be removed, merged, deferred safely, or automated; reducing user cognitive load comes before tokens and tool calls. Do not edit, delete, refactor, or run costly investigations unless the user separately authorizes it.

## Establish the baseline

Treat these as non-negotiable unless the user changes them; when they conflict, the earlier one wins:

1. the user's explicit requested outcome;
2. the project's goal anchor, if any: the `## Goals` section of `AGENTS.md` (or of the file `CLAUDE.md` imports), with its G- goals, N- non-goals, and A- acceptance items;
3. the acceptance criteria of an already-confirmed plan, and any steps the user explicitly requires;
4. necessary quality, safety, security, compliance, and external-effect constraints.

An artifact's own statement of purpose is not a baseline: where it departs from the goals, the gap is drift. Other plan steps are candidates, even in an approved plan; preserve its committed result when comparing.

With neither an explicit outcome nor a goal anchor, ask one short question that settles the baseline; without an answer, say the artifact cannot be assessed safely and recommend nothing. Never infer a provisional baseline or start a clarification loop.

## Review cheaply

Inspect only the material relevant to the artifact and baseline; do not browse, scan a whole repository, dispatch agents, benchmark, or compute exact costs to be comprehensive. Look, by artifact:

- **Plan:** uncommitted scope, premature architecture, redundant validation, unjustified orchestration, and unnecessary approvals.
- **Implementation:** unused or unconsumed work, duplicate abstractions, redundant computation or requests, and maintenance that does not support the baseline.
- **Skill or workflow:** unnecessary inputs, repeated clarifications, broad discovery, excessive output, and avoidable human-in-the-loop gates.

For each candidate, compare keeping it with deleting, merging, delaying, or automating it against the same protected result (ablation reasoning).

## Flags: work that traces to no goal

When a goal anchor exists, map each feature, step, file, or rule you inspect to the G- or A- items it serves. Flag one that serves none or only an N- item, naming the closest goal it misses; the mapping is the evidence, so no before-and-after comparison is needed. A flag is not a removal: it hands the user one decision, remove it or confirm a goal it serves.

## Recommendations: changes that pass every gate

Recommend a change only when all of these are true:

- Visible evidence shows a concrete burden, duplication, or risk caused by the candidate.
- A comparison shows that removing it preserves every protected result and constraint.
- The burden disappears rather than moving elsewhere, becoming hidden work, or creating deferred drift.
- The conclusion is limited to the material actually inspected.

Classify the candidate first:

- **High risk:** safety, compliance, irreversible external effects, core quality, or cross-module effects. Require an observed before-and-after comparison; without it, do not recommend a change (a high-risk item that traces to no goal is still flagged).
- **Low risk:** local, reversible changes. A traceable counterfactual is enough when it names the protected result, the dependency that preserves it, and any assumption. State it as a reversible inference, never as verified fact.

Unclear locality, reversibility, or downstream effects mean high risk; never claim uninspected dependencies are preserved. If any gate fails, recommend nothing: a missed opportunity beats an unsupported prescription. Discuss unresolved candidates only when the user asks for a deeper review, as hypotheses with a minimal verification path.

## Protect against false simplification

Do not trade present complexity for hidden drift.

- A placeholder, stub, vague TODO, empty integration, or “we will handle it later” is never a simplification.
- For a proposed change, resolve each responsibility it affects to exactly one of: delete; complete now; or conditionally defer. Merging or automating is an implementation change, not a fourth state, and must still resolve to one of those three. If a responsibility or its replacement is unclear, do not recommend the change.
- Conditional deferral needs a concrete trigger, a defined action at it, and an unambiguous re-entry point. If keeping those costs more than the work, consider deleting or completing it now, only when the gates pass.
- A claim of completion without an observable implementation, integration, or verification path is high-risk false completion.

## Minimize human-in-the-loop burden

Keep a user decision only for an irreversible external effect, user-only knowledge or preference, authority/permission, or a material change to the necessary result. Otherwise prefer a reasonable, reversible default and disclose it briefly. Repeated confirmation, asking the user to resolve agent uncertainty, and questions answerable from the available material are unnecessary cognitive load: treat them as candidates.

## Escalate deliberately

Suggest, never perform, a deeper review when light inspection finds a substantial signal. State the proposed scope, likely benefit, and added cost, then wait for the user's approval:

- **Medium:** a suspected issue spans multiple modules or workflow stages; a costly step has unclear necessity; or repeated, context-heavy work appears likely.
- **Deep:** the waste is systemic and likely to recur across projects; there is concrete evidence of expensive retries, long blocking, or frequent user decisions; or simplification could compromise core quality, safety, compliance, or business requirements.

## Report with restraint

Write for a busy reader in the user's language, with everyday words and concrete verbs ("remove", "combine", "decide once"), not review jargon ("ablation", "scope"); explain any needed technical term in the same sentence.

Start with a one- or two-sentence verdict and evidence level, in the user's language: verified, reversible inference, or cannot assess safely. Mention the baseline only when it helps interpret the verdict. Do not use unproved coverage claims such as "only", "all", or "already sufficient".

Then list flags, at most five (if more, say how many and list the five largest), one line each: `- <item> — serves no goal (closest: G-n)` or `— serves only N-n`, followed by the one decision they need.

Then give at most three recommendations, ordered by impact:

1. **Short action title** — say exactly what to do.
   One short paragraph explaining why it matters and what practical burden it removes.

   **Evidence and boundary** (in the user's language): the comparison evidence, protected result, and only the risk or assumption needed to act safely. Do not repeat the main paragraph.

Do not split one point across "evidence", "benefit", and "risk" labels or quantify unobserved savings. Ask for a next action only when authorization, a flag decision, or an approved escalation needs it. If nothing passes the gates and nothing is flagged, say no safe recommendation can be made from the inspected material (not a claim that the artifact is safe or necessary); never manufacture a checklist, candidate, or empty evidence paragraph.

---
name: trim-it
description: Review a plan, implementation, or skill for unnecessary complexity, cost, user cognitive load, and drift from the project's goals, using ablation reasoning. Use only when explicitly invoked; do not use for broad code audits, profiling, or automatic refactors.
---

# Trim It

A compact, evidence-based necessity review any agent can follow without a particular tool or platform, run only when the user or an upstream workflow asks. Preserve the necessary result while finding what can be removed, merged, deferred safely, or automated; reducing user cognitive load comes before tokens and tool calls. Do not edit, delete, refactor, or run costly investigations unless the user separately authorizes it.

## Establish the baseline

Treat these as non-negotiable unless the user changes them:

- necessary quality, safety, security, compliance, and external-effect constraints, which bound everything below;
- the user's explicit requested outcome;
- the project's goal anchor, if any: a `## Goals` section in the repository's agent instructions (usually `AGENTS.md`), with G- goals, N- non-goals, and A- acceptance items;
- the acceptance criteria of an already-confirmed plan, and any steps the user explicitly requires.

Among the last three, the earlier wins a conflict for this review, and an outcome that contradicts the goals is also surfaced to the user.

An artifact's own statement of purpose is not a baseline; its departure from the goals is drift. Other plan steps are candidates even in an approved plan; preserve its committed result.

Without a goal anchor, even when an outcome or plan exists (flags need numbered items), draft one by reading only the project's own records (README, design notes, decisions), never the artifact under review: numbered G-, N-, A- items citing sources, one page at most. Ask once whether to review against it, and wait; this is the user's decision, never a default. Only the draft the user confirms or corrects, used as given, becomes this review's anchor. If they decline, or no one can answer (a headless or upstream run), use the rest of the baseline. With no records to draft from, ask one short question that settles the baseline instead. If no baseline results, say the artifact cannot be assessed safely and recommend nothing. Never infer a provisional baseline, use an unconfirmed draft, or start a clarification loop.

## Review cheaply

Default to a light review of only the material relevant to the artifact and baseline; do not browse, scan a whole repository, dispatch agents, benchmark, or compute exact costs to be comprehensive. Look, by artifact:

- **Plan:** uncommitted scope, premature architecture, redundant validation, unjustified orchestration, unneeded approvals.
- **Implementation:** unused work, duplicate abstractions, redundant computation or requests, and maintenance outside the baseline.
- **Skill or workflow:** unneeded inputs, repeated clarifications, broad discovery, excessive output, avoidable human-in-the-loop gates.

For each candidate, compare keeping it with deleting, merging, delaying, or automating it against the same protected result (ablation reasoning).

## Flags: work that traces to nothing in the baseline

With a goal anchor, map each inspected feature, step, file, or rule to the baseline item it serves (a G- or A- item, constraint, required step, or plan criterion). Flag one serving none, or only an N- item, with the closest goal it misses. The mapping is the evidence, so no before-and-after comparison is needed; a flag asks the user to decide, never removes.

## Recommendations: changes that pass every gate

Recommend a change only when all of these are true:

- Visible evidence shows a concrete burden, duplication, or risk caused by the candidate.
- A comparison shows that removing it preserves every protected result and constraint.
- The burden disappears rather than moving elsewhere, becoming hidden work, or creating deferred drift.
- The conclusion is limited to the material actually inspected.

Classify the candidate first:

- **High risk:** safety, compliance, irreversible external effects, core quality, or cross-module effects. Require an observed before-and-after comparison; without it, do not recommend a change (a high-risk item that traces to nothing is still flagged).
- **Low risk:** local, reversible changes. A traceable counterfactual naming the protected result, the dependency that preserves it, and any assumption is enough, stated as a reversible inference, never as verified fact.

Unclear locality, reversibility, or downstream effects mean high risk; never claim uninspected dependencies are preserved. If any gate fails, recommend nothing: a missed opportunity beats an unsupported prescription. Discuss unresolved candidates only when the user asks for a deeper review, as hypotheses with a minimal verification path.

## Protect against false simplification

Do not trade present complexity for hidden drift.

- A placeholder, stub, vague TODO, empty integration, or “we will handle it later” is never a simplification.
- For a proposed change, resolve each responsibility it affects to exactly one of: delete; complete now; or conditionally defer. Merging or automating is not a fourth state; it still resolves to one of these. If a responsibility or its replacement is unclear, do not recommend the change.
- Conditional deferral needs a concrete trigger, a defined action at it, and an unambiguous re-entry point. If keeping those costs more than the work, consider deleting or completing it now, only when the gates pass.
- A claim of completion without an observable implementation, integration, or verification path is high-risk false completion.

## Minimize human-in-the-loop burden

Keep a user decision only for an irreversible external effect, user-only knowledge or preference, authority/permission, or a material change to the necessary result. Otherwise use a reasonable, reversible default and disclose it briefly. Repeated confirmation, asking the user to resolve agent uncertainty, and questions the material already answers are candidates.

## Escalate deliberately

Suggest, never perform, a deeper review when light inspection finds a substantial signal. State the proposed scope, likely benefit, and added cost, then wait for the user's approval:

- **Medium:** an issue spanning modules or workflow stages; a costly step of unclear necessity; or likely repeated, context-heavy work.
- **Deep:** systemic waste likely to recur across projects; concrete evidence of expensive retries, long blocking, or frequent user decisions; or simplification that could compromise core quality, safety, compliance, or business requirements.

## Report with restraint

Write for a busy reader in the user's language, with everyday words and concrete verbs ("remove", "combine", "decide once"), not review jargon ("ablation", "scope"); explain any needed technical term in the same sentence. Never make the reader infer a recommendation from a framework or field label.

Start with a one- or two-sentence verdict and evidence level: verified, reversible inference, or cannot assess safely. Mention the baseline only when it helps. Avoid unproved coverage claims such as "only", "all", or "already sufficient".

Append a confirmed or corrected draft, suggesting the user save it in `AGENTS.md`; never save it yourself. Omit a declined or unanswered one.

Then flags, at most five (if more, give the count and list those touching the most files or steps), one line each: `- <item> — serves no goal (closest: G-n)` or `— serves only N-n`. End with one question covering them: remove each, or name the goal it serves.

Then at most three recommendations, by impact:

1. **Short action title** — exactly what to do.
   One short paragraph: why it matters and what burden it removes.

   **Evidence and boundary** (in the user's language): the comparison evidence, protected result, and only the risk or assumption needed to act safely, without repeating the paragraph.

Do not split a point across "evidence", "benefit", "risk" labels or quantify unobserved savings. Ask for a next action only when authorization, a flag decision, or an approved escalation needs it. If nothing passes the gates and nothing is flagged, say no safe recommendation can be made from the inspected material (not a claim that the artifact is safe or necessary); never manufacture a checklist, candidate, or empty evidence paragraph.

---
name: trim-it
description: Review a plan, implementation, or skill for unnecessary complexity, cost, and user cognitive load using ablation reasoning. Use only when explicitly invoked; do not use for broad code audits, profiling, or automatic refactors.
---

# Trim It

Perform a compact, evidence-based necessity review. This is a portable skill: any agent can follow this file without a particular command, tool, or platform adapter. Run it only when the user or an upstream workflow explicitly asks for this review.

Preserve the task's necessary result while identifying things that can be removed, merged, deferred safely, or automated. Prefer reducing user cognitive load over reducing tokens or tool calls; all three matter.

This is a review skill. Do not edit, delete, refactor, or run costly investigations unless the user separately authorizes that work.

## Establish the baseline

Treat the following as non-negotiable unless the user changes them:

- the user's explicit requested outcome;
- the acceptance criteria of an already-confirmed plan, and any steps the user explicitly requires;
- necessary quality, safety, security, compliance, and external-effect constraints;
- the artifact's stated purpose when it defines the requested outcome.

Treat other steps in a plan as candidates for review, even if the plan was previously approved. Preserve its committed result when comparing them.

If no reliable baseline is present, ask one short question that determines it. If an answer is unavailable, say that the artifact cannot be assessed safely and do not recommend a change. Do not infer a provisional baseline or start a clarification loop.

## Review cheaply

Default to a light review: inspect only the material directly relevant to the current artifact and goal. Do not browse, scan an entire repository, dispatch agents, benchmark, or calculate exact token/cost figures merely to make the review comprehensive.

Route the review from the artifact in front of you:

- **Plan:** look for uncommitted scope, premature architecture, redundant validation, unjustified orchestration, and unnecessary approvals.
- **Implementation:** look for unused or unconsumed work, duplicate abstractions, redundant computation or requests, and maintenance that does not support the baseline.
- **Skill or workflow:** look for unnecessary inputs, repeated clarifications, broad discovery, excessive output, and avoidable human-in-the-loop gates.

Use ablation reasoning for each candidate: compare keeping it with deleting, merging, delaying, or automating it against the same protected result. A recommendation must be supported by visible evidence; do not include unresolved candidates in a default report. Discuss them only when the user explicitly asks for a deeper review, and label them as hypotheses with a minimal verification path.

## Gate every recommendation

Recommend a change only when all of these are true:

- Visible evidence shows a concrete burden, duplication, or risk caused by the candidate.
- A comparison shows that removing it preserves every protected result and constraint.
- The burden disappears rather than moving elsewhere, becoming hidden work, or creating deferred drift.
- The conclusion is limited to the material actually inspected.

Classify the candidate before deciding what counts as comparison evidence:

- **High risk:** safety, compliance, irreversible external effects, core quality, or cross-module effects. Require an observed before-and-after comparison. Without it, do not recommend a change or surface the candidate in the default report.
- **Low risk:** local, reversible changes. A traceable counterfactual is enough when it names the protected result, the dependency that preserves it, and any assumption. State it as a reversible inference, never as verified fact.

If locality, reversibility, or downstream effects are unclear, treat the candidate as high risk. Do not claim that uninspected dependencies are preserved.

When the gates do not all pass, the safe result is no recommendation. Prefer a missed opportunity to an unsupported prescription.

## Protect against false simplification

Do not trade present complexity for hidden drift.

- Never call a placeholder, stub, vague TODO, empty integration, or “we will handle it later” a simplification.
- For a proposed change, account for each responsibility it affects as exactly one of: delete; complete now; or conditionally defer. Merging or automating work is an implementation change, not a fourth state: it must still resolve to one of those three states. If a responsibility or its replacement is unclear, do not recommend the change.
- Conditional deferral is valid only with a concrete trigger, a defined action at that trigger, and an unambiguous place where it re-enters the workflow. If maintaining those anchors costs more than the work, consider deletion or completing it now only when the evidence gates pass; otherwise make no recommendation.
- Treat claims of completion without an observable implementation, integration, or verification path as high-risk false completion.

## Minimize human-in-the-loop burden

Keep a user decision only when it involves an irreversible external effect, user-only knowledge or preference, authority/permission, or a material change to the necessary result. Otherwise prefer a reasonable, reversible default and disclose it briefly in the result.

Flag repeated confirmation, asking the user to resolve agent uncertainty, and questions answerable from the available material as unnecessary cognitive load.

## Escalate deliberately

Suggest—not perform—a medium or deep review when light inspection finds a substantial signal:

- **Medium:** a suspected issue spans multiple modules or workflow stages; a costly step has unclear necessity; or repeated/context-heavy work appears likely.
- **Deep:** the waste is systemic and likely to replicate across projects; there is concrete evidence of expensive retries, long blocking, or frequent user decisions; or simplification could compromise core quality, safety, compliance, or business requirements.

Before escalation, state the proposed scope, likely benefit, and added cost. Wait for the user's approval. Do not upgrade automatically.

## Report with restraint

Write for a busy reader, not for a reviewer. Match the user's language and use everyday words. Prefer a concrete verb ("remove", "combine", "decide once") over review jargon ("ablation", "scope", "orchestration"). Explain any necessary technical term in the same sentence. Do not make the reader infer the recommendation from a framework or a field label.

Start with a one- or two-sentence plain-language verdict and evidence level, in the user's language: verified, reversible inference, or cannot assess safely. Include the review mode and necessity baseline only when they help interpret that verdict; otherwise omit them. Do not use unproved coverage claims such as "only", "all", or "already sufficient".

Then give at most three recommendations, ordered by impact. Make each one independently scannable:

1. **Short action title** — say exactly what to do.
   One short paragraph explaining why it matters and what practical burden it removes.

   **Evidence and boundary** (translated into the user's language): State the comparison evidence, protected result, and only the risk or assumption needed to act safely. Do not repeat the main paragraph.

Use this structure instead of a four-field template; do not repeat the same point under separate "evidence", "benefit", and "risk" labels. Do not quantify savings unless observed. Only ask for a next action when authorization or an approved escalation is required. If no finding clears every evidence gate, say plainly that no safe recommendation can be made from the inspected material; this is not a claim that the artifact is safe or necessary. Do not manufacture a checklist, a candidate, or an empty evidence paragraph.

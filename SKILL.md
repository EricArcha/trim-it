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
- an already-confirmed plan and its acceptance criteria;
- necessary quality, safety, security, compliance, and external-effect constraints.

Everything else is eligible for scrutiny. If no reliable baseline is present, ask one short question. If an answer is unavailable, infer a provisional baseline from the visible artifact, state that inference and its confidence, then continue. Do not block or start a clarification loop.

## Review cheaply

Default to a light review: inspect only the material directly relevant to the current artifact and goal. Do not browse, scan an entire repository, dispatch agents, benchmark, or calculate exact token/cost figures merely to make the review comprehensive.

Route the review from the artifact in front of you:

- **Plan:** look for uncommitted scope, premature architecture, redundant validation, unjustified orchestration, and unnecessary approvals.
- **Implementation:** look for unused or unconsumed work, duplicate abstractions, redundant computation or requests, and maintenance that does not support the baseline.
- **Skill or workflow:** look for unnecessary inputs, repeated clarifications, broad discovery, excessive output, and avoidable human-in-the-loop gates.

Use ablation reasoning for each candidate: if this item were deleted, merged, delayed, or automated, would the necessary result and constraints still hold? Recommend a change only when the answer is supported by visible evidence. Label unresolved cases as hypotheses, not findings.

## Protect against false simplification

Do not trade present complexity for hidden drift.

- Never call a placeholder, stub, vague TODO, empty integration, or “we will handle it later” a simplification.
- Classify every responsibility as exactly one of: delete; complete now; or conditionally defer. Merging or automating work is an implementation change, not a fourth state: it must still resolve to one of those three states.
- Conditional deferral is valid only with a concrete trigger, a defined action at that trigger, and an unambiguous place where it re-enters the workflow. If maintaining those anchors costs more than the work, recommend deletion or completing it now instead.
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

State the review mode and the necessity baseline in one short line. Then provide no more than three high-confidence, action-oriented findings, sorted by expected impact. For each, include:

- **Change:** what to remove, merge, defer, or automate.
- **Evidence:** why the necessary result remains protected.
- **Benefit:** qualitative savings in user decisions, calls/tokens, time, or maintenance. Never invent precise figures.
- **Risk:** a relevant caveat or reversible path.

Only ask for a next action when authorization or an approved escalation is required. If no finding clears the evidence threshold, say plainly that no worthwhile trimming was found; do not manufacture a checklist to appear useful. Match the user's language.

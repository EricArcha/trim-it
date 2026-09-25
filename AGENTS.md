# Repository Guidelines

## Project Structure & Module Organization

This repository packages the portable `trim-it` Codex skill. Its core design
idea is **ablation reasoning** (消融实验): assess a candidate by comparing the
protected result with and without it, then recommend removal only when visible
evidence shows the result and constraints remain intact. Keep this primary
workflow, its constraints, and reporting rules in `SKILL.md`. Keep agent-facing
UI metadata in `agents/openai.yaml`; its `display_name`, descriptions, and
default prompt should accurately reflect the skill. `.gitignore` holds
local-only exclusions. There are no source, asset, or test directories.

## Development & Validation

There is no build system or automated test suite. Validate changes before
submitting them:

- Read `SKILL.md` top to bottom and check that instructions are internally
  consistent, actionable, and within the documented review-only scope.
- Confirm the YAML remains valid and that the default prompt references
  `$trim-it` exactly.
- Review the diff with `git diff --check` and `git diff` to catch whitespace
  errors and unintended wording changes.

## Writing Style & Naming Conventions

Use Markdown with clear `#`/`##` headings, short paragraphs, and direct,
instructional language. Preserve ablation reasoning as the basis for every
necessity recommendation: name the protected result, compare removing or
changing the candidate, and state the evidence boundary. Prefer concrete verbs
such as “remove”, “defer”, and “verify”; avoid unsupported claims, vague rules,
and duplicated policy.
Preserve the existing front matter keys in `SKILL.md` (`name`, `description`).
Use two-space indentation for YAML nested keys and double-quoted YAML strings
when following the existing `agents/openai.yaml` style. Keep filenames lowercase
except for standard files such as `SKILL.md` and `AGENTS.md`.

## Testing Guidelines

Treat a focused example prompt as the acceptance test: it should lead to a
compact, evidence-based necessity review without editing the reviewed artifact.
When changing policy, verify all affected rules agree on the baseline, evidence
gates, risk levels, and reporting limits.

## Commit & Pull Request Guidelines

Use concise, imperative commit subjects, following existing history—for example,
`Add evidence gates to trim-it` or `Improve trim-it report readability`.
Keep each commit narrowly focused. Pull requests should describe the behavior
change, identify affected files, and include a representative prompt/output
example when user-facing guidance or report format changes. Link the related
issue when one exists.

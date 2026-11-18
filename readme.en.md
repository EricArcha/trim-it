# Trim It

**Review development plans, implementations, and AI workflows for work you can skip.**

[中文](readme.md) · Created by [Eric / EricArcha](https://github.com/EricArcha)

When AI helps build a project, it can keep adding features, steps, and requests for confirmation. Give Trim It your development plan, implementation, or AI workflow and the result you need to deliver. It checks what could be removed, combined, or deferred, and explains the evidence.

Trim It is a working guide for AI, called a Skill. You invoke it explicitly. By default, it gives advice without changing your files.

## Try it for the first time

You need a working Codex setup. **No coding or reading repository files required.**

1. Start a Codex chat and paste:

   ```text
   $skill-installer Install trim-it from https://github.com/EricArcha/trim-it. The Skill is at the repository root; use trim-it as the installation name.
   ```

2. After installation, type `$trim-it` in a chat. If the Skill does not appear, restart Codex and try again.
3. Paste the exercise below, or use your own development plan. State the result you need to preserve.

Installation needs network access, which Codex may ask you to allow. This installs a local Skill; installation in other AI tools depends on their Skill support. See the [official OpenAI guide](https://learn.chatgpt.com/docs/build-skills) for installation and invocation guidance.

## Copy this exercise

```text
$trim-it

Review the development plan below. Give advice without editing files.

The following goal anchor is confirmed for this exercise and is unrelated to the current project:
## Goals
G-1: Build a local to-do list tool for personal use.
N-1: No accounts, team collaboration, or cloud sync.
A-1: Add and complete tasks, retain them after reopening, and provide startup instructions.

Plan:
1. Implement adding tasks, marking them complete, and saving locally.
2. Write startup instructions in the README.
3. Copy the identical startup instructions into a second document and maintain both separately. No other files link to the second document.
4. Add a login page and team permission management.

Identify evidence-based simplifications and goal drift that needs my decision.
```

The kind of change to look for (**illustrative, not a recorded test result**):

> **Skip the second copy of the startup instructions.** The README provides the same content; maintaining two copies adds update work. From the supplied plan, keeping the README should meet the instructions requirement, assuming the second copy has no additional content or references depending on it.
>
> **Decide whether to keep login and team permissions.** They serve accounts and team collaboration, both stated non-goals. This needs your decision; nothing is removed automatically.

The useful difference: you can see **what to skip, why, and under which conditions**. Trim It does not promise a removable item in every review. Without enough evidence, it will say it cannot safely recommend a change.

## When to use it

| Your situation | Try asking |
| --- | --- |
| An AI-generated development plan keeps growing | `$trim-it Check which development steps can be skipped while preserving the delivery result.` |
| An AI workflow keeps asking questions | `$trim-it Check which confirmations can be reduced and which decisions need me.` |
| Features keep accumulating | `$trim-it Compare this work with the project goals and flag work that serves none.` |

Include the material and your goals. Remove unnecessary client or personal information before sharing.

## What to expect

- **Establish the result to protect.** If the project has no clear goals, you may be asked to confirm a draft based on its existing records. Without records, expect one necessary question.
- **Require evidence.** A recommendation must explain how the change preserves the result. Safety, irreversible effects, and core quality require an observed before-and-after comparison.
- **Keep the report compact.** Up to 3 recommendations and 5 goal-drift flags, with a total count when more flags exist. Recommendations are not executed automatically. A wider review needs your approval.

Use it for a focused necessity review. A full code audit, performance testing, or automatic refactoring needs a separate request. Results depend on the AI, material, and evidence available.

## Updates and feedback

To update your installed copy, ask Codex: “Update trim-it from its original repository, preserve my changes, and tell me about any conflicts first.” Updating a repository checkout does not automatically update a separate installed copy.

For questions or improvements, open a [GitHub issue](https://github.com/EricArcha/trim-it/issues) with your intended result, input, and actual response. Sanitize examples first. For security concerns, read [Sensitive concerns](contributing.md).

[Changelog](changelog.md) · [Contributing](contributing.md)

© 2026 Eric / EricArcha · [MIT License](LICENSE). You may modify, share, and use commercially with the copyright and permission notice retained.

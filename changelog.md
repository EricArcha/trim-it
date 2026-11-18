# Changelog / 变更记录

按可核对的 Git 历史整理。日期是提交日期，不代表公开发布日期。仓库目前没有版本标签，因此不补造版本号。

Based on verifiable Git history. Dates are commit dates, not public release dates. No version numbers are assigned retroactively; the repository currently has no version tags.

## Unreleased / 未发布

- 为双语 README 增加许可、Codex Skill、只审查及趣味徽章。
  Added license, Codex Skill, review-only, and playful badges to both READMEs.

- 采用 MIT 许可证，版权署名为 Eric / EricArcha。
  Adopted the MIT License with copyright attributed to Eric / EricArcha.
- 新增面向新手的中文、英文 README，围绕开发与 AI 工作流，包含安装提示、开发计划练习和示意回答。
  Added beginner-friendly Chinese and English READMEs focused on development and AI workflows, with installation guidance, a development-plan exercise, and an illustrative response.
- 新增变更记录和精简的贡献指南，将维护与安全要点合并其中；保留 Eric / EricArcha 署名。
  Added a changelog and a compact contribution guide containing maintenance and security guidance; retained Eric / EricArcha attribution.
- 补充本地敏感文件的忽略规则。此次文档准备不改变审查流程或调用配置。
  Added ignore rules for local sensitive files. This documentation preparation does not change the review workflow or invocation settings.

## 2026-11-05

- 加入项目目标基准，区分“没有服务目标、待用户决定的事项”和“有证据支持的精简建议”。质量和安全约束优先；明确请求与项目目标冲突时需说明。
  Added a project goal anchor and separated goal-drift flags requiring a user decision from evidence-based recommendations. Quality and safety remain binding; conflicts between explicit requests and project goals are surfaced.
- 缺少目标基准时，根据项目自身记录起草并等待用户确认。拒绝或无人可回答时使用其他已知基准，不把未确认草稿写进报告。
  When goals are missing, draft them from project records and wait for confirmation. If declined or no answer is possible, use the remaining baseline and omit the unconfirmed draft from the report.
- 将扩大审查的规则统一为：说明要检查什么、收益和成本，获批后继续。
  Consolidated review expansion into one rule: describe the added inspection, benefit, and cost, then wait for approval.

历史依据 / History: `6b7320d` → `3c09de1`（7 次提交 / 7 commits）。

## 2026-09-25

- 新增仓库协作规范，明确证据、安全边界和低风险建议的适用条件。
  Added repository guidelines and clarified evidence, safety boundaries, and conditions for low-risk recommendations.

历史依据 / History: `9b0ccbd`, `d6b98bf`。

## 2026-09-13

- 建立可移植 Skill 和 Codex 调用配置，仅在明确请求时使用。
  Created the portable Skill and Codex invocation metadata, with explicit invocation required.
- 改进报告可读性，逐步加入证据要求、高低风险区分和防止虚假精简的约束。
  Improved report readability and introduced evidence gates, risk classification, and safeguards against false simplification.

历史依据 / History: `1646e54`, `77a3d95`, `58de537`, `e20481a`。

早期报告格式曾包含折叠证据区；当前格式以 `SKILL.md` 为准。
An earlier report format used collapsible evidence; `SKILL.md` defines the current format.

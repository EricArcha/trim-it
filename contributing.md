# Contributing / 参与贡献

## 反馈与修改 / Feedback and changes

在 [Issues](https://github.com/EricArcha/trim-it/issues) 提供：你要保住的结果、已脱敏的输入、实际回答和期望变化。没有代码经验也可以贡献。

In [Issues](https://github.com/EricArcha/trim-it/issues), include the result to preserve, sanitized input, actual response, and expected change. Coding experience is not required.

修改前读 `SKILL.md` 和 `AGENTS.md`。一次解决一个问题，保持默认只审查的边界；改动用户可见行为时，同步两份 README 和变更记录。示例保持在开发与 AI 工作流内，示意与实测明确区分。

Read `SKILL.md` and `AGENTS.md` before making changes. Address one problem, preserve review-only defaults, and update both READMEs and the changelog for user-facing changes. Keep examples within development and AI workflows; distinguish illustrations from recorded tests.

## 验证与推送 / Validation and publication

本项目没有构建系统或自动测试套件。按 `AGENTS.md` 检查指令一致性与 YAML，用聚焦示例验证策略改动；PR 写明问题、变化和验证结果。

There is no build system or automated test suite. Follow `AGENTS.md` to check instruction consistency and YAML, use a focused example for policy changes, and describe the problem, change, and validation in your PR.

```sh
git diff --check
git diff
git status --short
```

新增文件也要逐份阅读。公开推送前检查文件及将推送的历史，包括提交信息和邮箱；保留署名，清理密钥、私人路径和客户数据。`.gitignore` 不会清理已提交内容。

Read new files too. Before a public push, inspect files and the history being pushed, including commit messages and emails. Preserve attribution and remove credentials, private paths, and client data. `.gitignore` does not sanitize committed content.

## 维护与许可 / Maintenance and license

[Eric / EricArcha](https://github.com/EricArcha) 维护本项目，决定合并和发布。围绕证据讨论，尊重参与者；不承诺固定更新或响应时限。许可见 [MIT License](LICENSE)，保留已有版权与许可声明。未发布变更写入 `changelog.md`，不虚构版本号。

[Eric / EricArcha](https://github.com/EricArcha) maintains the project and decides merges and releases. Discuss evidence and respect contributors; no fixed update or response time is promised. See the [MIT License](LICENSE) and retain existing copyright and permission notices. Record pending changes in `changelog.md` without inventing versions.

## 敏感问题 / Sensitive concerns

不要公开粘贴密钥或私人材料。敏感问题使用 Security 页的私密漏洞报告入口（如已启用）；没有入口时，只发不含敏感细节的联系请求，取得私密渠道后再提供详情。真实密钥暴露后先撤销或轮换。

Do not post credentials or private material publicly. Use private vulnerability reporting on the Security page if enabled. Otherwise, post a contact request without sensitive details and obtain a private channel before sharing them. Revoke or rotate exposed credentials first.

本仓库只有指令与文档；材料仍由你选择的 AI 工具处理，其权限和数据政策由相应产品决定。Skill 不是权限隔离或安全保证。

This repository contains instructions and documentation. Your chosen AI tool processes your material under its own permissions and data policies. A Skill is not a permissions sandbox or safety guarantee.

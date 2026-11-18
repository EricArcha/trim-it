# Trim It

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](LICENSE)
[![Codex Skill](https://img.shields.io/badge/Codex-Skill-111111?style=flat-square)](https://learn.chatgpt.com/docs/build-skills)
[![Review only](https://img.shields.io/badge/Mode-review%20only-7c3aed?style=flat-square)](SKILL.md)
[![Bloat: on a diet](https://img.shields.io/badge/Bloat-on%20a%20diet-f97316?style=flat-square)](SKILL.md)

**让 AI 检查开发计划、代码实现和 AI 工作流，找出可以少做的工作。**

[English](readme.en.md) · 作者：[Eric / EricArcha](https://github.com/EricArcha)

让 AI 帮你做项目时，它可能不断加功能、加步骤、要求你确认。把开发计划、已有实现或 AI 工作流交给 Trim It，它会围绕你要交付的结果，检查哪些工作可以删除、合并或推迟，并说明依据。

它是一份给 AI 使用的工作指南（Skill）。你主动调用时才使用；默认只提建议，不改你的文件。

## 第一次使用

准备：你已经可以使用 Codex。**不用写代码，也不用先看懂仓库里的文件。**

1. 在 Codex 新建一个聊天，粘贴这句话：

   ```text
   $skill-installer 请从 https://github.com/EricArcha/trim-it 安装 trim-it。Skill 位于仓库根目录，安装名称用 trim-it。
   ```

2. 安装完成后，在聊天中输入 `$trim-it`。如果没有出现对应 Skill，重启 Codex 再试。
3. 粘贴下面的练习，或换成你自己的开发计划。明确写出你要保住的结果。

安装需要联网，Codex 可能请求相应权限。它是本地 Skill 的安装方式；其他 AI 工具的安装方式取决于各自是否支持 Skill。安装与调用说明参考 [OpenAI 官方指南](https://learn.chatgpt.com/docs/build-skills)。

## 复制这段，感受一次变化

```text
$trim-it

请审查下面的开发计划，只给建议，不修改文件。

本次练习已确认的目标基准如下，与当前项目无关：
## Goals
G-1：做一个给自己用的本地待办清单工具。
N-1：不做账号、团队协作或云端同步。
A-1：能添加和勾选任务，关闭再打开后任务仍在；有一份启动说明。

计划：
1. 实现添加任务、勾选完成和本地保存。
2. 在 README 写启动说明。
3. 把完全相同的启动说明再复制到另一份文档，之后两份分别维护。没有其他文件链接到第二份说明。
4. 增加登录页面和团队权限管理。

请指出有依据的精简建议，以及需要我决定的偏离目标事项。
```

你应当看到的变化方向（示意，**不是实测输出**）：

> **取消第二份启动说明**：README 已提供同样的内容，分别维护两份会增加更新负担。根据给定计划推断，保留 README 就能满足启动说明要求；前提是第二份没有额外内容或引用依赖。
>
> **请决定是否保留登录和团队权限**：它们服务于“不做”的账号和团队协作，偏离本次目标。先由你决定，不自动删除。

真正有用的变化是：你能看懂**少做什么、为什么、什么条件下成立**。Trim It 不承诺每次都能找出可删项；证据不足时，会说明无法安全建议。

## 什么时候用

| 你正在做的事 | 可以这样问 |
| --- | --- |
| AI 给出的开发计划越来越长 | `$trim-it 保住交付结果，检查这份开发计划里哪些步骤可以省掉。` |
| AI 工作流总在反复提问 | `$trim-it 看看哪些确认可以减少，哪些必须由我决定。` |
| 功能越加越多 | `$trim-it 对照项目目标，找出没有服务目标的内容。` |

附上要审查的材料和目标。材料涉及客户或个人信息时，先去掉不必要的敏感内容。

## 使用时会发生什么

- **先弄清要保住什么。** 如果项目没有明确目标，可能请你确认一份根据已有项目记录整理的目标草稿；没有记录时，会问一个必要问题。
- **建议要有依据。** 能说明删去后仍保住结果，才建议改变。涉及安全、不可逆后果或重要质量的内容，需要实际前后对比证据。
- **报告保持紧凑。** 最多列出 3 条精简建议、5 条目标偏离事项；偏离事项更多时会说明总数。建议不会自动执行，扩大检查范围前会征求同意。

它适合做一次聚焦的必要性检查。全面代码审计、性能测试和自动重构需要另行安排。效果取决于所用 AI、提供的材料和证据。

## 更新与反馈

更新已安装的副本：请 Codex “从原仓库更新 trim-it，保留我自己的改动；遇到冲突先告诉我”。只更新仓库不会自动更新另一处已安装的副本。

使用问题或改进建议，请到 [GitHub Issues](https://github.com/EricArcha/trim-it/issues) 描述你想保住的结果、输入和实际回答。示例请先脱敏；安全问题请看 [敏感问题说明](contributing.md)。

[变更记录](changelog.md) · [参与贡献](contributing.md)

© 2026 Eric / EricArcha · [MIT 许可证](LICENSE)。可修改、分享和商用，须保留版权和许可声明。

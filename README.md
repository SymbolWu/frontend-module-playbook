# Frontend Module Playbook

一套面向 React / TypeScript 页面模块的可迁移协作规范，已按 Agent Skill 形式组织，可用于模块设计、实现、评审、注释、文档整理和联调排查。

安装方式：把 `skills/frontend-module-playbook/` 复制到目标仓库的兼容 skill 目录中，或在公开仓库场景下按你的 skills 工具链使用仓库源地址安装。

仓库地址：`git@github.com:SymbolWu/frontend-module-playbook.git`

它适合做两类事情：

- 作为公开 skill 仓库发布和分发
- 作为规则母本复制到存量项目或新项目模板中

## 这个 skill 解决什么问题

当前很多前端项目并不缺“能写代码”的 AI，而是缺“知道该把逻辑放哪、怎么改才不越层、怎么评审才真正看风险”的稳定规则。

这个 skill 的目标不是替代业务设计，而是收敛页面级模块协作中的共性问题：

- 页面组件、view-model、transformer、service、repository 之间的职责边界
- AI 或开发者实际改代码时的落点选择和最小改动原则
- 注释、评审、提交、文档整理的统一工作方式
- 前后端联调时更稳定的排查顺序

## 适用场景

- React / TypeScript 页面模块
- 以页面目录为单位组织代码的前端项目
- 存在 ViewModel / transformer / service / repository 分层需求的项目
- 需要 AI 长期参与开发、评审和文档整理的团队

## 不适用的内容

这个仓库不提供：

- 某个具体业务模块的产品规则
- 项目专属路由入口或导航挂载方式
- 特定后端接口字段和状态枚举
- 某个仓库独有的环境变量和部署策略

如果某条规则必须依赖项目事实，就不应该继续沉淀在这个仓库里。

## 快速开始

### 1. 直接查看主 skill

- `skills/frontend-module-playbook/SKILL.md`

### 2. 查看规则正文

- `skills/frontend-module-playbook/references/module-architecture.md`
- `skills/frontend-module-playbook/references/implementation-workflow.md`
- `skills/frontend-module-playbook/references/comment-workflow.md`
- `skills/frontend-module-playbook/references/review-workflow.md`
- `skills/frontend-module-playbook/references/commit-workflow.md`
- `skills/frontend-module-playbook/references/doc-workflow.md`
- `skills/frontend-module-playbook/references/integration-debug-workflow.md`

### 3. 把它接入目标项目

把 `skills/frontend-module-playbook/` 复制到目标仓库的任一兼容目录：

- `.github/skills/frontend-module-playbook/`
- `.agents/skills/frontend-module-playbook/`
- `.claude/skills/frontend-module-playbook/`

如果你主要使用 GitHub Copilot / VS Code，优先使用 `.github/skills/`。

更完整的接入说明见 `docs/import-template.md`。

## 安装提示

当前仓库可直接使用以下安装示例：

```bash
npx skills add https://github.com/SymbolWu/frontend-module-playbook --skill frontend-module-playbook
```

如果暂时不走 CLI 安装，直接复制 `skills/frontend-module-playbook/` 目录仍然是最稳妥的接入方式。

## 可以怎么用

这个 skill 适合以下类型的请求：

- 为一个新的页面级模块设计目录结构和职责边界
- 判断某段逻辑应该落在组件、view-model、transformer 还是 service
- 评审一个模块改动是否存在流程回归、状态来源冲突或降级路径缺失
- 给存量页面补注释、实现说明或技术确认清单
- 排查“上传成功但任务不推进”“结果页打不开”这类联调链路问题

典型调用示例：

- `/frontend-module-playbook 为一个新的报表页设计模块目录和职责边界`
- `/frontend-module-playbook 这个页面的导出逻辑应该落在组件还是 view-model`
- `/frontend-module-playbook review 这个 React 模块改动有没有流程回归风险`
- `/frontend-module-playbook 排查上传成功但任务状态不推进的链路`

## 仓库结构

```text
frontend-module-playbook/
	AGENTS.md
	README.md
	CHANGELOG.md
	docs/
		skill-distribution.md
		release-checklist.md
		import-template.md
	skills/
		frontend-module-playbook/
			SKILL.md
			references/
```

职责划分：

- `skills/frontend-module-playbook/` 是 skill 本体
- `skills/frontend-module-playbook/references/` 是规则正文唯一来源
- `docs/` 只保留仓库级说明，不重复保存规则正文

## 入口说明

- 面向 AI 或协作者的入口索引见 `AGENTS.md`
- 规则正文统一放在 `skills/frontend-module-playbook/references/`
- 分发方案见 `docs/skill-distribution.md`
- 发布前检查见 `docs/release-checklist.md`
- 仓库提交规范见 `docs/commit-workflow.md`
- release 模板见 `docs/release-template.md`
- 项目接入模板见 `docs/import-template.md`
- 版本演进见 `CHANGELOG.md`

## 发布建议

如果你准备把它作为公开 skill 仓库发布，建议按这个顺序推进：

1. 先复制到 1 到 2 个真实项目中验证复用效果。
2. 再整理 README、CHANGELOG 和引入模板。
3. 再公开到 GitHub，并视需要提交到 skills 聚合目录。

## 版本

当前版本：`0.1.0`

首个版本说明见 `CHANGELOG.md`。
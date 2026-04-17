# Frontend Module Playbook

这个项目沉淀一套可迁移的前端模块协作规范，重点覆盖以下主题：

- 页面级模块如何分层与拆分
- AI 参与编码时的实现流程
- 注释、评审、提交、文档整理的统一规则
- 前后端联调时的通用排查顺序

这些内容提炼自一个真实 React 业务模块的长期协作经验，但这里保留的都是可迁移规则，不包含具体业务、路由入口、产品约束或项目私有流程。

## 目录

- `skills/frontend-module-playbook/SKILL.md`：skill 主入口
- `skills/frontend-module-playbook/references/*`：模块架构、实现、注释、评审、提交、文档、联调等规则正文
- `docs/skill-distribution.md`：skill 化与分发方案
- `docs/release-checklist.md`：公开发布前检查清单
- `docs/import-template.md`：向存量项目或新项目引入时的模板说明

## 适用范围

这套规范更适合以下场景：

- React / TypeScript 页面模块
- 以页面目录为单位组织代码的前端项目
- 存在 ViewModel / transformer / service / repository 分层需求的项目
- 需要 AI 长期参与开发、评审和文档整理的团队

## 不包含的内容

- 某个具体业务模块的产品规则
- 项目专属路由入口或导航挂载方式
- 特定后端接口字段和状态枚举
- 某个仓库独有的环境变量和部署策略

## 入口说明

- 面向 AI 或协作者的入口索引见 `AGENTS.md`。
- 规则正文统一放在 `skills/frontend-module-playbook/references/`。
- `docs/` 只保留仓库级说明，例如分发、发布和引入模板。

## Skill 形式

本仓库现在采用公开发布更常见的技能库结构：

- `skills/frontend-module-playbook/SKILL.md`
- `skills/frontend-module-playbook/references/*`

这意味着仓库本身更适合作为一个可分发 skill 源：

- 可按 `skills.sh` 生态常见方式组织
- 适合后续扩展为多 skill 仓库
- 适合在目标项目中按需复制到 `.github/skills/` 或其他 agent 兼容目录

详细方案见 `docs/skill-distribution.md`，发布前检查见 `docs/release-checklist.md`，接入模板见 `docs/import-template.md`。
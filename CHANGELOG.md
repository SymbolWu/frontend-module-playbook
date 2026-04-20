# Changelog

All notable changes to this repository will be documented in this file.

## 0.2.0 - 2026-04-20

统一当前 Skill 的正式定位，并补充近期已落地的规则增强内容。

### Changed

- 将对外定位统一收敛为“架构、实现、评审、注释、提交、文档整理与代码组织约束”
- 更新 README、SKILL、引入模板与发布清单中的能力描述，移除旧的团队化问题排查口径
- 补充更通用的模块架构、目录设计、模块化与单一职责原则
- 补充实现层的命名规则、复用搜索顺序与长文件治理约束
- 补充纯逻辑文件的 region 使用原则与相关注释规范
- 明确采用 MIT License，并同步仓库首页与 Skill 元数据中的许可说明

### Removed

- 删除团队定制化的问题排查工作流及其正式入口引用

## 0.1.1 - 2026-04-17

补充公开仓库真实地址与安装示例的最小修正版。

### Changed

- 在 README 中补充真实 GitHub 仓库地址
- 在 README 中补充可直接使用的安装命令示例

## 0.1.0 - 2026-04-17

首个公开整理版本。

### Added

- 建立 `skills/frontend-module-playbook/` 作为主 skill 目录
- 新增 `SKILL.md` 作为 skill 入口
- 新增 `references/` 作为规则正文唯一来源
- 新增模块架构、实现、注释、评审、提交、文档整理等参考文档
- 新增 `docs/skill-distribution.md` 说明 skill 化与分发方案
- 新增 `docs/release-checklist.md` 作为公开发布前检查清单
- 新增 `docs/import-template.md` 作为目标项目接入模板

### Changed

- 将仓库定位从“规则文档集合”收敛为“公开 skill 源仓库”
- 将 README 改为面向公开分发和接入的仓库首页
- 将规则正文统一迁移到 `skills/frontend-module-playbook/references/`

### Removed

- 删除重复的 `docs/*workflow.md` 文档副本
- 删除旧的 `.github/skills` 内嵌结构，避免双份维护
# Changelog

All notable changes to this repository will be documented in this file.

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
- 新增模块架构、实现、注释、评审、提交、文档整理、联调排查等参考文档
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
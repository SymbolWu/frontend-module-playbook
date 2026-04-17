# 引入模板

## 目标

给目标项目一份最小接入模板，让这个 skill 能被快速复制进存量项目或新项目模板中。

## 存量项目引入

把当前仓库中的 `skills/frontend-module-playbook/` 复制到目标仓库的对应目录中。常见目标位置：

- `.github/skills/frontend-module-playbook/`
- `.agents/skills/frontend-module-playbook/`
- `.claude/skills/frontend-module-playbook/`

推荐优先使用 `.github/skills/`，因为 GitHub Copilot 和 VS Code 相关工具链更常见。

## 存量项目接入说明模板

可直接放进目标仓库 README、AGENTS 或协作文档：

```md
## Frontend Module Skill

This repository uses the `frontend-module-playbook` skill for page-level frontend module work.

Skill location:

- `.github/skills/frontend-module-playbook/`

Use it when you need to:

- design or refactor a page module
- decide where logic belongs across component, view-model, transformer, service, and repository
- review module changes for behavior risk
- organize comment, documentation, commit, or integration-debug work

Start from:

- `.github/skills/frontend-module-playbook/SKILL.md`
```

## 新项目模板引入

如果你维护 starter repo、template repo 或脚手架，建议直接把 skill 目录预置进去：

1. 在模板仓库中加入 `.github/skills/frontend-module-playbook/`
2. 在模板 README 中补一段“本项目使用 frontend-module-playbook 作为模块协作规范”
3. 如果模板还需要 always-on 规则，再由模板仓库自己补 instruction 文件

## 复制后的最小检查

- 目录名是否仍为 `frontend-module-playbook`
- `SKILL.md` 的 `name` 是否仍匹配目录名
- `references/` 是否完整复制
- 目标仓库文档里是否已经指向新的 skill 路径

## 不建议的做法

- 只复制 `SKILL.md`，不复制 `references/`
- 在多个目录里放多份同名 skill，导致来源不清
- 复制后继续保留旧路径说明，造成入口混乱
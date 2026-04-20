# 引入模板

## 目标

给目标项目一份最小接入模板，让这个 skill 能被快速复制进存量项目或新项目模板中。

## 存量项目引入

推荐优先使用 `skills` CLI 做接入，再把手动复制作为 fallback。

先做一个通用检查：

```bash
npx -y skills add SymbolWu/frontend-module-playbook -l
```

如果一个项目可能同时被多个 agent 使用，推荐优先使用最通用的项目级安装方式，不指定 `--agent`：

```bash
npx -y skills add SymbolWu/frontend-module-playbook --skill frontend-module-playbook -y
```

如果你需要显式控制目标工具，再使用已验证的主流项目级安装示例：

```bash
# Claude Code
npx -y skills add SymbolWu/frontend-module-playbook --skill frontend-module-playbook --agent claude-code -y

# GitHub Copilot
npx -y skills add SymbolWu/frontend-module-playbook --skill frontend-module-playbook --agent github-copilot -y

# Cursor
npx -y skills add SymbolWu/frontend-module-playbook --skill frontend-module-playbook --agent cursor -y

# Codex
npx -y skills add SymbolWu/frontend-module-playbook --skill frontend-module-playbook --agent codex -y

# Windsurf
npx -y skills add SymbolWu/frontend-module-playbook --skill frontend-module-playbook --agent windsurf -y
```

如果不走 CLI，再把当前仓库中的 `skills/frontend-module-playbook/` 复制到目标仓库的对应目录中。常见目标位置：

- `.github/skills/frontend-module-playbook/`
- `.agents/skills/frontend-module-playbook/`
- `.claude/skills/frontend-module-playbook/`
- `.windsurf/skills/frontend-module-playbook/`

如果是手动复制，且主要面向 GitHub Copilot / VS Code，推荐优先使用 `.github/skills/`。

补充说明：

- `skills` CLI 的项目级安装目录由它自身的 agent target 决定。
- 不指定 `--agent` 时，CLI 会根据当前环境已检测到的 agent 做项目级安装；这通常是多 agent 项目的最通用方式。
- 如果需要一次指定多个 agent，可以在同一条命令里写多个值，例如 `--agent claude-code github-copilot cursor`。
- `claude-code` 通常落到 `.claude/skills/`。
- `github-copilot`、`cursor`、`codex` 这类 target 在 CLI 下会共用 `.agents/skills/` 一类项目目录。
- `windsurf` 使用自己的项目目录。
- 对多 agent 项目，优先让 `skills` CLI 统一管理，不建议手动复制多份 skill 目录。
- 手动复制时，仍然应优先遵循目标工具自己的兼容目录约定。

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
- organize comments, documentation, commit preparation, or code-organization work

Start from:

- `.github/skills/frontend-module-playbook/SKILL.md`
```

如果你主要通过 `skills` CLI 安装，也可以在目标项目文档里直接补一句：

```md
Install with:

`npx -y skills add SymbolWu/frontend-module-playbook --skill frontend-module-playbook --agent <your-agent> -y`
```

## 新项目模板引入

如果你维护 starter repo、template repo 或脚手架，建议直接把 skill 目录预置进去：

1. 在模板仓库中加入 `.github/skills/frontend-module-playbook/`
2. 在模板 README 中补一段“本项目使用 frontend-module-playbook 作为模块协作规范”
3. 如果模板还需要 always-on 规则，再由模板仓库自己补 instruction 文件

## 接入后需要确认的项目事实

把 skill 复制进目标仓库后，建议先确认以下事实，再决定哪些规则可以直接继承、哪些需要本地化适配：

- 路由入口和页面挂载方式
- 页面状态管理方式
- 请求层命名和目录习惯
- 样式方案与样式文件组织方式
- 项目级共享目录的命名，例如 `utils/`、`shared/`、`common/`
- 错误上报和异常兜底方式
- 当前项目的最小验证或测试基线

## 复制后的最小检查

- 目录名是否仍为 `frontend-module-playbook`
- `SKILL.md` 的 `name` 是否仍匹配目录名
- `references/` 是否完整复制
- 目标仓库文档里是否已经指向新的 skill 路径

## 不建议的做法

- 只复制 `SKILL.md`，不复制 `references/`
- 在多个目录里放多份同名 skill，导致来源不清
- 复制后继续保留旧路径说明，造成入口混乱
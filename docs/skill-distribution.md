# Skill 化与分发方案

## 目标

把 `frontend-module-playbook` 从“规则文档仓库”升级成“可被 AI 工具直接加载和复用的 skill 资产”，并且让它能在存量项目与新项目中方便引入。

## 当前仓库已经具备的基础

当前内容天然适合做 skill，原因是它本来就是一套可迁移规则，而不是绑定某个业务的实现代码：

- 有明确入口索引
- 有按任务类型拆分的规则文档
- 有明确使用边界
- 不依赖某个单独仓库的路由、环境变量或后端字段

这类内容比“单条超长 prompt”更适合封装为 skill。

## 当前采用的落地方式

本仓库现在采用“公开发布优先”的技能库结构：

- `skills/frontend-module-playbook/SKILL.md`
- `skills/frontend-module-playbook/references/*`

这是 skills 生态里更常见的组织方式。它把当前仓库定义成“skill 源仓库”，而不是“某个业务仓库里的内嵌 skill 目录”。

为了避免双份维护，规则正文只保留在 `references/` 中；`docs/` 目录只保留仓库级说明文档。

## 怎么在存量项目中引入

推荐先按使用目的决定安装方式：

- 如果只是个人本机使用，不希望目标仓库出现新的待提交文件，优先全局安装：`npx -y skills add https://github.com/SymbolWu/frontend-module-playbook -g --skill frontend-module-playbook -y`
- 如果希望把 skill 当作仓库内协作资产共享给团队，再使用项目级安装。

现在已经可以稳定识别并安装本仓库中的 skill。

先做一个通用检查：

```bash
npx -y skills add SymbolWu/frontend-module-playbook -l
```

如果一个项目会被多个 agent 共用，推荐优先使用最通用的项目级安装方式，不指定 `--agent`：

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

补充说明：

- `skills` CLI 的项目级安装目录取决于 agent target 本身。
- 如果你只是个人本机使用，优先 `-g`，这样不会改动目标仓库工作区。
- `VS Code` 只是编辑器宿主，不是 `skills` CLI 的 `--agent` 值；只有你实际使用的是 GitHub Copilot，才对应 `github-copilot`。
- 不指定 `--agent` 时，CLI 会根据当前环境已检测到的 agent 做项目级安装；这通常是多 agent 项目的最通用方式。
- 如果需要一次指定多个 agent，可以在同一条命令里写多个值，例如 `--agent claude-code github-copilot cursor`。
- `claude-code` 使用 `.claude/skills/`。
- `github-copilot`、`cursor`、`codex` 这类 target 在 CLI 下会共享 `.agents/skills/` 一类项目目录。
- `windsurf` 使用自己的项目目录。
- 项目级安装会直接改动目标仓库，常见会出现 `.agents/skills/`、`.claude/skills/`、`.windsurf/skills/` 或 `skills-lock.json` 等文件；因此 AI 在提交代码时把这些文件也纳入候选改动是正常现象。
- 如果这些文件就是团队要共享的 skill 资产，建议单独提交一次初始化接入；如果只是个人本机临时使用，就不要走项目级安装，或者在目标仓库里明确忽略这些文件。
- 因此，CLI 安装路径和手动复制时的推荐目录不一定完全一致。
- 对多 agent 项目，优先让 CLI 统一管理，而不是手动维护多份复制目录。

如果不走 CLI，再退回到“从本仓库复制 skill 目录到目标仓库”的方式，因为这仍然最直接、最少依赖：

1. 把 `skills/frontend-module-playbook/` 复制到目标仓库的 `.github/skills/` 目录下。
2. 视目标工具链，改成 `.agents/skills/` 或 `.claude/skills/` 也可以。
3. 根据目标仓库事实，微调 `SKILL.md` 和参考文档。

手动复制方式的优点：

- 对现有仓库侵入小
- 不依赖私有包管理
- 版本可跟随仓库一起审查和演进
- 适合先在少量项目试点

## 怎么在新项目中引入

推荐把这套 skill 直接放进你的前端项目模板或脚手架：

1. 在 starter repo 或 template repo 中预置 `.github/skills/frontend-module-playbook/`
2. 在新项目 README 或 AGENTS 文档里补一句“模块设计与实现优先参考该 skill”
3. 如果目标团队还需要 always-on 规则，再额外补该仓库自己的 instruction 文件

这样新项目从初始化开始就带有同一套协作约束。

## 有没有类似 SkillHub 的平台

有接近的分发渠道，但目前没有一个唯一通用、所有工具都统一使用的“官方 SkillHub”。更现实的渠道有三类：

### 1. Git 仓库直接分发

最稳妥。

- 公开 GitHub 仓库
- 通过 README 说明复制路径和使用方式
- 通过 release/tag 管理版本

适合当前阶段先验证内容质量和实际采用率。

### 2. 社区聚合分发

存在面向 Copilot 生态的聚合渠道，例如 Awesome Copilot 一类目录或市场入口。

它更像“发现入口”而不是统一标准仓库，但可以提高可见性。

### 3. Agent Plugin / 扩展化分发

这是更进一步的形态。

- skill 可以被打包进 agent plugin
- 用户通过编辑器内安装入口获取
- 适合以后做成更完整的“可安装能力包”

这条路线更像真正的平台化分发，但比纯 skill 目录要重。

## 推荐分阶段路线

### 阶段 1

先维护好当前仓库中的公开 skill 版本。

目标：

- 在你自己的 1 到 2 个存量项目试装
- 看 skill 描述是否能稳定被正确触发
- 看规则是否还需要再拆细

### 阶段 2

把它放进新项目模板或目标业务仓库。

目标：

- 验证新项目初始化是否顺手
- 观察团队成员是否真的会用 slash command 或自动加载能力

### 阶段 3

再考虑公开分发。

可选动作：

- 用 GitHub 仓库公开发布
- 提交到社区聚合目录
- 评估是否值得做成 agent plugin

## 现实判断

能做到，而且在没有历史包袱的前提下，更适合直接把这个仓库做成“公开 skill 源仓库”。

平台上传仍然是第二步，但现在第一步不再是内嵌到本仓库的 `.github/skills`，而是把根目录 `skills/` 结构收敛好，再复制到真实项目里验证复用效果。
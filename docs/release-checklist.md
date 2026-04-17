# 发布清单

## 目标

在把这个仓库公开发布到 GitHub、skills 生态目录或其他聚合渠道之前，确认 skill 本体、仓库说明和引入方式都已经收敛清楚。

## 发布前必查

### 1. Skill 结构

- 确认主 skill 位于 `skills/frontend-module-playbook/`
- 确认 `SKILL.md` 中的 `name` 与目录名一致
- 确认 skill 只保留一份正文来源，不存在多份重复规则文档
- 确认 `references/` 中的文件名、引用路径和 `SKILL.md` 中的链接一致

### 2. 仓库首页

- README 能在第一页说清这个 skill 是做什么的
- README 能说清适用场景和不适用范围
- README 能给出最小安装或复制方式
- README 能给出至少 2 到 3 个典型使用示例

### 3. 分发说明

- 确认 [docs/skill-distribution.md](./skill-distribution.md) 与当前目录结构一致
- 确认已有“如何接入存量项目”和“如何接入新项目”的说明
- 确认没有残留旧的 `.github/skills` 路线说明

### 4. 公开可读性

- skill 描述不要写成只对作者自己有意义的内部术语
- 示例要覆盖架构、实现、评审、联调这几类主要任务
- 文案中不要假设读者已经知道你的某个业务背景

### 5. 版本和演进

- 在 `metadata.version` 中维护一个明确版本
- 每次规则有明显变化时，补一条 release note 或 changelog
- 不把试验性规则直接当成稳定规范发布

### 6. 提交和发布规范

- 确认仓库提交信息遵循 `docs/commit-workflow.md`
- 确认首个 release 文案与 `docs/release-template.md` 保持一致或同方向
- 如果本次调整改变了旧结构或旧路径，确认提交类型是否应使用 `BREAKING:`

## 发布动作建议顺序

1. 先在你自己的 1 到 2 个项目中复制接入，验证能否稳定使用。
2. 再整理 README、分发说明和 release note。
3. 再公开到 GitHub，并视需要提交到 skills 聚合目录。

## 发布后检查

- 找一个全新项目，按 README 独立走一遍接入流程
- 找一个存量项目，验证复制到 `.github/skills/` 后是否能正常使用
- 检查是否还存在文档入口指向已删除路径
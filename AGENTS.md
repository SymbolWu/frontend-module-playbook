# AGENTS.md

本文件适用于 `frontend-module-playbook` 文档项目。

`README.md` 负责项目介绍；本文件只保留给 AI 或协作者使用的入口顺序与边界说明。

## 任务入口

- 如果你要设计一个新的页面级业务模块，优先看 `skills/frontend-module-playbook/references/module-architecture.md`。
- 如果你要开始实际改代码，优先看 `skills/frontend-module-playbook/references/implementation-workflow.md`。
- 如果你要补注释或统一注释风格，优先看 `skills/frontend-module-playbook/references/comment-workflow.md`。
- 如果你要做代码评审，优先看 `skills/frontend-module-playbook/references/review-workflow.md`。
- 如果你要整理提交，优先看 `skills/frontend-module-playbook/references/commit-workflow.md`。
- 如果你要整理实现说明、确认清单或接口文档，优先看 `skills/frontend-module-playbook/references/doc-workflow.md`。

## 使用边界

- 这里保留的是可迁移规则，不包含具体业务产品规则。
- 不包含某个仓库专属的路由入口、部署方式、环境变量或后端字段约束。
- 如果某条规则必须依赖具体项目事实，应该放回对应项目文档，不应写进本项目。

## 使用原则

- 优先把这里当成“规则母本”，再按目标项目做适配，而不是原样硬拷贝到所有仓库。
- 新增规则文档时，优先判断它属于模块架构、实现流程、注释、评审、提交或文档整理中的哪一类，并放入 `skills/frontend-module-playbook/references/`。
- `AGENTS.md` 只保留入口说明，不重复展开各份文档细则。
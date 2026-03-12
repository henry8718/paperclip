# Doc 目录总结与使用指南

本文档用于快速理解 `doc/` 目录中各文档的定位，并给出按目标场景的阅读与使用方式。

## 1. 一句话总览

`doc/` 目录覆盖了 Paperclip 的产品目标、V1 实现规范、开发部署、数据库、发布流程、插件能力、专题方案和实验记录。

---

## 2. 文档地图（按用途分组）

### A. 产品与规范（先看）

| 文档 | 用途 | 何时看 |
|---|---|---|
| `GOAL.md` | 产品愿景与长期目标（为什么做） | 刚接触项目时 |
| `PRODUCT.md` | 产品定义、核心概念、用户流程（做什么） | 理解业务模型时 |
| `SPEC-implementation.md` | V1 落地合同（必须实现什么） | 做功能、评审方案前 |
| `SPEC.md` | 长周期规格与远期方向 | 规划中长期能力时 |
| `TASKS.md` | 任务模型定义与结构语义 | 涉及任务系统设计时 |
| `TASKS-mcp.md` | 面向 MCP 场景的任务说明 | 做 MCP 相关集成时 |

### B. 开发与运行（高频）

| 文档 | 用途 | 何时看 |
|---|---|---|
| `DEVELOPING.md` | 本地开发、工作树、备份、密钥配置 | 日常开发 |
| `DATABASE.md` | DB 运行模式（嵌入式/Docker/托管）与迁移 | 数据库相关改动 |
| `DEPLOYMENT-MODES.md` | `local_trusted` / `authenticated` 模式定义 | 鉴权与部署策略设计时 |
| `DOCKER.md` | 容器部署与本地容器化运行 | Docker 部署或排障 |
| `CLI.md` | `paperclipai` CLI 用法 | 通过命令行管理实例时 |
| `OPENCLAW_ONBOARDING.md` | OpenClaw 接入引导 | 接入 OpenClaw 时 |

### C. 发布与运维流程

| 文档 | 用途 | 何时看 |
|---|---|---|
| `RELEASING.md` | 发布流程与检查项 | 发版前 |
| `PUBLISHING.md` | 包发布策略/执行说明 | 发布 npm 相关产物时 |

### D. 扩展与架构专题

| 文档 | 用途 | 何时看 |
|---|---|---|
| `plugins/PLUGIN_SPEC.md` | 插件规范草案/约束 | 设计插件系统时 |
| `plugins/ideas-from-opencode.md` | 插件与扩展思路沉淀 | 方案调研时 |
| `spec/agent-runs.md` | Agent Run 细化规范 | Run 编排改动时 |
| `spec/agents-runtime.md` | Agent Runtime 能力定义 | 运行时能力迭代时 |
| `spec/ui.md` | UI 规范与交互约束 | UI/UX 设计时 |

### E. 方案与实验记录（参考）

| 目录/文档 | 用途 |
|---|---|
| `plan/`、`plans/` | 各类实施计划（权限、认证、工作区、存储等） |
| `experimental/` | 实验性方案，通常不是稳定承诺 |
| `README-draft.md` | README 草稿版本，可用于文案参考 |
| `CLIPHUB.md` | ClipHub 方向说明 |

---

## 3. 推荐阅读路径（按角色）

### 3.1 新加入开发者（半天入门）

1. `GOAL.md`
2. `PRODUCT.md`
3. `SPEC-implementation.md`
4. `DEVELOPING.md`
5. `DATABASE.md`

> 这条路径可快速建立：愿景 → 业务对象 → V1约束 → 本地运行 → 数据模型运行方式。

### 3.2 后端/数据开发

- 必看：`SPEC-implementation.md`、`DATABASE.md`、`DEVELOPING.md`
- 选看：`spec/agent-runs.md`、`plans/*` 中与你负责域相关的计划

### 3.3 前端开发

- 必看：`SPEC-implementation.md`（UI requirements 章节）、`spec/ui.md`、`DEVELOPING.md`
- 选看：`PRODUCT.md`（用户流）、`TASKS.md`（任务展示语义）

### 3.4 运维/部署

- 必看：`DEPLOYMENT-MODES.md`、`DOCKER.md`、`DATABASE.md`、`CLI.md`
- 发版时补看：`RELEASING.md`、`PUBLISHING.md`

---

## 4. 如何使用这份文档索引（实操建议）

### 用法 1：按问题检索

先明确你要解决的问题，再按分组定位：

- “我该做什么功能？”→ 产品与规范组
- “本地启动报错/数据库如何配？”→ 开发与运行组
- “要上线/打包发布？”→ 发布与运维组
- “要做插件/新能力设计？”→ 扩展与架构专题

### 用法 2：提案前对齐

写方案前至少引用：

- `SPEC-implementation.md` 的相关约束
- 若涉及部署/鉴权，补充 `DEPLOYMENT-MODES.md`
- 若涉及存储与迁移，补充 `DATABASE.md`

### 用法 3：代码改动前检查

建议在 PR 前自查：

- 是否符合 V1 合同（`SPEC-implementation.md`）
- 是否与开发命令/运行方式一致（`DEVELOPING.md`）
- 若改数据模型，是否同步数据库流程说明（`DATABASE.md`）

---

## 5. 维护建议

- 新增设计文档时，优先放到 `doc/plans/`（可追踪实施计划）或 `doc/spec/`（能力规范）。
- 若文档会影响团队开发行为，请在 `DEVELOPING.md` 或 `SPEC-implementation.md` 增加引用入口。
- 每次大功能合并后，更新本文件中的“文档地图”，保持新成员可快速导航。

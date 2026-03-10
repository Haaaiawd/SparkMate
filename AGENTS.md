# AGENTS.md - AI 协作协议

> **"如果你正在阅读此文档，你就是那个智能体 (The Intelligence)。"**
> 
> 这个文件是你的**锚点 (Anchor)**。它定义了项目的法则、领地的地图，以及记忆协议。
> 当你唤醒（开始新会话）时，**请首先阅读此文件**。

---

## 🧠 30秒恢复协议 (Quick Recovery)

**当你开始新会话或感到"迷失"时，立即执行**:

1. **读取 .agent/rules/agents.md** → 获取项目地图
2. **查看下方"当前状态"** → 找到最新架构版本
3. **读取 `genesis/v{N}/05_TASKS.md`** → 了解当前待办
4. **开始工作**

---

## 🗺️ 地图 (领地感知)

以下是这个项目的组织方式：

| 路径 | 描述 | 访问协议 |
|------|------|----------|
| `src/` | **实现层**。实际的代码库。 | 通过 Task 读/写。 |
| `genesis/` | **设计演进史**。版本化架构状态 (v1, v2...)。 | **只读**(旧版) / **写一次**(新版)。 |
| `genesis/v{N}/` | **当前真理**。最新的架构定义。 | 永远寻找最大的 `v{N}`。 |
| `.agent/workflows/` | **工作流**。`/genesis`, `/blueprint` 等。 | 通过 `view_file` 阅读。 |
| `.agent/skills/` | **技能库**。原子能力。 | 通过 `view_file` 调用。 |

---

## 📍 当前状态 (由 Workflow 自动更新)

> **注意**: 此部分由 `/genesis`、`/blueprint` 和 `/forge` 自动维护。

- **最新架构版本**: `genesis/v1`
- **活动任务清单**: `尚未生成`（等待 /blueprint）
- **待办任务数**: -
- **最近一次更新**: `2026-03-09`

### 🌊 Wave 1 — 待 /blueprint 设置
_Genesis v1 已完成，等待执行 `/blueprint` 生成 05_TASKS.md_

---

## 🌳 项目结构 (Project Tree)

> **注意**: 此部分由 `/genesis` 维护。

```text
SparkMate/
├── genesis/v1/                     # 当前架构文档（只读）
│   ├── 00_MANIFEST.md
│   ├── concept_model.json
│   ├── 01_PRD.md
│   ├── 02_ARCHITECTURE_OVERVIEW.md
│   ├── 03_ADR/
│   │   ├── ADR_001_TECH_STACK.md
│   │   └── ADR_002_RESEARCH_DESIGN.md
│   ├── 04_SYSTEM_DESIGN/           # 待 /design-system 填充
│   ├── 05_TASKS.md                 # 待 /blueprint 生成
│   └── 06_CHANGELOG.md
│
├── src/
│   ├── miniprogram/                # 微信小程序前端
│   ├── cloudfunctions/             # 云函数层（后端）
│   └── admin/                      # 研究管理后台（Next.js）
│
├── AGENTS.md                       # AI 协作协议（本文件）
└── idea.md                         # 原始想法文档（存档）
```

---

## 🧭 导航指南 (Navigation Guide)

> **注意**: 此部分由 `/genesis` 维护。

- **架构总览**: `genesis/v1/02_ARCHITECTURE_OVERVIEW.md`
- **PRD**: `genesis/v1/01_PRD.md`
- **ADR**: 架构决策见 `genesis/v1/03_ADR/`
- **miniprogram-system**: 源码 `src/miniprogram/` → 设计 `genesis/v1/04_SYSTEM_DESIGN/miniprogram-system.md`
- **cloudfunction-system**: 源码 `src/cloudfunctions/` → 设计 `genesis/v1/04_SYSTEM_DESIGN/cloudfunction-system.md`
- **admin-system**: 源码 `src/admin/` → 设计 `genesis/v1/04_SYSTEM_DESIGN/admin-system.md`
- **详细设计**: 待 `/design-system` 执行后更新（填充 `genesis/v1/04_SYSTEM_DESIGN/`）
- **任务清单**: 待 `/blueprint` 执行后更新（生成 `genesis/v1/05_TASKS.md`）

---

## 🛠️ 工作流注册表

| 工作流 | 触发时机 | 产出 |
|--------|---------|------|
| `/quickstart` | 新用户入口 / 不知道从哪开始 | 编排其他工作流 |
| `/genesis` | 新项目 / 重大重构 | PRD, Architecture, ADRs |
| `/scout` | 变更前 / 接手项目 | `genesis/v{N}/00_SCOUT_REPORT.md` |
| `/design-system` | genesis 后 | 04_SYSTEM_DESIGN/*.md |
| `/blueprint` | genesis 后 | 05_TASKS.md + agents.md 初始 Wave |
| `/change` | 微调已有任务 | 更新 TASKS + SYSTEM_DESIGN (仅修改) + CHANGELOG |
| `/explore` | 调研时 | 探索报告 |
| `/challenge` | 决策前质疑 | 07_CHALLENGE_REPORT.md (含问题总览目录) |
| `/forge` | 编码执行 | 代码 + 更新 agents.md Wave 块 |
| `/craft` | 创建工作流/技能/提示词 | Workflow / Skill / Prompt 文档 |

---

## 📜 宪法 (The Constitution)

1. **版本即法律**: 不"修补"架构文档，只"演进"。变更必须创建新版本。
2. **显式上下文**: 决策写入 ADR，不留在"聊天记忆"里。
3. **交叉验证**: 编码前对照 `05_TASKS.md`。我在做计划好的事吗？
4. **美学**: 文档应该是美的。善用 Markdown 和 Emoji。

---
## 🔄 Auto-Updated Context

<!-- AUTO:BEGIN — 由工作流自动维护，请勿手动编辑此区块 -->

### 技术栈决策
- **小程序**: 微信原生小程序 + TypeScript（基础库 3.x）
- **动画**: lottie-miniprogram（微光崽核心动画）
- **后端**: 微信云开发 CloudBase，Node.js 18 云函数（无服务器）
- **数据库**: CloudBase 云数据库（MongoDB 兼容）
- **LLM**: [待人类确认] 候选 DeepSeek / 通义千问 / 文心一言
- **研究后台**: Next.js 15 + TailwindCSS + shadcn/ui + Recharts，部署到云托管

### 系统边界
- **miniprogram-system**: 微信小程序 UI 层，负责所有用户交互与动画渲染
- **cloudfunction-system**: 业务逻辑枢纽，包含 8 个云函数 + 3 个定时任务
- **database-system**: CloudBase 云数据库，7 个集合，研究数据持久化
- **admin-system**: 研究管理后台 Web，数据仪表盘 + CSV 导出

### 活跃 ADR
- **ADR-001: 技术栈选择** — 微信云开发 + 原生小程序 + DeepSeek API，低运维成本优先
- **ADR-002: 研究设计选择** — 纵向自然实验 + 剂量-效应分析，无外部对照组，伦理风险低

### 当前任务状态
- Genesis v1 已完成（2026-03-09）
- 等待执行 `/design-system` 填充 04_SYSTEM_DESIGN/
- 等待执行 `/blueprint` 生成 05_TASKS.md

<!-- AUTO:END -->

---
> **状态自检**: 准备好了？提醒用户运行 `/quickstart` 开始吧。

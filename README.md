# Incremental Delivery Skill · 增量交付技能

[中文](#cn) | [English](#en)

---

## <a name="cn"></a>中文

### 简介

Vibe Coding 迭代几轮之后，你自己也忘了上次改了什么，AI 更是每次从零开始。`incremental-delivery` 在编码前生成一份 `.incr/` 文档，记录任务清单和验收标准，让人和 AI 共享同一份事实源——既能追溯历史决策，也能在动手前对齐需求。

### 优点

- **人和 AI 共享上下文** — 每次任务形成独立文档，`[[wiki-link]]` 串联。新对话的 AI 沿链即可还原完整背景，不用重复解释
- **需求对齐前移** — 写代码前先明确功能点和验收标准。偏差在规划阶段就被发现，而非代码写完之后
- **AI 有据可依** — 文档中的约束和验收点让 AI 知道"项目不能怎么写"和"写到什么程度算通过"，减少自由发挥
- **验收不走形式** — 验收条件在真实运行系统中逐项校验，不靠代码审查勾 `[x]`

### 示例

以"新增导出功能"为例，`.incr/` 文档的大致框架：

```
# 数据导出功能

> 状态：进行中    日期：2026-07-16

## 需求

### 功能点
- [ ] F1：后端导出 API，支持 CSV / Excel 两种格式
- [ ] F2：前端列表页增加"导出"按钮，调用 API 下载文件

### 阶段规划
阶段 1：后端 API（F1） — 2 个任务 / 1 个文件
阶段 2：前端按钮（F2） — 2 个任务 / 2 个文件

### 影响范围
直接改动：`api/export.py`、`views/ListPage.vue`

## 验收

### F1：后端导出 API
- [ ] GET /api/export?format=csv 返回 CSV 文件
- [ ] GET /api/export?format=xlsx 返回 Excel 文件
- [ ] 数据量 > 10000 行时仍可在 30s 内完成

### F2：前端导出按钮
- [ ] 列表页出现"导出"按钮，点击弹出格式选择
- [ ] 下载文件内容与列表筛选结果一致

## 约束
- 导出走流式响应，不把全量数据加载到内存（偏差检测：现有列表接口已按此模式）
- API 命名遵循 `/api/xxx` 前缀（交叉对照：F1 → 由现有路由规则覆盖）
```

执行流程：**检查上下文 → 理解需求 → 提取约束 → 规划阶段 → [用户确认] → 逐阶段开发 → 逐项验收 → 归档**。

### 安装与使用

```bash
git clone git@github.com:BullHorse67/incremental-delivery-skill.git \
  ~/.claude/skills/incremental-delivery
```

在 Claude Code 中输入 `/incremental-delivery`。文档生成在项目 `.incr/` 目录，命名 `YYYY-MM-NNN-name.md`。

---

## <a name="en"></a>English

### Overview

After a few rounds of vibe coding, you can't remember what you changed — and AI starts every session from zero. `incremental-delivery` produces a `.incr/` document before coding begins, capturing task lists and acceptance criteria. Human and AI share a single source of truth: traceable decision history and aligned requirements, before a line of code is written.

### Benefits

- **Shared context for human and AI** — Each task gets its own document, chained via `[[wiki-link]]`. A fresh AI session follows the chain to reconstruct full context — no repeated explanations
- **Requirements aligned early** — Define feature points and acceptance criteria before coding. Misalignment is caught during planning, not after implementation
- **AI knows the guardrails** — Constraints and acceptance criteria tell AI "what not to do in this project" and "what done looks like," reducing improvisation
- **Verification that counts** — Acceptance criteria are validated in a running system. Code-review-only check-off doesn't qualify

### Example

For "add export feature", a `.incr/` document looks roughly like:

```
# Data Export Feature

> Status: In Progress    Date: 2026-07-16

## Requirements

### Feature Points
- [ ] F1: Backend export API, supporting CSV and Excel formats
- [ ] F2: Frontend "Export" button on the list page

### Phase Plan
Phase 1: Backend API (F1) — 2 tasks / 1 file
Phase 2: Frontend button (F2) — 2 tasks / 2 files

### Impact Scope
Direct: api/export.py, views/ListPage.vue

## Acceptance

### F1: Backend Export API
- [ ] GET /api/export?format=csv returns a CSV file
- [ ] GET /api/export?format=xlsx returns an Excel file
- [ ] >10,000 rows completes within 30s

### F2: Frontend Export Button
- [ ] "Export" button appears on list page with format selection
- [ ] Downloaded content matches the current list filter

## Constraints
- Use streaming response — never load full dataset into memory
  (deviation detection: existing list endpoints follow this pattern)
- API naming follows /api/xxx prefix
  (cross-reference: F1 → covered by existing route convention)
```

Execution flow: **Check Context → Understand Requirements → Extract Constraints → Plan Phases → [User Confirms] → Develop by Phase → Verify by Feature → Archive**.

### Install & Use

```bash
git clone git@github.com:BullHorse67/incremental-delivery-skill.git \
  ~/.claude/skills/incremental-delivery
```

Type `/incremental-delivery` in Claude Code. Documents land in `.incr/` at project root, named `YYYY-MM-NNN-name.md`.

---

MIT

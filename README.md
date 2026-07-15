# Incremental Delivery Skill

[中文说明](#chinese) | [English](#english)

---

## <a name="chinese"></a>增量交付技能

### 简介

为已有系统的小规模功能开发提供结构化交付流程。生成一份机器可执行、人类可阅读的开发文档，按阶段逐步推进。

### 核心规则

| 规则 | 说明 |
|------|------|
| **R1. MVP 先行** | 每次达成最小可验收标准，不引入不必要的抽象和配置 |
| **R2. 先读后写** | 动手前先读懂同类代码风格，CLAUDE.md 和 README 必读 |
| **R3. 阶段渐进** | 按任务列表逐步推进，每完成一个立即打勾 |
| **R4. 范围收敛** | 只验证本次新增，不做全系统回归 |
| **R5. 验收即执行** | 验收点必须在真实运行系统中校验，禁止仅靠代码审查通过 |

### 工作流程

```
步骤0：检查上下文 → 步骤1：理解需求 → 步骤2：提取关键约束
→ 步骤3：规划阶段 → [确认门] → 步骤4：逐阶段开发
→ 步骤5：逐功能点验收（真实系统） → 步骤6：汇总与归档
```

### 安装

```bash
# 克隆到 Claude Code skills 目录
git clone git@github.com:BullHorse67/incremental-delivery-skill.git \
  ~/.claude/skills/incremental-delivery
```

### 使用

在 Claude Code 对话中输入：

```
/incremental-delivery
```

或直接描述你的增量开发需求，AI 会自动调用此技能。

### 文档命名规范

```
YYYY-MM-NNN-name.md
```
- `YYYY-MM`: 年月
- `NNN`: 当月序号（001 开始）
- `name`: 英文 kebab-case 功能简称

---

## <a name="english"></a>English

### Overview

A structured delivery process for small-scale feature development on existing systems. Produces a machine-executable, human-readable development document, progressing phase by phase.

### Core Rules

| Rule | Description |
|------|-------------|
| **R1. MVP First** | Reach minimum acceptable standard each time; no unnecessary abstractions |
| **R2. Read Before Write** | Understand existing code patterns before writing; CLAUDE.md and README required |
| **R3. Phased Progression** | Follow task list sequentially; check off each completed task immediately |
| **R4. Scope Discipline** | Only verify what was added; declare impact scope explicitly |
| **R5. Verify by Execution** | Validate in running system (API, UI, logs); code review alone is FORBIDDEN |

### Workflow

```
Step 0: Check Context → Step 1: Understand Requirements → Step 2: Extract Constraints
→ Step 3: Plan Phases → [Confirmation Gate] → Step 4: Develop by Phase
→ Step 5: Verify by Feature (real system) → Step 6: Summary & Archive
```

### Installation

```bash
# Clone into Claude Code skills directory
git clone git@github.com:BullHorse67/incremental-delivery-skill.git \
  ~/.claude/skills/incremental-delivery
```

### Usage

In Claude Code, type:

```
/incremental-delivery
```

Or describe your incremental development needs — the AI will invoke this skill automatically.

### Document Naming Convention

```
YYYY-MM-NNN-name.md
```
- `YYYY-MM`: Year-Month
- `NNN`: Month-sequential number (starting at 001)
- `name`: English kebab-case feature abbreviation

---

## License

MIT

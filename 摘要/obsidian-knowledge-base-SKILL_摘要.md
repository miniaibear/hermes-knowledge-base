---
source: obsidian-knowledge-base SKILL.md
date: 2026-03-12
origin_file: 原料/obsidian-knowledge-base-SKILL.md
tags: [skill, knowledge-base, workflow]
---

# 摘要：obsidian-knowledge-base SKILL

## 一句话定位
Obsidian 知识库管理的标准操作流程，覆盖 ingest/query/lint 三种场景。

## 核心机制

**三层文件结构**
- 原料/：原始素材，不加工
- 摘要/：提炼后的脱水版
- 沉淀/：有价值的回答沉淀

**三条宪法级原则**
1. CLAUDE.md 是最高规则
2. log.md 只增不减
3. 原料→摘要→沉淀，单向流动，不走回头路

## Ingest 流程（新增素材）
用户丢原文 → AI 提炼摘要 → 更新 index.md → 记录到 log.md

## Query 流程（提问）
有价值的回答 → 自动存档到沉淀/ → 更新 index.md

## Lint 流程（健康检查）
用户触发 → AI 检查矛盾内容 → 标注问题

## 关键细节
- Vault 路径：`/root/hermes-knowledge-base/`
- index.md 每篇笔记只写一行 TLDR
- 所有行为以 CLAUDE.md 为准

---
source: obsidian-knowledge-base SKILL.md
date: 2026-03-12
tags: [skill, knowledge-base, workflow]
---

# Obsidian Knowledge Base SKILL.md

## Vault 路径
```
/root/hermes-knowledge-base/
```

## 文件结构
```
hermes-knowledge-base/
├── CLAUDE.md              ← 知识库宪法（控制 AI 行为的最高规则）
├── index.md               ← 全局目录，每篇笔记一行 TLDR
├── log.md                 ← 操作日志，只增不减
├── 原料/                   ← 原始素材，未加工
├── 摘要/                   ← 提炼后的摘要
└── 沉淀/                   ← 有价值的回答沉淀
```

## 工作流

### Ingest（新素材）
把原文丢给 AI → AI 提炼摘要 → 更新 index.md → 记录到 log.md

### Query（提问）
有价值的回答 → 自动存档到 沉淀/ → 更新 index.md

### Lint（健康检查）
用户说"做一次 lint" → AI 检查矛盾内容 → 标注问题

## 核心原则
1. CLAUDE.md 是最高规则，所有行为以此为准
2. log.md 只增不减，历史记录不删除
3. index.md 保持精简，每篇笔记一行 TLDR
4. 原料/ → 摘要/ → 沉淀/ 是单向流动，不走回头路

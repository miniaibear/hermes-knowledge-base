# log — 操作日志

> 只增不减。追踪每次 ingest/query/lint 的轨迹。

---

## 2026-04-11

## init — 知识库初始化

- 创建三层目录结构：原料/ / 摘要/ / 沉淀/
- 写入 CLAUDE.md（知识库宪法）
- 写入 index.md（全局目录）
- 写入 log.md（操作日志）

---

---

## 2026-04-11（续）

## ingest | 知识库架构设计原则

- 原始素材：[[原料/知识库架构设计原则.md]]
- 产出摘要：[[摘要/知识库架构设计原则_摘要.md]]
- 核心 takeaway：笔记库即代码仓库，原料只读，Claude 是编译器
- 已更新 index.md

---

---

## query | 知识库工作流示范

- 用户请求：示范如何用这套架构做知识管理
- 产出沉淀：[[沉淀/知识库工作流示范.md]]
- 核心产出：Ingest/Query/Lint 三动作的实际执行方式
- 已更新 index.md

---

---

## 2026-04-12

## query | skills 实用场景

- 用户问"skills 有什么用"
- 产出沉淀：[[沉淀/skills实用场景示范.md]]
- 核心产出：Skills 核心价值 = 工作流自动化 + 跨 session 记忆 + 上下文压缩；"沉淀=搜索的逆过程"
- 已更新 index.md

---

## ingest | obsidian-knowledge-base SKILL.md

- 原始素材：[[原料/obsidian-knowledge-base-SKILL.md]]
- 产出摘要：[[摘要/obsidian-knowledge-base-SKILL_摘要.md]]
- 核心 takeaway：ingest/query/lint 三流程，原料→摘要→沉淀单向流动
- 已更新 index.md

---

## ingest | Kelly Criterion Prediction Markets (arXiv 2412.14144v1)

- 原始素材：[[原料/kelly-criterion-prediction-markets-2412.14144v1.html]]
- 产出摘要：[[摘要/kelly-criterion-prediction-markets_摘要.md]]
- 核心 takeaway：预测市场价格≠概率，Kelly公式给出最优下注比例 f*=(Q-P)/(1+Q)；市场摩擦导致价格-概率系统性缺口
- 已更新 index.md

*日志规范：每条记录以 `## ingest | ## query | ## lint` 前缀开头*

## ingest 2026-03-12

- 用户口头记录今日交易复盘
- 存入 Journal/Trading/2026-03-12.md
- 更新 index.md 加入 Journal/Trading/ 分类

## ingest 2026-04-17

- 用户补充交易复盘细节（100倍行情版本）
- 核心变化：最高涨幅100倍（不是50倍），正常本级别盈利1万~2万刀（不是1000~2000刀）
- 新增内容：MEME币大肉行情执行铁律（五段式完整版）
- 存入 Journal/Trading/2026-04-17.md（覆盖原2026-03-12版本为同一标的的更完整记录）
- index.md 更新日期至 2026-04-17


## ingest | Kelly Criterion to Prediction Markets (详细版重写)

- 原始素材：[[原料/kelly-criterion-prediction-markets-2412.14144v1.html]]
- 产出摘要：[[摘要/kelly-criterion-prediction-markets_摘要.md]]
- 核心 takeaway：市场价格≠概率；Kelly f*=(Q-P)/(1+Q)；预测市场存在系统性缺口；α参数可调节 payout 缩小缺口；KL散度显示 bias 误估计是一阶效应，fraction 误计算是二阶效应
- index.md TLDR 更新至 2026-04-20


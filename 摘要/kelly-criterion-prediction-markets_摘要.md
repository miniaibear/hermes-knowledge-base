# Kelly Criterion 在预测市场的应用

**来源：** https://arxiv.org/abs/2412.14144 （arXiv:2412.14144v1 [q-fin.PM]）

**作者：** Bernhard K Meister，2024年12月18日

**核心 Takeaway（一句话）：**
预测市场的合约价格系统性地偏离真实概率——Kelly公式给出理性投资人的最优下注比例，但即便所有人都用Kelly策略，价格与信念之间仍存在不可避免的缺口；通过修改payout结构（引入参数α）可以缩小这一缺口。

---

## 一、背景：为什么价格 ≠ 概率？

预测市场（如 Polymarket hosted on Solana）与传统金融市场的一个关键区别：**价格有上下界 [0, 1]**，不像股票可以无限涨。

两个原因导致价格偏离概率：

1. **金融视角**：区分"真实概率"与"市场概率"——后者包含边际投资者的风险厌恶，由定价核（pricing kernel）调整
2. **博彩视角**：payout不对称——偏离50%的位置，一边回报大于另一边，产生杠杆效应，影响赔率

**现实例子**：美国大选期间 Polymarket 成交数十亿美元，但Manski（2004）、Wolfers & Zitzewitz（2004, 2006）等学者早就指出：预测市场的0-1合约价格并不等于事件真实概率。

---

## 二、核心模型：Kelly公式与最优下注比例

### 2.1 All-or-Nothing 合约

- 支付价格 p（0 < p < 1）买入1单位
- 事件发生 → 获得 $1，损失初始投入 p
- 事件不发生 → 损失 p，无任何回报

### 2.2 Kelly优化问题

投资者有主观信念 q（认为事件发生的概率），当前市场价格为 p，求最优下注比例 f。

**效用函数**（对数效用）：
$$U(q, p, f) = (1-q)\log(1-f) + q\log\left(1 + f\frac{1-p}{p}\right)$$

**一阶条件** → 最优Kelly fraction：
$$f^* = \frac{Q - P}{1 + Q}$$

其中：
- $P = \frac{p}{1-p}$（市场odds）
- $Q = \frac{q}{1-q}$（信念odds）

### 2.3 直观解读

| 情况 | f* | 含义 |
|------|-----|------|
| q = p | 0 | 信念=价格，公平市场，不下注 |
| q > p | > 0 | 认为赔率划算，做多 |
| q < p | < 0 | 认为赔率不合算，做空（需允许卖空） |

注意：论文假设**禁止借贷**（不能加杠杆做空），所以 f* 必须落在合理范围内。

---

## 三、关键结论：价格-信念缺口可以很大

### 3.1 双投资者toy model

假设市场只有两个投资者：
- 投资者A：资本 $1，确定相信某结果（q = 0 或 q = 1）
- 投资者B：资本 $C，信念为 q（中间值）

**市场出清条件**：两人总头寸为零，确定者提供流动性，让不确定者的头寸平衡。

**Case 1：确定者相信事件不发生（q⁻ = 0）**

$$C_{1-} = \frac{1-p}{q - p}$$

期望值：
$$E_-(q, p) = C_{1-} \cdot q + 1 = \frac{1-p \cdot (2-p) \cdot q}{1-p}$$

取值范围：
- p < 1/2：E ∈ [0, 1/2]
- p > 1/2：E ∈ [1/2, 1]
- p = 1/2：E = 1/2

**Case 2：确定者相信事件发生（q⁺ = 1）**

$$C_{1+} = \frac{1-p}{p - q_{1+}}$$

期望值：**E₊ = p**（恰好等于价格）

### 3.2 缺口能有多大？

极端例子：如果所有投资者信念只有 0% 或 100%，哪怕最小的资金不平衡也会把价格推到0或1，但期望值可以完全不动——仍接近50%。

**推论**：即便所有参与者都用Kelly策略且信息充分，价格和信念仍可能相差悬殊。这不是非理性，而是市场结构的必然结果。

---

## 四、改进方案：修改Payout结构（α参数）

### 4.1 修改后的效用函数

论文提出在payout中引入指数α：

$$U_\alpha(q, p, f) = (1-q)\log(1-f) + q\log\left(1 + f\left(\frac{p}{1-p}\right)^\alpha\right)$$

**最优解**：
$$f^*_\alpha = \frac{\hat{P}^\alpha - Q}{Q + 1}, \quad \hat{P}^\alpha = \left(\frac{p}{1-p}\right)^\alpha$$

### 4.2 α的含义

| α值 | 效果 |
|-----|------|
| α = 1 | 传统Kelly，结果 |
| 0 ≤ α < 1 | 平滑处理，**接近0或1边界时缩小缺口**，低赔率高概率赌注更有吸引力 → 增加流动性 |
| α > 1 | 边界处缺口**扩大**，行为与α < 1相反 |

**实用价值**：当市场价格接近0或1的边界时，选择合适的α可以吸引更多流动性。但如果市场反转，流动性也会快速流失。

---

## 五、双截断游戏（Double-or-Nothing）的有限时间分析

### 5.1 模型设定

N步biased random walk，事件上涨概率为 p。定义累积分布：

$$F(k, N, p) = \sum_{i=0}^{\lfloor k \rfloor} \binom{N}{i} p^i (1-p)^{N-i}$$

### 5.2 Chernoff界（大偏差理论）

利用Kullback-Leibler散度（相对熵）建立上下界：

$$F(k, N, p) \leq e^{-N \cdot D\left(\frac{k}{N} \| p\right)}$$

$$F(k, N, p) \geq \frac{1}{2\sqrt{N}} e^{-N \cdot D\left(\frac{k}{N} \| p\right)}$$

其中KL散度：
$$D(x \| p) = x\log\frac{x}{p} + (1-x)\log\frac{1-x}{1-p}$$

### 5.3 对增长率的影响

论文分析了两种**误估计**的影响：

**类型A：误估计bias（p偏差ε）**

$$D\left(\frac{k}{N} \| p+\epsilon\right) - D\left(\frac{k}{N} \| p\right) = \frac{p - k/N}{p(1-p)} \cdot \epsilon + O(\epsilon^2)$$

→ 偏差的影响是**一阶线性**的

**类型B：误计算fraction（f偏差ε）**

$$U(p, 2p-1+\epsilon) - U(p, 2p-1) = -\frac{1}{4p(1-p)} \cdot \epsilon^2 + O(\epsilon^3)$$

→ 误计算的影响是**二阶（平方）**的

**核心洞察**：对增长率的伤害，误估计bias比误计算fraction更严重——前者是一阶效应，后者是二阶效应。

---

## 六、论文结论

1. 信息理论（即便最简单形式）可以揭示预测市场的运作机制
2. 市场价格与投资者平均信念之间存在系统性缺口，且缺口规模可以非常大
3. 通过调整payout参数α，可以主动管理接近边界时的流动性和缺口大小
4. KL散度是分析有限时间下不同策略表现的有力工具

---

## 参考文献（论文自带）

- Kelly, J L (1956). "A New Interpretation of Information Rate." Bell System Technical Journal.
- Cover & Thomas (1991). "Elements of Information Theory." Wiley-Interscience.
- Manski (2004). "Interpreting the Predictions of Prediction Markets." NBER Working Paper.
- Wolfers & Zitzewitz (2004). "Prediction markets." Journal of Economic Perspectives.
- Wolfers & Zitzewitz (2006). "Interpreting prediction market prices as probabilities."
- Breiman (1961). "Optimal gambling systems for favorable games."
- Meister & Price (2024). "A Quantum Double-or-Nothing Game." Entropy 26(1).

---

**关联笔记：** [[../沉淀/知识库工作流示范]]

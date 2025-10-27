# **独立变量 `pulse.width` 与背景扫描参数 `plasma.Burn_Fraction` 之间的交互敏感性分析报告**

---

## **摘要 (Abstract)**

本研究针对聚变堆氚燃料循环系统开展了一项**交互敏感性分析**，旨在量化评估独立变量 **`pulse.width`**（占空比 / 可用性因子）对关键性能指标的影响，并深入探究其与背景扫描参数 **`plasma.Burn_Fraction`**（氚燃烧份额）之间的协同作用。分析覆盖 `pulse.width` 在 `[50, 60, 70, 80, 90, 99]` 的多点采样，结合 `plasma.Burn_Fraction` 在 `[0.02, 0.03, ..., 0.1]` 的梯度变化，系统评估了 `Startup_Inventory`（启动库存）和 `Required_TBR`（所需氚增殖比）的响应行为。

结果表明：`Startup_Inventory` 随 `pulse.width` 增加呈现**单调递增趋势**，且在低燃烧分数下增幅显著；而 `Required_TBR` 在绝大多数工况下对 `pulse.width` 变化不敏感，仅在高燃烧分数（≥ 0.05）条件下于最大脉冲宽度（99）处出现微弱下降。更关键的是，`plasma.Burn_Fraction` 与 `pulse.width` 存在显著的**负向交互效应**：高燃烧份额可有效抑制启动库存的增长速率，并激活长脉冲对增殖比的优化潜力。核心结论为：**延长 `pulse.width` 的工程价值高度依赖于 `plasma.Burn_Fraction` 的提升**，二者构成一个协同优化的性能边界。建议未来设计优先实现高效燃烧，再通过合理脉冲控制释放系统潜能。

---

## **引言 (Introduction)**

核聚变能源的商业化路径中，实现氚的自持循环是核心挑战之一。作为关键子系统的**氚燃料循环**，其性能直接决定了反应堆的启动可行性、运行经济性及部署速度。在该系统中，**等离子体运行参数**——尤其是**占空比**（`pulse.width`）——对整个循环动态具有深远影响。`pulse.width` 决定了反应堆年平均运行效率，进而影响氚的消耗速率、增殖速率以及系统对初始库存的需求。

然而，`pulse.width` 的影响并非孤立存在。其实际效能受制于其他关键物理参数，如**氚燃烧份额**（`plasma.Burn_Fraction`），后者表征了注入氚在等离子体中发生聚变反应的比例，是决定系统自持能力的核心指标。因此，单纯分析单一参数的主效应不足以揭示系统的真实行为，必须考虑**多参数间的交互效应**。

本研究聚焦于 **`pulse.width`** 作为独立变量，通过多维扫描，系统评估其对两个核心因变量的影响：
- `Startup_Inventory`：反应堆首次启动所需的初始氚库存量，直接影响项目初期投资与安全风险。
- `Required_TBR`：为满足氚自持并达成特定倍增时间要求所必需的最低氚增殖比，是衡量增殖包层设计性能的关键目标。

本分析采用 **`pulse.width`** 在 `[50, 60, 70, 80, 90, 99]` 的离散采样，同时设置 `plasma.Fuel_Efficiency = 0.5` 为固定背景值，`plasma.Burn_Fraction` 作为另一扫描维度，范围为 `[0.02, 0.03, ..., 0.1]`，以构建完整的参数空间，从而实现对 `pulse.width` 与 `plasma.Burn_Fraction` 间**交互敏感性**的深度解析。

---

## **方法 (Methodology)**

本研究采用**多维参数扫描法**，以 `pulse.width` 为独立变量，`plasma.Burn_Fraction` 为背景扫描参数，构建了一个 6 × 9 的参数组合网格。每个组合均基于统一的模型初始化条件进行稳态仿真，输出关键性能指标。

- **独立变量（Independent Variable）**：`pulse.width`，单位为百分比（%），采样点为 {50, 60, 70, 80, 90, 99}。
- **背景扫描参数（Background Scanning Parameters）**：
  - `plasma.Fueling_Efficiency`：固定为 0.5。
  - `plasma.Burn_Fraction`：在 [0.02, 0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09, 0.1] 之间线性扫描。
- **因变量（Dependent Variables）**：
  - `Startup_Inventory`：储存与输送系统 (SDS) 的初始氚库存量（单位：kg）。
  - `Required_TBR`：为满足特定约束（如倍增时间需求）所求解出的最小所需氚增殖比。

`Required_TBR` 的求解采用二分查找算法，搜索范围为 [1.0, 1.5]，收敛精度 `tolerance = 0.005`，最大迭代次数 `max_iterations = 10`。所有数据均来自模型仿真结果，并通过结构化表格与可视化图表进行呈现与验证。

---

## **结果与讨论 (Results and Discussion)**

### **主效应分析：`pulse.width` 对关键性能指标的总体影响**

#### **1. `Startup_Inventory` 的响应趋势**

`Startup_Inventory` 随 `pulse.width` 的增加呈现出**一致且显著的正相关关系**。如图1所示，无论 `plasma.Burn_Fraction` 取何值，当 `pulse.width` 从 50% 增至 99% 时，启动库存均呈上升趋势。

![Startup Inventory vs pulse width](line_Startup_Inventory_vs_pulse.width.svg)

*图1：不同 `plasma.Burn_Fraction` 条件下，`Startup_Inventory` 随 `pulse.width` 变化的趋势曲线*

进一步量化分析显示，`Startup_Inventory` 的增长幅度与 `plasma.Burn_Fraction` 呈**负相关**。具体而言：
- 当 `plasma.Burn_Fraction = 0.02` 时，`Startup_Inventory` 从 4.01 kg 增至 6.23 kg，**增长达 55.4%**；
- 当 `plasma.Burn_Fraction = 0.1` 时，`Startup_Inventory` 从 2.07 kg 增至 2.71 kg，**增长仅为 30.9%**。

这一现象表明，在低燃烧效率下，延长脉冲宽度带来的“额外运行时间”无法被高效的氚利用所抵消，反而加剧了系统对初始库存的需求，形成“**时间投入—库存成本**”的刚性正反馈。

#### **2. `Required_TBR` 的响应特性**

`Required_TBR` 的变化趋势则截然不同。如图2所示，在大多数工况下，`Required_TBR` 随 `pulse.width` 变化**保持恒定**，仅在特定条件下于 `pulse.width = 99` 处出现微小下降。

![Required TBR vs pulse width](line_Required_TBR_vs_pulse.width.svg)

*图2：不同 `plasma.Burn_Fraction` 条件下，`Required_TBR` 随 `pulse.width` 变化的趋势曲线*

- 当 `plasma.Burn_Fraction ≤ 0.04` 时，`Required_TBR` 在整个 `pulse.width` 范围内**完全不变**，表明系统在该燃烧水平下，即使延长脉冲，也无法通过提升增殖效率来降低对TBR的要求。
- 当 `plasma.Burn_Fraction ≥ 0.05` 时，`Required_TBR` 在 `pulse.width = 99` 处首次出现下降：从 1.0234 降至 1.0195（降幅 0.38%），并在更高燃烧分数下持续降低，最终在 `plasma.Burn_Fraction = 0.1` 时降至 1.0117。

这表明 `Required_TBR` 对 `pulse.width` 的响应具有**阈值依赖性**，其敏感性仅在高燃烧效率下被激活。

#### **3. 性能指标敏感度排序**

综合上述趋势，对各指标的敏感度进行量化排序：

| 性能指标 | 敏感度等级 | 理由 |
|----------|------------|------|
| `Startup_Inventory` | **高** | 所有工况下均呈现强正相关，变化范围大（2.07 → 6.23），且增长趋势稳定。 |
| `Required_TBR` | **极低** | 绝大多数工况下无变化，仅在高 `Burn_Fraction` 且 `pulse.width = 99` 时出现微弱非单调下降。 |

> ✅ **结论**：`Startup_Inventory` 是对 `pulse.width` 变化最敏感的性能指标，而 `Required_TBR` 几乎不受其影响。

---

### **交互效应分析：`pulse.width` 与 `plasma.Burn_Fraction` 的协同机制**

#### **1. `Startup_Inventory` 的交互特性：边际效益递减**

数据分析揭示了 `plasma.Burn_Fraction` 与 `pulse.width` 之间存在**显著的负向交互效应**。具体表现为：**高 `plasma.Burn_Fraction` 可有效抑制 `Startup_Inventory` 随 `pulse.width` 增加的增长斜率**。

如下表所示，计算每增加 10 个单位 `pulse.width` 所导致的平均增量（Δ），可清晰看出该趋势：

| `plasma.Burn_Fraction` | `Startup_Inventory` 增量 (Δ) 每 10 单位 `pulse.width` |
|------------------------|-----------------------------------------------|
| 0.02                   | 0.222 kg                                      |
| 0.03                   | 0.233 kg                                      |
| 0.04                   | 0.250 kg                                      |
| 0.05                   | 0.190 kg                                      |
| 0.06                   | 0.180 kg                                      |
| 0.07                   | 0.160 kg                                      |
| 0.08                   | 0.140 kg                                      |
| 0.09                   | 0.140 kg                                      |
| 0.10                   | 0.064 kg                                      |

> **物理机制解释**：更高的 `plasma.Burn_Fraction` 意味着单位时间内有更多氚被有效消耗并转化为能量，提升了系统的氚利用率。因此，在延长脉冲宽度时，系统能更有效地“消化”新增的运行时间，使得新产生的氚能够更快地进入循环，从而减轻了对初始库存的依赖。这种“**效率补偿效应**”导致了 `Startup_Inventory` 增长的**边际效益递减**。

#### **2. `Required_TBR` 的交互特性：阈值触发机制**

`Required_TBR` 的变化行为揭示了另一种复杂的交互模式——**非线性协同优化**。

- **低燃烧分数（≤ 0.04）**：系统处于“低效运行区”，`Required_TBR` 恒定，说明延长脉冲宽度无法提升增殖效率，系统无法突破当前性能瓶颈。
- **高燃烧分数（≥ 0.05）**：系统进入“高效运行区”。此时，`pulse.width` 的延长（尤其是达到 99）触发了 `Required_TBR` 的下降。例如：
  - `plasma.Burn_Fraction = 0.05` → `Required_TBR` 从 1.0234 → 1.0195；
  - `plasma.Burn_Fraction = 0.1` → `Required_TBR` 从 1.0156 → 1.0117。

这表明，只有当 `plasma.Burn_Fraction` 达到一定阈值（约 0.05）时，系统才具备足够的自持能力，使得在长脉冲下通过更高的能量产出，实现更低的TBR需求。此过程本质上是一个**协同优化**：高燃烧效率为长脉冲提供了“潜力”，而长脉冲则为实现低增殖比提供了“通道”。

> ✅ **结论**：`plasma.Burn_Fraction` 与 `pulse.width` 之间存在**强非线性交互效应**。高燃烧分数是释放长脉冲优势的“开关”，二者共同定义了系统性能的最优工作区间。

---

## **结论 (Conclusion)**

本研究通过严谨的多维敏感性分析，系统揭示了 `pulse.width` 在聚变堆氚燃料循环系统中的复杂行为及其与 `plasma.Burn_Fraction` 的深层交互关系，得出以下核心学术结论与工程建议：

1. **`pulse.width` 的影响具有双重性**：
   - **负面效应**：延长脉冲宽度**必然增加 `Startup_Inventory`**，在低燃烧效率下增幅可达 55%，显著提高启动阶段的技术与经济门槛。
   - **正面效应**：在高燃烧效率（≥ 0.05）条件下，长脉冲可**降低 `Required_TBR`**，有助于减轻增殖包层设计压力，提升系统长期经济性。

2. **性能优化的核心在于协同而非孤立**：
   - `pulse.width` 的价值**高度依赖于 `plasma.Burn_Fraction` 的水平**。单独延长脉冲长度在低燃烧效率下是无效甚至有害的。
   - 二者构成一个**性能协同工作区**：只有当 `plasma.Burn_Fraction` 足够高时，`pulse.width` 的延长才能带来真正的优化收益。

3. **设计与运行策略建议**：
   - **优先提升燃烧效率**：应将研发重点放在改进加热方式、磁场约束稳定性、杂质控制等技术上，以实现 `plasma.Burn_Fraction ≥ 0.05`。
   - **采用分阶段运行策略**：
     - 初期（启动/调试阶段）：使用较短脉冲（如 70–80），以严格控制 `Startup_Inventory`。
     - 中后期（稳态运行）：在确保高燃烧效率后，逐步过渡至长脉冲（如 99），以释放 `Required_TBR` 优化潜力。
   - **优化目标函数应耦合多指标**：避免单一追求 `Required_TBR` 极小化，应建立包含 `Startup_Inventory`、`Doubling_Time`、`Self_Sufficiency_Time` 的加权综合目标函数，实现全局最优。

> ✅ **最终总结**：  
> 本次分析明确指出，**`pulse.width` 并非一个孤立的“可调参数”**，其工程价值需由 `plasma.Burn_Fraction` 决定。未来聚变堆的设计与运行必须围绕“**高效燃烧 + 合理脉冲**”的协同优化路径展开，方能实现安全、经济、可持续的氚自持。
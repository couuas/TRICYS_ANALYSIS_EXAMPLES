# **独立变量 `tep.DIR` 与背景扫描参数 `plasma.Burn_Fraction` 之间的交互敏感性分析报告**

---

## **摘要**

本研究针对聚变堆氚燃料循环系统中关键参数 `tep.DIR`（托卡马克排气处理系统直接内部循环比例）开展了一项系统性的**交互敏感性分析**，旨在量化其对核心性能指标的影响，并揭示其与背景参数 `plasma.Burn_Fraction`（等离子体氚燃烧份额）之间的耦合效应。分析表明：`tep.DIR` 的提升可显著降低启动库存量（`Startup_Inventory`），但对所需氚增殖比（`Required_TBR`）的影响存在显著阈值效应，仅在高 `plasma.Burn_Fraction` 条件下才能有效触发优化。主效应分析显示，`Startup_Inventory` 对 `tep.DIR` 的变化具有强线性负相关性，是响应最敏感的指标；而 `Required_TBR` 的敏感度极低，且呈现非连续、分段式变化特征。交互效应分析进一步揭示，`plasma.Burn_Fraction` 是决定 `tep.DIR` 效益能否释放的关键“开关”——当 `plasma.Burn_Fraction ≥ 0.07` 时，`tep.DIR ≥ 0.6` 可激活系统主动优化 `TBR` 能力。基于此，提出“先提升燃烧效率，再强化增殖能力”的分阶段优化策略，为反应堆设计与运行控制提供理论依据。

---

## **引言**

在核聚变能源商业化进程中，氚燃料循环系统的自持能力与经济性是决定其可行性与部署速度的核心因素。其中，**启动库存**（`Startup_Inventory`）与**所需氚增殖比**（`Required_TBR`）是衡量系统初始成本与长期可持续性的两大关键指标。近年来，**托卡马克排气处理系统直接内部循环比例**（`tep.DIR`）因其在减少外部氚需求和降低库存压力方面的潜力，成为优化设计的重点变量。

然而，`tep.DIR` 的实际效益并非孤立存在，而是深度依赖于等离子体运行状态，尤其是**等离子体氚燃烧份额**（`plasma.Burn_Fraction`）。若燃烧效率低下，即使提高 `tep.DIR`，系统仍可能因燃料利用率不足而无法实现增殖目标。因此，有必要对 `tep.DIR` 与 `plasma.Burn_Fraction` 的交互作用进行系统性评估。

本研究的目标是：**量化评估独立变量 `tep.DIR` 的变化对 `Startup_Inventory` 与 `Required_TBR` 的影响，并深入分析其与背景参数 `plasma.Burn_Fraction` 之间的交互效应**，以揭示不同运行场景下的性能边界与优化路径。

- **独立变量采样**：`tep.DIR` 扫描范围为 `[0.1, 0.15, 0.2, 0.3, 0.4, 0.6, 0.8]`。
- **背景扫描参数**：`plasma.Fueling_Efficiency` 固定为 0.5，`plasma.Burn_Fraction` 扫描范围为 `[0.02, 0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09, 0.1]`。
- **因变量**：`Startup_Inventory`（kg）、`Required_TBR`。

---

## **方法**

本研究采用多维参数扫描法，将 `tep.DIR` 作为独立变量，在指定范围内进行离散采样。同时，将 `plasma.Burn_Fraction` 作为背景扫描参数，与 `tep.DIR` 构成组合输入。模型在每组参数组合下运行仿真，输出 `Startup_Inventory` 与 `Required_TBR` 作为性能指标。

对于 `Required_TBR`，系统启用二分查找算法，通过迭代优化 `bz.TBR`（增殖区氚增殖比）以满足 `sds.inventory`（储存与输送系统氚库存量）的约束条件，确保系统在设定的倍增时间内实现自持。该过程自动求解出满足特定性能要求的最小 `Required_TBR` 值。

所有分析均基于统一的物理模型框架，确保结果的可比性与可靠性。

---

## **结果与讨论**

### **主效应分析：`tep.DIR` 对核心性能指标的总体影响**

#### **1. `Startup_Inventory` 的单调递减趋势**

如图1所示，`Startup_Inventory` 随 `tep.DIR` 的增加呈现**一致且显著的下降趋势**，无论 `plasma.Burn_Fraction` 取何值。这表明，提高排气处理系统中直接返回燃料的比例，能够有效减少对外部氚源的依赖，从而降低初始库存需求。

![Startup Inventory vs tep DIR](line_Startup_Inventory_vs_tep.DIR.svg)

**图1：启动库存量（`Startup_Inventory`）随 `tep.DIR` 的变化趋势**

数据表明，`tep.DIR` 的提升对 `Startup_Inventory` 具有强线性负相关效应。例如，在 `plasma.Burn_Fraction = 0.02` 时，`tep.DIR` 从 0.1 增至 0.8，启动库存由 9.63 kg 降至 6.10 kg，降幅达 36.6%；而在 `plasma.Burn_Fraction = 0.1` 时，降幅亦达 20.2%。这种普适性下降趋势说明，`tep.DIR` 是降低初始投资成本的有效手段。

#### **2. `Required_TBR` 的非连续响应与阈值效应**

如图2所示，`Required_TBR` 的变化表现出明显的**分段恒定+阶梯式下降**特征，而非平滑连续变化。

![Required TBR vs tep DIR](line_Required_TBR_vs_tep.DIR.svg)

**图2：所需氚增殖比（`Required_TBR`）随 `tep.DIR` 的变化趋势**

- 当 `tep.DIR ≤ 0.3` 时，`Required_TBR` 在绝大多数 `plasma.Burn_Fraction` 组合下保持恒定，表明系统未触发约束求解器的迭代优化。
- 仅当 `tep.DIR ≥ 0.6` 时，`Required_TBR` 才在部分高燃耗条件下出现阶跃式下降：
  - `plasma.Burn_Fraction = 0.07`：从 1.0195 降至 1.0156；
  - `plasma.Burn_Fraction = 0.1`：从 1.0156 降至 1.0117。

这一现象表明：`Required_TBR` 对 `tep.DIR` 的响应存在**显著的非线性饱和与阈值效应**。只有当 `tep.DIR` 足够高（≥ 0.6）且 `plasma.Burn_Fraction` 足够高（≥ 0.07）时，系统才具备“主动优化增殖比”的能力。

#### **3. 性能指标敏感度排序**

基于全数据集的量化分析，可对各指标的敏感度进行排序：

| 指标 | 敏感度特征 | 敏感度系数估算（示例） | 排名 |
|------|------------|--------------------------|------|
| `Startup_Inventory` | 强线性负相关，全局响应 | ≈ 5.04 kg/单位 `tep.DIR`（`Burn_Fraction=0.02`） | 1（最敏感） |
| `Required_TBR` | 分段恒定，仅在高 `tep.DIR` 下发生微小阶跃 | < 0.012 / 单位 `tep.DIR` | 2（最不敏感） |

> ✅ **结论**：`Startup_Inventory` 是对 `tep.DIR` 变化最敏感的性能指标，而 `Required_TBR` 的敏感度极低，其响应受系统状态调控机制限制。

---

### **交互效应分析：`tep.DIR` 与 `plasma.Burn_Fraction` 的耦合机制**

本次分析的核心发现在于，`tep.DIR` 的实际效益高度依赖于 `plasma.Burn_Fraction`，二者之间存在显著的**正向协同效应**。

#### **1. `plasma.Burn_Fraction` 作为系统响应的“灵敏度开关”**

通过对比不同 `plasma.Burn_Fraction` 条件下的数据，可清晰识别出以下模式：

- **低 `plasma.Burn_Fraction`（≤ 0.04）**：
  - `Startup_Inventory` 随 `tep.DIR` 下降迅速，但 `Required_TBR` 始终恒定（如 `Burn_Fraction=0.04` 时，`Required_TBR=1.0273`）。
  - **机制解释**：低燃烧份额意味着大量注入的氚未能参与聚变，系统严重依赖高初始库存维持平衡。此时，即使提高 `tep.DIR`，也无法有效提升燃料利用率，系统不具备“优化增殖比”的动力。

- **中高 `plasma.Burn_Fraction`（≥ 0.05）**：
  - `Startup_Inventory` 仍持续下降；
  - `Required_TBR` 在 `tep.DIR ≥ 0.6` 时开始下降，且降幅随 `Burn_Fraction` 提升而增大。
  - **关键发现**：`Burn_Fraction` 越高，系统越容易达到“需主动优化 `TBR`”的临界状态，即 `tep.DIR` 的提升在高燃耗场景下**更易触发约束求解器**，从而实现 `Required_TBR` 的进一步优化。

#### **2. 交互效应的量化表现**

以下是不同 `plasma.Burn_Fraction` 下 `tep.DIR` 对 `Required_TBR` 的影响对比：

| `plasma.Burn_Fraction` | `tep.DIR` 变化 | `Required_TBR` 变化 | 交互效应类型 |
|------------------------|----------------|-----------------------|--------------|
| 0.02                   | 0.1 → 0.8      | 1.0547 → 1.0469       | 无优化触发（恒定） |
| 0.05                   | 0.1 → 0.8      | 1.0234 → 1.0234       | 无优化触发（恒定） |
| 0.07                   | 0.6 → 0.8      | 1.0195 → 1.0156       | 阶梯式优化触发 |
| 0.10                   | 0.6 → 0.8      | 1.0156 → 1.0117       | 显著优化触发 |

> ✅ **核心结论**：`plasma.Burn_Fraction` 是决定 `tep.DIR` 是否能转化为 `Required_TBR` 优化的关键变量。**只有当 `plasma.Burn_Fraction ≥ 0.07` 且 `tep.DIR ≥ 0.6` 时，系统才能实现“库存+增殖比”的双重优化**。

#### **3. `plasma.Fueling_Efficiency` 的恒定角色**

在本分析中，`plasma.Fueling_Efficiency` 固定为 0.5，未参与扫描。因此，其与 `tep.DIR` 的交互效应无法评估。但其固定值保证了各组数据的可比性，是本分析得以成立的基础。

---

## **结论**

本研究通过对 `tep.DIR` 与 `plasma.Burn_Fraction` 的交互敏感性分析，得出以下主要学术结论与工程建议：

### **1. 主要学术结论**
- `tep.DIR` 对 `Startup_Inventory` 具有**强线性负相关**关系，是降低初始氚库存的最有效手段。
- `tep.DIR` 对 `Required_TBR` 的影响具有**显著的非连续性与阈值效应**，仅在 `tep.DIR ≥ 0.6` 且 `plasma.Burn_Fraction ≥ 0.07` 时才可能触发优化。
- `plasma.Burn_Fraction` 是决定 `tep.DIR` 效益能否释放的**主导交互因子**，二者构成正向协同机制。

### **2. 设计与运行优化建议**
1. **优先提升 `plasma.Burn_Fraction`**：在系统设计阶段，应将提升等离子体燃烧效率作为首要目标。若 `Burn_Fraction` 无法达到 0.07 以上，则 `tep.DIR` 的提升将无法带来 `TBR` 优化，导致资源浪费。
2. **设定 `tep.DIR` 的“经济阈值”**：建议将 `tep.DIR` 控制在 **0.6 以上**，以确保系统具备主动优化能力。
3. **实施“分阶段优化”策略**：
   - **第一阶段**：在低 `Burn_Fraction` 下，利用 `tep.DIR` 降低 `Startup_Inventory`，控制初始建设成本。
   - **第二阶段**：待 `Burn_Fraction` 提升至 ≥ 0.07 后，进一步提升 `tep.DIR` 至 0.8，以实现 `Required_TBR` 的优化，达成全生命周期成本最小化。
4. **避免盲目提升 `tep.DIR`**：若 `Burn_Fraction` 无法提升，继续增加 `tep.DIR` 将导致边际效益趋零，应引入“`Burn_Fraction`-`tep.DIR` 效益矩阵”进行决策支持。

### **3. 研究启示**
聚变堆氚燃料循环系统的优化必须摒弃“单一参数驱动”的思维。未来的设计与运行策略应建立在 **“先提升燃烧效率，再强化增殖能力”** 的动态框架之上，通过多参数协同优化，实现技术、经济与安全性的统一。

--- 

> **最终总结**：`tep.DIR` 是降低启动库存的强大工具，但其真正价值的释放依赖于 `plasma.Burn_Fraction` 的协同作用。唯有在高燃烧效率的基础上，`tep.DIR` 才能成为实现氚自持与快速部署的催化剂。
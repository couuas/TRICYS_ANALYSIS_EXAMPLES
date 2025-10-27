# plasma Burn Fraction 与 plasma Fueling Efficiency、Required_TBR约束值 交互敏感性分析报告


生成时间: 2025-10-27 12:17:39.906147


## 分析案例配置详情


本分析案例的具体配置如下，这决定了仿真的扫描方式和分析的重点：


| 配置项 | 值 | 说明 |
| :--- | :--- | :--- |
| **`name`** | `"DoubleTime_PLASMA_Analysis"` | 本次分析案例的名称。 |
| **`independent_variable`** | `"plasma.Burn_Fraction"` | 独立扫描变量，即本次分析中主要改变的参数。 |
| **`independent_variable_sampling`** | `[0.02, 0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09, 0.1]` | 独立变量的采样方法和范围。 |
| **`default_independent_values`** | `{"plasma.Burn_Fraction": 0.05}` | 独立扫描变量在模型中的原始默认值。 |
| **`simulation_parameters`** | `{"plasma.Fueling_Efficiency": 0.5, "Required_TBR": {"metric_name": "Doubling_Time", "metric_max_value": [4380, 8760, 13140, 17530]}}` | 背景扫描参数，与独立变量组合形成多维扫描。 |
| **`default_simulation_values`** | `{"plasma.Fueling_Efficiency": 0.5}` | 背景扫描参数在模型中的原始默认值。 |
| **`dependent_variables`** | `["Required_TBR"]` | 因变量，即我们关心的、随自变量变化的性能指标。 |


## “Required_TBR”优化配置

当“Required_TBR”作为因变量时，系统会启用一个二分查找算法来寻找满足特定性能指标的最小`bz.TBR`值。以下是本次优化任务的具体配置：


| 配置项 | 值 | 说明 |
| :--- | :--- | :--- |
| **`source_column`** | `"sds.inventory"` | 限制条件的数据源列。 |
| **`parameter_to_optimize`** | `"bz.TBR"` | 优化的目标参数。 |
| **`search_range`** | `[1, 1.5]` | 参数的搜索范围。 |
| **`tolerance`** | `0.005` | 搜索的收敛精度。 |
| **`max_iterations`** | `10` | 最大迭代次数。 |
| **`metric_name (from simulation_parameters)`** | `"Doubling_Time"` | 限制条件的性能指标。 |
| **`metric_max_value (from simulation_parameters)`** | `[4380, 8760, 13140, 17530]` | 限制条件满足的上限值。（hour） |


## 约束求解性能指标分析图


### 不同约束值下的“Required TBR”分析 (按参数分组)

下图展示了“Required TBR”指标随独立变量变化的趋势。每个子图对应一组特定的背景扫描参数组合，子图内的每条曲线代表一个具体的约束值。


![不同约束值下的Required TBR分析](multi_Required_TBR_analysis_by_param.svg)


## 性能指标总表 (分组: `plasma.Fueling_Efficiency`)


#### 数据子表 (原始默认值: `plasma.Fueling_Efficiency=0.5`)

##### “Required TBR” 相关数据

|   plasma.Burn_Fraction | Constraint Doubling_Time   |   Required_TBR |
|-----------------------:|:---------------------------|---------------:|
|                   0.02 | 0.50 year                  |        1.30078 |
|                   0.03 | 0.50 year                  |        1.25    |
|                   0.04 | 0.50 year                  |        1.22656 |
|                   0.05 | 0.50 year                  |        1.21094 |
|                   0.06 | 0.50 year                  |        1.20312 |
|                   0.07 | 0.50 year                  |        1.19531 |
|                   0.08 | 0.50 year                  |        1.1875  |
|                   0.09 | 0.50 year                  |        1.18359 |
|                   0.1  | 0.50 year                  |        1.18359 |
|                   0.02 | 1.00 year                  |        1.17578 |
|                   0.03 | 1.00 year                  |        1.14453 |
|                   0.04 | 1.00 year                  |        1.125   |
|                   0.05 | 1.00 year                  |        1.11719 |
|                   0.06 | 1.00 year                  |        1.10938 |
|                   0.07 | 1.00 year                  |        1.10547 |
|                   0.08 | 1.00 year                  |        1.10156 |
|                   0.09 | 1.00 year                  |        1.10156 |
|                   0.1  | 1.00 year                  |        1.09766 |
|                   0.02 | 1.50 year                  |        1.13281 |
|                   0.03 | 1.50 year                  |        1.10547 |
|                   0.04 | 1.50 year                  |        1.09375 |
|                   0.05 | 1.50 year                  |        1.08594 |
|                   0.06 | 1.50 year                  |        1.08203 |
|                   0.07 | 1.50 year                  |        1.07812 |
|                   0.08 | 1.50 year                  |        1.07422 |
|                   0.09 | 1.50 year                  |        1.07031 |
|                   0.1  | 1.50 year                  |        1.07031 |
|                   0.02 | 2.00 year                  |        1.11328 |
|                   0.03 | 2.00 year                  |        1.08984 |
|                   0.04 | 2.00 year                  |        1.07812 |
|                   0.05 | 2.00 year                  |        1.07031 |
|                   0.06 | 2.00 year                  |        1.06641 |
|                   0.07 | 2.00 year                  |        1.0625  |
|                   0.08 | 2.00 year                  |        1.05859 |
|                   0.09 | 2.00 year                  |        1.05859 |
|                   0.1  | 2.00 year                  |        1.05469 |



---


---

# AI模型分析提示词 (deepseek-v3.1)

```markdown
**角色：** 你是一名聚变反应堆氚燃料循环领域的专家。

**任务：** 请**完全基于**下方提供的**两类数据表格**，对聚变堆燃料循环模型的**敏感性分析**结果进行深度解读。

**分析要点 (必须严格依据数据表格作答)：**

1.  **全局敏感性分析 (参考“性能指标总表”) :**
    *   分析性能指标总表（ `Startup_Inventory`, `Doubling_Time` 以及以 `Required_` 开头的求解指标等）呈现出怎样的**总体趋势**？请进行量化描述。
    *   如果存在多个性能指标，分析哪个性能指标对独立变量 `plasma.Burn_Fraction` 的变化最为敏感？哪个最不敏感？

2.  **交互效应分析：** 本次分析包含了多变量的交互效应。请分析独立变量 `plasma.Burn_Fraction` 与背景扫描参数 (`plasma.Fueling_Efficiency`, `Required_TBR约束值 (hour)`) 之间的交互作用对各项性能指标的影响。请注意，独立变量或背景扫描参数中，可能包含常规的模型参数，也可能包含为满足特定性能目标（限制倍增时间Double_Time达到倍增）而求解出的特殊变量（约束限制变量Double_Time）。请讨论在不同的变量组合下，性能指标的敏感性有何不同？是否存在显著的交互效应？

3.  **综合结论：**
结合所有分析（包括主趋势、背景参数交互效应），总结在不同的运行场景下，调整 `plasma.Burn_Fraction` 对整个氚燃料循环系统的综合影响和潜在的利弊权衡。
    *   基于这些发现，可以得出哪些关于系统设计或运行优化的初步建议？
```



---

# AI模型分析结果

根据您提供的性能指标总表数据（仅包含 `Required_TBR` 指标，且背景扫描参数 `plasma.Fueling_Efficiency` 固定为默认值 0.5），我将严格按照数据表格进行深度解读。分析聚焦于独立变量 `plasma.Burn_Fraction` 与背景扫描参数 `Required_TBR约束值 (Doubling_Time)` 的交互作用对求解指标 `Required_TBR`（满足倍增时间约束所需的最小TBR值）的影响。

### 1. 全局敏感性分析 (基于“性能指标总表”)
性能指标总表仅提供了 `Required_TBR` 这一指标的数据。该指标表示在给定 `plasma.Burn_Fraction` 和 `Doubling_Time` 约束下，通过二分查找算法求解出的满足 `Doubling_Time <= 约束值` 的最小 `bz.TBR` 值。

**总体趋势分析：**
- **`Required_TBR` 随 `plasma.Burn_Fraction` 增大而减小：** 对于任一固定的 `Doubling_Time` 约束值（例如 0.50 year），当 `plasma.Burn_Fraction` 从 0.02 增加到 0.1 时，`Required_TBR` 从 1.30078 单调递减至 1.18359。这表明更高的燃烧分数（更高效的氚燃烧）可以降低对包层产氚（TBR）的要求，因为系统自身消耗的氚更少，对外部氚增殖的依赖降低。
- **`Required_TBR` 随 `Doubling_Time` 约束放宽而减小：** 对于任一固定的 `plasma.Burn_Fraction`（例如 0.02），当 `Doubling_Time` 约束从 0.50 year 放宽至 2.00 year 时，`Required_TBR` 从 1.30078 递减至 1.11328。更长的允许倍增时间意味着系统对氚库存增长的要求更低，因此所需的最小TBR也相应降低。
- **敏感性量化：**
  - **对 `plasma.Burn_Fraction` 的敏感性：** 在 `Doubling_Time=0.50 year` 时，`Burn_Fraction` 从 0.02 到 0.1（变化幅度 0.08），`Required_TBR` 从 1.30078 到 1.18359（变化幅度 -0.11719，相对变化约 -9.0%）。在 `Doubling_Time=2.00 year` 时，相同 `Burn_Fraction` 变化导致 `Required_TBR` 从 1.11328 到 1.05469（变化幅度 -0.05859，相对变化约 -5.3%）。**`Required_TBR` 对 `Burn_Fraction` 的变化是敏感的，且敏感性在更严格的倍增时间约束下更高。**
  - **对 `Doubling_Time` 约束的敏感性：** 在 `Burn_Fraction=0.02` 时，`Doubling_Time` 约束从 0.50 year 到 2.00 year（变化 1.50 year），`Required_TBR` 从 1.30078 到 1.11328（变化幅度 -0.1875，相对变化约 -14.4%）。在 `Burn_Fraction=0.1` 时，相同约束变化导致 `Required_TBR` 从 1.18359 到 1.05469（变化幅度 -0.1289，相对变化约 -10.9%）。**`Required_TBR` 对 `Doubling_Time` 约束的变化也非常敏感，且敏感性在较低 `Burn_Fraction` 时略高。**

**结论：** `Required_TBR` 对两个变量（`plasma.Burn_Fraction` 和 `Doubling_Time` 约束）的变化均表现出显著的敏感性。其中，对 `Doubling_Time` 约束的绝对变化量（ΔRequired_TBR）略大于对 `Burn_Fraction` 的变化量，但相对敏感性相近。**`Required_TBR` 是本次分析中最核心的敏感指标。**

### 2. 交互效应分析
本次分析考察了独立变量 `plasma.Burn_Fraction` 与背景扫描参数 `Required_TBR约束值 (Doubling_Time)` 的交互作用对 `Required_TBR`（求解值）的影响。

**交互作用表现：**
- **`Burn_Fraction` 与 `Doubling_Time` 约束对降低 `Required_TBR` 具有协同效应：** 数据显示，同时提高 `Burn_Fraction` 和放宽 `Doubling_Time` 约束可以最大程度地降低对包层TBR的要求。例如，`Required_TBR` 的最低值 1.05469 出现在 `Burn_Fraction=0.1` 和 `Doubling_Time=2.00 year` 的组合下。
- **`Burn_Fraction` 的边际效益递减：** 对于任一固定的 `Doubling_Time` 约束，`Required_TBR` 随 `Burn_Fraction` 增加的下降幅度逐渐减小（曲线逐渐平缓）。例如，在 `Doubling_Time=0.50 year` 下，`Burn_Fraction` 从 0.02 到 0.03 时，`Required_TBR` 下降 0.05078；而从 0.09 到 0.1 时，仅下降 0.0（甚至保持不变）。这表明在较高的燃烧分数下，进一步改善燃烧效率对降低TBR要求的效果有限。
- **`Doubling_Time` 约束的放松效应受 `Burn_Fraction` 调制：** 在较低的 `Burn_Fraction`（如 0.02）下，放松 `Doubling_Time` 约束（从 0.50 到 2.00 year）带来的 `Required_TBR` 下降幅度（-0.1875）要高于在较高 `Burn_Fraction`（如 0.1）下的下降幅度（-0.1289）。这意味着当燃烧效率本身较低时，允许更长的倍增时间能更有效地补偿对TBR的高要求。

**结论：** 存在显著的交互效应。**`plasma.Burn_Fraction` 和 `Doubling_Time` 约束值不是独立作用的变量**。系统对TBR的要求（`Required_TBR`）同时依赖于这两个变量的取值组合。较高的 `Burn_Fraction` 可以缓解严格倍增时间约束带来的高压，而较宽松的倍增时间约束也能降低对高燃烧分数的依赖。两者共同决定了实现氚自持的难易程度。

### 3. 综合结论与优化建议
**综合影响：**
调整 `plasma.Burn_Fraction` 对整个氚燃料循环系统的核心影响体现在**显著改变对包层产氚能力（TBR）的最低要求**上。更高的燃烧分数直接降低了对TBR的需求，这使得工程上更容易实现氚的自持（TBR > 1.0 的挑战减小）。但同时，极高的燃烧分数（如 >0.08）带来的边际效益递减，且可能受到等离子体物理实现的限制。

**利弊权衡：**
- **利：** 提高 `Burn_Fraction` 是降低对包层性能（TBR）要求的有效手段，可以放宽对倍增时间的约束，或降低对氚提取、储存等子系统性能的要求。
- **弊：** 实现高 `Burn_Fraction` 可能需要更先进的等离子体控制技术、更高的磁场或温度，增加了等离子体操作的难度和成本。且超过一定值后，收益不再显著。

**初步优化建议：**
1.  **设定合理的倍增时间目标：** 如果工程上能够接受较长的氚库存倍增时间（如 1.5-2.0 年），那么对 `Burn_Fraction` 和 `TBR` 的要求都可以显著放宽（`Required_TBR` 可降至 1.05-1.11 左右），大大降低了包层设计的难度。
2.  **设定 `Burn_Fraction` 的目标区间：** 鉴于边际效益递减，将 `Burn_Fraction` 目标设定在 0.05-0.07 范围可能是性价比最高的选择。在此区间内，`Required_TBR` 对 `Burn_Fraction` 的变化仍较为敏感（下降明显），且数值上（~1.10-1.20）对于大多数固态增殖剂包层设计而言是可能实现的。
3.  **协同设计：** 包层TBR目标（`Required_TBR`）的确定必须与等离子体物理 achievable 的 `Burn_Fraction` 以及电厂可接受的氚库存增长周期（`Doubling_Time`）进行**协同优化**。不应孤立地追求某一指标的最优。
4.  **注意约束条件：** 本分析基于固定的 `plasma.Fueling_Efficiency=0.5`。若加料效率变化，上述关系和具体数值会发生改变，需进行额外的敏感性分析。

**总结：** 通过提高燃烧分数或放宽倍增时间约束，可以有效降低聚变堆对包层TBR的要求。设计者应在等离子体性能、包层技术可行性和电厂运行策略之间寻求最佳平衡点。建议将 `plasma.Burn_Fraction` 目标定为 0.05-0.07，并尽可能争取 1.5 年以上的倍增时间，以将所需的TBR控制在 1.10 以下，增加工程实现的可靠性。
```

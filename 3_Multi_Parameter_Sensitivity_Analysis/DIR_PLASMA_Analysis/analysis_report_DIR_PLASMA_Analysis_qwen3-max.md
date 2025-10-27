# tep DIR 与 plasma Fueling Efficiency、plasma Burn Fraction 交互敏感性分析报告


生成时间: 2025-10-27 13:01:33.862447


## 分析案例配置详情


本分析案例的具体配置如下，这决定了仿真的扫描方式和分析的重点：


| 配置项 | 值 | 说明 |
| :--- | :--- | :--- |
| **`name`** | `"DIR_PLASMA_Analysis"` | 本次分析案例的名称。 |
| **`independent_variable`** | `"tep.DIR"` | 独立扫描变量，即本次分析中主要改变的参数。 |
| **`independent_variable_sampling`** | `[0.1, 0.15, 0.2, 0.3, 0.4, 0.6, 0.8]` | 独立变量的采样方法和范围。 |
| **`default_independent_values`** | `{"tep.DIR": 0.85}` | 独立扫描变量在模型中的原始默认值。 |
| **`simulation_parameters`** | `{"plasma.Fueling_Efficiency": [0.5], "plasma.Burn_Fraction": [0.02, 0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09, 0.1]}` | 背景扫描参数，与独立变量组合形成多维扫描。 |
| **`default_simulation_values`** | `{"plasma.Fueling_Efficiency": 0.5, "plasma.Burn_Fraction": 0.05}` | 背景扫描参数在模型中的原始默认值。 |
| **`dependent_variables`** | `["Startup_Inventory", "Required_TBR"]` | 因变量，即我们关心的、随自变量变化的性能指标。 |


## “Required_TBR”优化配置

当“Required_TBR”作为因变量时，系统会启用一个二分查找算法来寻找满足特定性能指标的最小`bz.TBR`值。以下是本次优化任务的具体配置：


| 配置项 | 值 | 说明 |
| :--- | :--- | :--- |
| **`source_column`** | `"sds.inventory"` | 限制条件的数据源列。 |
| **`parameter_to_optimize`** | `"bz.TBR"` | 优化的目标参数。 |
| **`search_range`** | `[1, 1.5]` | 参数的搜索范围。 |
| **`tolerance`** | `0.005` | 搜索的收敛精度。 |
| **`max_iterations`** | `10` | 最大迭代次数。 |


## 性能指标分析图


### Startup Inventory vs tep DIR

![Startup Inventory vs tep DIR](line_Startup_Inventory_vs_tep.DIR.svg)


## 约束求解性能指标分析图


### Required TBR vs tep DIR

![Required TBR vs tep DIR](line_Required_TBR_vs_tep.DIR.svg)


## 性能指标总表 (分组: `plasma.Fueling_Efficiency`, `plasma.Burn_Fraction`)


#### 数据子表 (原始默认值: `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.05`)

##### 性能指标

|   tep DIR |   Startup Inventory (kg) |
|----------:|-------------------------:|
|      0.1  |                     4.9  |
|      0.15 |                     4.8  |
|      0.2  |                     4.7  |
|      0.3  |                     4.5  |
|      0.4  |                     4.3  |
|      0.6  |                     3.91 |
|      0.8  |                     3.51 |


##### “Required TBR” 相关数据

|   tep DIR |   Required TBR |
|----------:|---------------:|
|      0.1  |         1.0234 |
|      0.15 |         1.0234 |
|      0.2  |         1.0234 |
|      0.3  |         1.0234 |
|      0.4  |         1.0234 |
|      0.6  |         1.0234 |
|      0.8  |         1.0234 |



---

> 其他参数组合下的数据子表：

#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.02` 时)

##### 性能指标

|   tep DIR |   Startup Inventory (kg) |
|----------:|-------------------------:|
|      0.1  |                     9.63 |
|      0.15 |                     9.38 |
|      0.2  |                     9.12 |
|      0.3  |                     8.62 |
|      0.4  |                     8.12 |
|      0.6  |                     7.11 |
|      0.8  |                     6.1  |


##### “Required TBR” 相关数据

|   tep DIR |   Required TBR |
|----------:|---------------:|
|      0.1  |         1.0547 |
|      0.15 |         1.0547 |
|      0.2  |         1.0547 |
|      0.3  |         1.0508 |
|      0.4  |         1.0508 |
|      0.6  |         1.0508 |
|      0.8  |         1.0469 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.03` 时)

##### 性能指标

|   tep DIR |   Startup Inventory (kg) |
|----------:|-------------------------:|
|      0.1  |                     7    |
|      0.15 |                     6.83 |
|      0.2  |                     6.66 |
|      0.3  |                     6.33 |
|      0.4  |                     6    |
|      0.6  |                     5.33 |
|      0.8  |                     4.66 |


##### “Required TBR” 相关数据

|   tep DIR |   Required TBR |
|----------:|---------------:|
|      0.1  |         1.0391 |
|      0.15 |         1.0391 |
|      0.2  |         1.0352 |
|      0.3  |         1.0352 |
|      0.4  |         1.0352 |
|      0.6  |         1.0352 |
|      0.8  |         1.0312 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.04` 时)

##### 性能指标

|   tep DIR |   Startup Inventory (kg) |
|----------:|-------------------------:|
|      0.1  |                     5.69 |
|      0.15 |                     5.56 |
|      0.2  |                     5.44 |
|      0.3  |                     5.19 |
|      0.4  |                     4.94 |
|      0.6  |                     4.44 |
|      0.8  |                     3.94 |


##### “Required TBR” 相关数据

|   tep DIR |   Required TBR |
|----------:|---------------:|
|      0.1  |         1.0273 |
|      0.15 |         1.0273 |
|      0.2  |         1.0273 |
|      0.3  |         1.0273 |
|      0.4  |         1.0273 |
|      0.6  |         1.0273 |
|      0.8  |         1.0273 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.06` 时)

##### 性能指标

|   tep DIR |   Startup Inventory (kg) |
|----------:|-------------------------:|
|      0.1  |                     4.37 |
|      0.15 |                     4.29 |
|      0.2  |                     4.21 |
|      0.3  |                     4.05 |
|      0.4  |                     3.88 |
|      0.6  |                     3.55 |
|      0.8  |                     3.22 |


##### “Required TBR” 相关数据

|   tep DIR |   Required TBR |
|----------:|---------------:|
|      0.1  |         1.0195 |
|      0.15 |         1.0195 |
|      0.2  |         1.0195 |
|      0.3  |         1.0195 |
|      0.4  |         1.0195 |
|      0.6  |         1.0195 |
|      0.8  |         1.0195 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.07` 时)

##### 性能指标

|   tep DIR |   Startup Inventory (kg) |
|----------:|-------------------------:|
|      0.1  |                     4    |
|      0.15 |                     3.93 |
|      0.2  |                     3.86 |
|      0.3  |                     3.72 |
|      0.4  |                     3.58 |
|      0.6  |                     3.3  |
|      0.8  |                     3.02 |


##### “Required TBR” 相关数据

|   tep DIR |   Required TBR |
|----------:|---------------:|
|      0.1  |         1.0195 |
|      0.15 |         1.0195 |
|      0.2  |         1.0195 |
|      0.3  |         1.0195 |
|      0.4  |         1.0195 |
|      0.6  |         1.0156 |
|      0.8  |         1.0156 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.08` 时)

##### 性能指标

|   tep DIR |   Startup Inventory (kg) |
|----------:|-------------------------:|
|      0.1  |                     3.72 |
|      0.15 |                     3.66 |
|      0.2  |                     3.6  |
|      0.3  |                     3.47 |
|      0.4  |                     3.35 |
|      0.6  |                     3.11 |
|      0.8  |                     2.86 |


##### “Required TBR” 相关数据

|   tep DIR |   Required TBR |
|----------:|---------------:|
|      0.1  |         1.0156 |
|      0.15 |         1.0156 |
|      0.2  |         1.0156 |
|      0.3  |         1.0156 |
|      0.4  |         1.0156 |
|      0.6  |         1.0156 |
|      0.8  |         1.0156 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.09` 时)

##### 性能指标

|   tep DIR |   Startup Inventory (kg) |
|----------:|-------------------------:|
|      0.1  |                     3.5  |
|      0.15 |                     3.44 |
|      0.2  |                     3.39 |
|      0.3  |                     3.28 |
|      0.4  |                     3.17 |
|      0.6  |                     2.96 |
|      0.8  |                     2.74 |


##### “Required TBR” 相关数据

|   tep DIR |   Required TBR |
|----------:|---------------:|
|      0.1  |         1.0156 |
|      0.15 |         1.0156 |
|      0.2  |         1.0156 |
|      0.3  |         1.0156 |
|      0.4  |         1.0156 |
|      0.6  |         1.0156 |
|      0.8  |         1.0156 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.1` 时)

##### 性能指标

|   tep DIR |   Startup Inventory (kg) |
|----------:|-------------------------:|
|      0.1  |                     3.32 |
|      0.15 |                     3.27 |
|      0.2  |                     3.23 |
|      0.3  |                     3.13 |
|      0.4  |                     3.03 |
|      0.6  |                     2.84 |
|      0.8  |                     2.65 |


##### “Required TBR” 相关数据

|   tep DIR |   Required TBR |
|----------:|---------------:|
|      0.1  |         1.0156 |
|      0.15 |         1.0156 |
|      0.2  |         1.0156 |
|      0.3  |         1.0156 |
|      0.4  |         1.0156 |
|      0.6  |         1.0117 |
|      0.8  |         1.0117 |





---

# AI模型分析提示词 (qwen3-max)

```markdown
**角色：** 你是一名聚变反应堆氚燃料循环领域的专家。

**任务：** 请**完全基于**下方提供的**两类数据表格**，对聚变堆燃料循环模型的**敏感性分析**结果进行深度解读。

**分析要点 (必须严格依据数据表格作答)：**

1.  **全局敏感性分析 (参考“性能指标总表”) :**
    *   分析性能指标总表（ `Startup_Inventory`, `Doubling_Time` 以及以 `Required_` 开头的求解指标等）呈现出怎样的**总体趋势**？请进行量化描述。
    *   如果存在多个性能指标，分析哪个性能指标对独立变量 `tep.DIR` 的变化最为敏感？哪个最不敏感？

2.  **交互效应分析：** 本次分析包含了多变量的交互效应。请分析独立变量 `tep.DIR` 与背景扫描参数 (`plasma.Fueling_Efficiency`, `plasma.Burn_Fraction`) 之间的交互作用对各项性能指标的影响。请注意，独立变量或背景扫描参数中，可能包含常规的模型参数，也可能包含为满足特定性能目标（限制倍增时间Double_Time达到倍增）而求解出的特殊变量（约束限制变量Double_Time）。请讨论在不同的变量组合下，性能指标的敏感性有何不同？是否存在显著的交互效应？

3.  **综合结论：**
结合所有分析（包括主趋势、背景参数交互效应），总结在不同的运行场景下，调整 `tep.DIR` 对整个氚燃料循环系统的综合影响和潜在的利弊权衡。
    *   基于这些发现，可以得出哪些关于系统设计或运行优化的初步建议？
```



---

# AI模型分析结果

作为聚变反应堆氚燃料循环领域的专家，我将严格基于所提供的数据表格，对“tep.DIR”与等离子体加料效率（plasma.Fueling_Efficiency）及燃烧分数（plasma.Burn_Fraction）之间的交互敏感性进行深度解读。分析完全依据表格数据，不引入任何外部假设或图表信息。

---

### 1. 全局敏感性分析

#### （1）总体趋势的量化描述

**Startup Inventory（启动氚库存，kg）：**  
在所有给定的 plasma.Burn_Fraction（0.02–0.10）条件下，随着 tep.DIR 从 0.1 增加至 0.8，Startup Inventory 均呈现**单调递减趋势**。以默认工况（Burn_Fraction = 0.05）为例：
- tep.DIR = 0.1 → Startup Inventory = 4.9 kg  
- tep.DIR = 0.8 → Startup Inventory = 3.51 kg  
降幅为 (4.9 − 3.51)/4.9 ≈ **28.4%**

在 Burn_Fraction = 0.02 的最不利工况下，降幅更大：
- 从 9.63 kg 降至 6.1 kg，降幅达 **36.7%**

这表明：**tep.DIR 的提升显著降低启动阶段所需的氚库存**，且该效应在低燃烧分数下更为显著。

**Required TBR（所需氚增殖比）：**  
与 Startup Inventory 不同，Required TBR 对 tep.DIR 的变化**整体不敏感**。在多数 Burn_Fraction 水平下（如 0.04、0.05、0.06、0.08、0.09），Required TBR 在整个 tep.DIR 扫描范围内**保持恒定**（如 1.0234、1.0273、1.0195、1.0156 等）。仅在部分低 Burn_Fraction 工况（如 0.02、0.03、0.07、0.10）中，Required TBR 在 tep.DIR ≥ 0.3 或 ≥ 0.6 时出现**微小下降**（通常变化幅度 ≤ 0.004）。

例如，在 Burn_Fraction = 0.02 时：
- tep.DIR = 0.1 → Required TBR = 1.0547  
- tep.DIR = 0.8 → Required TBR = 1.0469  
降幅仅 **0.74%**

因此，**Required TBR 对 tep.DIR 的敏感性极低**，其主要驱动因素是 plasma.Burn_Fraction，而非 tep.DIR。

> 注：表中未提供 Doubling_Time 数据，故无法分析该指标。根据任务描述，因变量仅为 Startup_Inventory 和 Required_TBR，因此“Doubling_Time”在本分析中不构成有效性能指标。

#### （2）敏感性对比

- **最敏感指标：Startup Inventory**  
  在所有工况下均随 tep.DIR 单调显著下降，变化幅度达 28–37%，对 tep.DIR 高度敏感。

- **最不敏感指标：Required TBR**  
  在多数 Burn_Fraction 下完全不变，在少数情况下仅有微小波动（<1%），表明其对 tep.DIR 几乎不敏感。

---

### 2. 交互效应分析

本次分析固定 plasma.Fueling_Efficiency = 0.5，仅扫描 plasma.Burn_Fraction（0.02–0.10）与 tep.DIR（0.1–0.8）的组合，构成二维参数空间。交互效应体现在：**tep.DIR 对 Startup Inventory 的影响强度依赖于 plasma.Burn_Fraction 的取值**。

#### （1）Startup Inventory 的交互效应

- **Burn_Fraction 越低，tep.DIR 的边际效益越大**。  
  例如，当 tep.DIR 从 0.1 提升至 0.8：
  - Burn_Fraction = 0.02：Startup Inventory 减少 3.53 kg  
  - Burn_Fraction = 0.10：仅减少 0.67 kg  

  这表明：在燃烧效率较差（低 Burn_Fraction）的运行场景下，提高 tep.DIR（即提升氚提取与再循环效率）对缓解启动氚库存压力具有**更强的补偿作用**。

- **绝对库存水平随 Burn_Fraction 增加而系统性下降**。  
  在任意 tep.DIR 下，Burn_Fraction 从 0.02 升至 0.10，Startup Inventory 大幅降低（如 tep.DIR=0.8 时，从 6.1 kg 降至 2.65 kg），说明燃烧分数是决定氚需求的根本性参数，而 tep.DIR 是调节性参数。

#### （2）Required TBR 的交互效应

- **Required TBR 主要由 plasma.Burn_Fraction 决定**，tep.DIR 仅在特定区间产生微弱调制。  
  例如：
  - Burn_Fraction = 0.05 → Required TBR 恒为 1.0234（与 tep.DIR 无关）  
  - Burn_Fraction = 0.02 → Required TBR 从 1.0547 微降至 1.0469（仅当 tep.DIR ≥ 0.6 时变化）

  这说明：**满足氚自持所需的最小 TBR 几乎不受 DIR 影响**，主要取决于等离子体中实际参与聚变的氚比例（Burn_Fraction）。只有在极低 Burn_Fraction 且高 DIR 条件下，循环效率的提升才能略微降低对增殖包层性能的要求。

- **无显著交互非线性**：未观察到 tep.DIR 与 Burn_Fraction 之间存在交叉反转或阈值效应，交互作用表现为**单调叠加**。

---

### 3. 综合结论与初步建议

#### （1）tep.DIR 的综合影响

- **正面影响**：提高 tep.DIR 可显著降低启动阶段的氚库存需求，尤其在燃烧效率不佳（低 Burn_Fraction）的早期运行阶段或低性能等离子体场景中，这一效益尤为突出。这对于缓解氚资源稀缺、降低初始燃料采购成本和放射性库存风险具有重要意义。
  
- **局限性**：tep.DIR 的提升**无法显著降低对增殖包层 TBR 的要求**。即使 DIR 接近理想值（0.8），Required TBR 仍主要由 Burn_Fraction 决定。例如，Burn_Fraction = 0.02 时，Required TBR 仍高达 ~1.05，远高于 Burn_Fraction = 0.10 时的 ~1.01。

#### （2）运行场景下的权衡

- **高 Burn_Fraction 场景（如 0.08–0.10）**：  
  Startup Inventory 本身已较低（<3.72 kg @ tep.DIR=0.1），tep.DIR 的优化空间有限，重点应放在维持高燃烧效率上。

- **低 Burn_Fraction 场景（如 0.02–0.04）**：  
  Startup Inventory 高达 5–9.6 kg，此时提升 tep.DIR 是**关键缓解手段**，可减少 30% 以上的启动库存，对项目可行性至关重要。

#### （3）初步设计与运行建议

1. **优先保障高 plasma.Burn_Fraction**：因其同时降低 Startup Inventory 和 Required TBR，是提升氚经济性的根本路径。
2. **在 Burn_Fraction 受限时（如调试期、低功率运行），应最大化 tep.DIR**：通过优化氚提取系统（如提高渗透回收率、缩短循环延迟）来补偿燃烧效率不足。
3. **TBR 设计裕量应基于最低预期 Burn_Fraction**：因 Required TBR 对 tep.DIR 不敏感，不能依赖高 DIR 来降低对增殖包层性能的要求。
4. **启动策略可动态调整 DIR 目标**：在初期低 Burn_Fraction 阶段，应配置高效率氚回收系统以控制库存；进入高 Burn_Fraction 稳态后，可适当放宽对 DIR 的要求。

综上，tep.DIR 是调控氚库存的关键操作变量，但**不能替代对等离子体燃烧性能和增殖包层 TBR 的根本性要求**。系统设计应采取“高 Burn_Fraction + 高 DIR”双轨策略，以实现氚燃料循环的稳健性和经济性。
```

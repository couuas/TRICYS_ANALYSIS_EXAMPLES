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

# AI模型分析提示词 (deepseek-v3.1)

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

根据提供的敏感性分析数据，我将基于性能指标总表进行深度解读。分析聚焦于独立变量 `tep.DIR`（可能是氚提取系统的去污因子或类似参数）与背景参数 `plasma.Fueling_Efficiency` 和 `plasma.Burn_Fraction` 的交互作用，以及对性能指标 `Startup_Inventory` 和 `Required_TBR` 的影响。

### 1. 全局敏感性分析
#### 性能指标总体趋势
- **Startup_Inventory (启动库存)**：该指标对 `tep.DIR` 的变化高度敏感。随着 `tep.DIR` 从 0.1 增加到 0.8（即去污能力增强），启动库存显著减少。例如，在默认背景参数（`plasma.Fueling_Efficiency=0.5`, `plasma.Burn_Fraction=0.05`）下：
  - `tep.DIR=0.1` 时，启动库存为 4.9 kg。
  - `tep.DIR=0.8` 时，启动库存降至 3.51 kg，降幅约 28.4%。
  这种下降趋势在所有背景参数组合下均一致，表明提高 `tep.DIR` 可有效降低系统对初始氚库存的需求。

- **Required_TBR (所需氚增殖比)**：该指标对 `tep.DIR` 的变化相对不敏感。在大多数情况下，`Required_TBR` 的值基本稳定在 1.02-1.05 范围内，仅在小数点后第三或第四位有微小变化。例如，在默认背景参数下，`Required_TBR` 恒为 1.0234，即使 `tep.DIR` 从 0.1 变化到 0.8。这表明 `tep.DIR` 的调整对满足库存平衡所需的 TBR 影响极小，系统对 TBR 的要求主要由等离子体燃烧参数（如 `Burn_Fraction`）决定。

**敏感性排序**：
- 最敏感的性能指标：**Startup_Inventory**。它对 `tep.DIR` 的变化响应强烈（线性下降趋势）。
- 最不敏感的性能指标：**Required_TBR**。它对 `tep.DIR` 的变化几乎无响应（变化幅度 <0.01）。

### 2. 交互效应分析
独立变量 `tep.DIR` 与背景参数 `plasma.Fueling_Efficiency`（此处固定为 0.5）和 `plasma.Burn_Fraction` 存在显著交互作用，主要体现在 `Startup_Inventory` 和 `Required_TBR` 上。

#### 对 Startup_Inventory 的交互效应：
- **与 `plasma.Burn_Fraction` 的交互**：`Burn_Fraction` 越高，启动库存越低，且 `tep.DIR` 的优化效果更明显。
  - 例如，当 `Burn_Fraction=0.02`（低燃烧率）时，`tep.DIR` 从 0.1 到 0.8 使库存从 9.63 kg 降至 6.1 kg（降幅 36.7%）。
  - 当 `Burn_Fraction=0.1`（高燃烧率）时，库存从 3.32 kg 降至 2.65 kg（降幅 20.2%）。
  这表明在低燃烧率场景下，提高 `tep.DIR` 对减少库存的收益更大；而在高燃烧率下，收益相对减弱。

- **与 `plasma.Fueling_Efficiency` 的交互**：本分析中 `Fueling_Efficiency` 固定为 0.5，因此无法直接评估其交互效应。但根据数据趋势，若 `Fueling_Efficiency` 变化，可能会进一步调制 `tep.DIR` 的影响（例如，低 fueling 效率可能放大 `tep.DIR` 的重要性）。

#### 对 Required_TBR 的交互效应：
- **与 `plasma.Burn_Fraction` 的交互**：`Burn_Fraction` 对 `Required_TBR` 的影响远大于 `tep.DIR`。
  - 当 `Burn_Fraction=0.02`（低燃烧率）时，`Required_TBR` 较高（~1.05），且 `tep.DIR` 的变化仅引起微小波动（如从 1.0547 到 1.0469）。
  - 当 `Burn_Fraction=0.1`（高燃烧率）时，`Required_TBR` 较低（~1.0156），且 `tep.DIR` 的影响更弱（几乎无变化）。
  这表明 `Required_TBR` 主要受等离子体燃烧物理的约束，而 `tep.DIR` 的优化对其贡献有限。

- **交互显著性**：`tep.DIR` 与 `Burn_Fraction` 的交互对 `Startup_Inventory` 是显著的（协同减少库存），但对 `Required_TBR` 不显著（TBR 需求由燃烧主导）。

### 3. 综合结论与优化建议
#### 综合影响：
- **利弊权衡**：
  - **利**：提高 `tep.DIR`（增强氚提取或去污能力）可显著降低启动氚库存，减轻外部氚供应压力，尤其适用于低燃烧率（`Burn_Fraction <0.05`）或低 fueling 效率的场景。
  - **弊**：`tep.DIR` 的提高可能带来工程复杂性（如更高效的提取系统）、能耗增加或成本上升，且对 TBR 需求（`Required_TBR`）的优化作用微弱。系统仍需依靠高 TBR 设计（>1.02）来满足库存平衡。

#### 运行优化建议：
1. **对于库存约束严格的场景**（如初始氚稀缺）：优先优化 `tep.DIR`，将其设置为较高值（如 0.6-0.8），可减少库存需求 20-30%。同时，结合提高 `Burn_Fraction`（如至 0.08-0.1）可进一步降低库存。
2. **对于 TBR 约束严格的场景**（如包层设计局限）：`tep.DIR` 的调整几乎无助于降低 TBR 要求。应重点优化等离子体参数（如提高 `Burn_Fraction` 或 `Fueling_Efficiency`）来减少 `Required_TBR`。
3. **系统协同设计**：在低燃烧率运行时（如 `Burn_Fraction=0.02`），`tep.DIR` 的边际收益最大，可投资于高效提取技术；在高燃烧率运行时（如 `Burn_Fraction=0.1`），`tep.DIR` 的收益递减，可适当降低其性能以节省成本。

**总结**：`tep.DIR` 是降低启动库存的关键杠杆，但与等离子体燃烧参数存在强交互作用；而 TBR 需求主要由燃烧物理决定，对 `tep.DIR` 不敏感。系统设计需根据具体约束（库存 vs. TBR）权衡焦点参数。
```

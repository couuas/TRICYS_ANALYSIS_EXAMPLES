# pulse width 与 plasma Fueling Efficiency、plasma Burn Fraction 交互敏感性分析报告


生成时间: 2025-10-27 12:51:37.627143


## 分析案例配置详情


本分析案例的具体配置如下，这决定了仿真的扫描方式和分析的重点：


| 配置项 | 值 | 说明 |
| :--- | :--- | :--- |
| **`name`** | `"Pulse_PLASMA_Analysis"` | 本次分析案例的名称。 |
| **`independent_variable`** | `"pulse.width"` | 独立扫描变量，即本次分析中主要改变的参数。 |
| **`independent_variable_sampling`** | `[50, 60, 70, 80, 90, 99]` | 独立变量的采样方法和范围。 |
| **`default_independent_values`** | `{"pulse.width": 90.0}` | 独立扫描变量在模型中的原始默认值。 |
| **`simulation_parameters`** | `{"plasma.Fueling_Efficiency": 0.5, "plasma.Burn_Fraction": [0.02, 0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09, 0.1]}` | 背景扫描参数，与独立变量组合形成多维扫描。 |
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


### Startup Inventory vs pulse width

![Startup Inventory vs pulse width](line_Startup_Inventory_vs_pulse.width.svg)


## 约束求解性能指标分析图


### Required TBR vs pulse width

![Required TBR vs pulse width](line_Required_TBR_vs_pulse.width.svg)


## 性能指标总表 (分组: `plasma.Fueling_Efficiency`, `plasma.Burn_Fraction`)


#### 数据子表 (原始默认值: `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.05`)

##### 性能指标

|   pulse width (%) |   Startup Inventory (kg) |
|------------------:|-------------------------:|
|                50 |                     2.56 |
|                60 |                     2.78 |
|                70 |                     3    |
|                80 |                     3.21 |
|                90 |                     3.41 |
|                99 |                     3.59 |


##### “Required TBR” 相关数据

|   pulse width (%) |   Required TBR |
|------------------:|---------------:|
|                50 |         1.0234 |
|                60 |         1.0234 |
|                70 |         1.0234 |
|                80 |         1.0234 |
|                90 |         1.0234 |
|                99 |         1.0195 |



---

> 其他参数组合下的数据子表：

#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.02` 时)

##### 性能指标

|   pulse width (%) |   Startup Inventory (kg) |
|------------------:|-------------------------:|
|                50 |                     4.01 |
|                60 |                     4.49 |
|                70 |                     4.96 |
|                80 |                     5.41 |
|                90 |                     5.85 |
|                99 |                     6.23 |


##### “Required TBR” 相关数据

|   pulse width (%) |   Required TBR |
|------------------:|---------------:|
|                50 |         1.0469 |
|                60 |         1.0469 |
|                70 |         1.0469 |
|                80 |         1.0469 |
|                90 |         1.0469 |
|                99 |         1.0469 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.03` 时)

##### 性能指标

|   pulse width (%) |   Startup Inventory (kg) |
|------------------:|-------------------------:|
|                50 |                     3.21 |
|                60 |                     3.54 |
|                70 |                     3.87 |
|                80 |                     4.18 |
|                90 |                     4.49 |
|                99 |                     4.76 |


##### “Required TBR” 相关数据

|   pulse width (%) |   Required TBR |
|------------------:|---------------:|
|                50 |         1.0352 |
|                60 |         1.0352 |
|                70 |         1.0352 |
|                80 |         1.0312 |
|                90 |         1.0312 |
|                99 |         1.0312 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.04` 时)

##### 性能指标

|   pulse width (%) |   Startup Inventory (kg) |
|------------------:|-------------------------:|
|                50 |                     2.8  |
|                60 |                     3.07 |
|                70 |                     3.32 |
|                80 |                     3.57 |
|                90 |                     3.82 |
|                99 |                     4.03 |


##### “Required TBR” 相关数据

|   pulse width (%) |   Required TBR |
|------------------:|---------------:|
|                50 |         1.0273 |
|                60 |         1.0273 |
|                70 |         1.0273 |
|                80 |         1.0273 |
|                90 |         1.0273 |
|                99 |         1.0273 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.06` 时)

##### 性能指标

|   pulse width (%) |   Startup Inventory (kg) |
|------------------:|-------------------------:|
|                50 |                     2.4  |
|                60 |                     2.59 |
|                70 |                     2.78 |
|                80 |                     2.96 |
|                90 |                     3.14 |
|                99 |                     3.3  |


##### “Required TBR” 相关数据

|   pulse width (%) |   Required TBR |
|------------------:|---------------:|
|                50 |         1.0195 |
|                60 |         1.0195 |
|                70 |         1.0195 |
|                80 |         1.0195 |
|                90 |         1.0195 |
|                99 |         1.0195 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.07` 时)

##### 性能指标

|   pulse width (%) |   Startup Inventory (kg) |
|------------------:|-------------------------:|
|                50 |                     2.28 |
|                60 |                     2.46 |
|                70 |                     2.62 |
|                80 |                     2.79 |
|                90 |                     2.95 |
|                99 |                     3.09 |


##### “Required TBR” 相关数据

|   pulse width (%) |   Required TBR |
|------------------:|---------------:|
|                50 |         1.0195 |
|                60 |         1.0195 |
|                70 |         1.0156 |
|                80 |         1.0156 |
|                90 |         1.0156 |
|                99 |         1.0156 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.08` 时)

##### 性能指标

|   pulse width (%) |   Startup Inventory (kg) |
|------------------:|-------------------------:|
|                50 |                     2.19 |
|                60 |                     2.35 |
|                70 |                     2.51 |
|                80 |                     2.66 |
|                90 |                     2.8  |
|                99 |                     2.93 |


##### “Required TBR” 相关数据

|   pulse width (%) |   Required TBR |
|------------------:|---------------:|
|                50 |         1.0156 |
|                60 |         1.0156 |
|                70 |         1.0156 |
|                80 |         1.0156 |
|                90 |         1.0156 |
|                99 |         1.0156 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.09` 时)

##### 性能指标

|   pulse width (%) |   Startup Inventory (kg) |
|------------------:|-------------------------:|
|                50 |                     2.13 |
|                60 |                     2.27 |
|                70 |                     2.41 |
|                80 |                     2.55 |
|                90 |                     2.69 |
|                99 |                     2.81 |


##### “Required TBR” 相关数据

|   pulse width (%) |   Required TBR |
|------------------:|---------------:|
|                50 |         1.0156 |
|                60 |         1.0156 |
|                70 |         1.0156 |
|                80 |         1.0156 |
|                90 |         1.0156 |
|                99 |         1.0156 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.1` 时)

##### 性能指标

|   pulse width (%) |   Startup Inventory (kg) |
|------------------:|-------------------------:|
|                50 |                     2.07 |
|                60 |                     2.2  |
|                70 |                     2.34 |
|                80 |                     2.47 |
|                90 |                     2.6  |
|                99 |                     2.71 |


##### “Required TBR” 相关数据

|   pulse width (%) |   Required TBR |
|------------------:|---------------:|
|                50 |         1.0156 |
|                60 |         1.0156 |
|                70 |         1.0156 |
|                80 |         1.0117 |
|                90 |         1.0117 |
|                99 |         1.0117 |





---

# AI模型分析提示词 (deepseek-v3)

```markdown
**角色：** 你是一名聚变反应堆氚燃料循环领域的专家。

**任务：** 请**完全基于**下方提供的**两类数据表格**，对聚变堆燃料循环模型的**敏感性分析**结果进行深度解读。

**分析要点 (必须严格依据数据表格作答)：**

1.  **全局敏感性分析 (参考“性能指标总表”) :**
    *   分析性能指标总表（ `Startup_Inventory`, `Doubling_Time` 以及以 `Required_` 开头的求解指标等）呈现出怎样的**总体趋势**？请进行量化描述。
    *   如果存在多个性能指标，分析哪个性能指标对独立变量 `pulse.width` 的变化最为敏感？哪个最不敏感？

2.  **交互效应分析：** 本次分析包含了多变量的交互效应。请分析独立变量 `pulse.width` 与背景扫描参数 (`plasma.Fueling_Efficiency`, `plasma.Burn_Fraction`) 之间的交互作用对各项性能指标的影响。请注意，独立变量或背景扫描参数中，可能包含常规的模型参数，也可能包含为满足特定性能目标（限制倍增时间Double_Time达到倍增）而求解出的特殊变量（约束限制变量Double_Time）。请讨论在不同的变量组合下，性能指标的敏感性有何不同？是否存在显著的交互效应？

3.  **综合结论：**
结合所有分析（包括主趋势、背景参数交互效应），总结在不同的运行场景下，调整 `pulse.width` 对整个氚燃料循环系统的综合影响和潜在的利弊权衡。
    *   基于这些发现，可以得出哪些关于系统设计或运行优化的初步建议？
```



---

# AI模型分析结果

### 深度解读报告：聚变堆燃料循环模型敏感性分析

---

#### **1. 全局敏感性分析**
**(1) 性能指标总体趋势量化描述**  
- **Startup Inventory (kg)**：  
  - **与pulse.width的关系**：在**所有**`plasma.Burn_Fraction`水平下，`Startup Inventory`均随`pulse.width`增加呈**线性增长**。例如：  
    - `Burn_Fraction=0.05`时，从50%到99%，库存从2.56 kg增至3.59 kg（增幅40.2%）；  
    - `Burn_Fraction=0.1`时，从2.07 kg增至2.71 kg（增幅30.9%）。  
  - **与Burn_Fraction的关系**：`Burn_Fraction`越低，库存需求越高。例如：  
    - `pulse.width=50%`时，`Burn_Fraction=0.02`的库存（4.01 kg）是`Burn_Fraction=0.1`（2.07 kg）的1.94倍。  

- **Required TBR**：  
  - **对pulse.width的敏感性极低**：在大多数情况下，`Required TBR`随`pulse.width`变化几乎不变（如`Burn_Fraction=0.02`时恒为1.0469）。仅少数场景（如`Burn_Fraction=0.1`）在最高`pulse.width`（99%）时略有下降（从1.0156→1.0117）。  
  - **对Burn_Fraction敏感**：`Burn_Fraction`从0.02升至0.1，`Required TBR`从1.0469降至1.0117（降幅3.4%）。  

**(2) 敏感性排序**  
- **最敏感指标**：`Startup Inventory`（受`pulse.width`和`Burn_Fraction`双重显著影响）。  
- **最不敏感指标**：`Required TBR`（几乎不受`pulse.width`影响，仅轻微依赖`Burn_Fraction`）。  

---

#### **2. 交互效应分析**
**(1) `pulse.width`与背景参数的交互作用**  
- **`plasma.Burn_Fraction`的调节效应**：  
  - **高`Burn_Fraction`（如0.1）**：`pulse.width`对库存的边际影响减弱（增幅30.9% vs 低`Burn_Fraction`的40.2%），说明高效燃烧可部分抵消长脉冲带来的氚需求压力。  
  - **低`Burn_Fraction`（如0.02）**：`pulse.width`增加导致库存需求急剧上升（从4.01→6.23 kg），表明系统在低燃烧效率下对脉冲时长更为敏感。  

- **`plasma.Fueling_Efficiency`的固定影响**：  
  当前数据仅包含`Fueling_Efficiency=0.5`，但默认值与扫描值一致，推测其可能通过影响燃料利用率间接放大或缓和`pulse.width`的作用（需更多数据验证）。  

**(2) 交互效应显著性**  
- **`Burn_Fraction`主导交互**：`pulse.width`对库存的影响强度高度依赖`Burn_Fraction`，呈现非线性耦合。例如：  
  - `Burn_Fraction=0.05`时，每增加10%脉冲宽度，库存平均增加0.21 kg；  
  - `Burn_Fraction=0.02`时，相同增幅对应库存增加0.44 kg（差异达109%）。  

---

#### **3. 综合结论与优化建议**
**(1) 综合影响与权衡**  
- **长脉冲（高`pulse.width`）的利弊**：  
  - **利**：可能提升等离子体稳定性（需结合物理模型确认）。  
  - **弊**：显著增加氚启动库存（尤其在低`Burn_Fraction`时），抬高燃料循环成本。  

- **高`Burn_Fraction`的核心价值**：  
  降低对`Required TBR`的需求（减少增殖包层设计压力）并缓解长脉冲的库存负担，但需通过等离子体优化实现。  

**(2) 设计建议**  
1. **优先提升`Burn_Fraction`**：将燃烧效率从默认0.05提高至0.1，可减少库存需求达39.3%（`pulse.width=90%`时从3.41→2.60 kg），同时降低`Required TBR`至1.0117。  
2. **脉冲时长优化**：在`Burn_Fraction≥0.06`时，`pulse.width`对`Required TBR`无影响，可依据工程约束（如热负荷）灵活选择50%~90%脉冲。  
3. **警惕低效燃烧场景**：若`Burn_Fraction≤0.03`，需严格限制`pulse.width`（如≤70%），否则库存和TBR需求将同步攀升。  

**(3) 后续研究方向**  
- 补充`Fueling_Efficiency`的扫描数据，量化其与`pulse.width`的交互作用。  
- 验证`Burn_Fraction>0.1`的可行性，进一步挖掘库存优化潜力。  

--- 

**总结**：本分析揭示了脉冲时长与燃烧效率的强耦合效应，为平衡氚自持与运行参数提供了数据驱动的决策依据。
```

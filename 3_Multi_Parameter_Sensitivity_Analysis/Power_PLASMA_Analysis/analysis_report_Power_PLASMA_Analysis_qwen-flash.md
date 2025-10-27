# pulse power 与 plasma Fueling Efficiency、plasma Burn Fraction 交互敏感性分析报告


生成时间: 2025-10-27 13:00:36.125458


## 分析案例配置详情


本分析案例的具体配置如下，这决定了仿真的扫描方式和分析的重点：


| 配置项 | 值 | 说明 |
| :--- | :--- | :--- |
| **`name`** | `"Power_PLASMA_Analysis"` | 本次分析案例的名称。 |
| **`independent_variable`** | `"pulse.power"` | 独立扫描变量，即本次分析中主要改变的参数。 |
| **`independent_variable_sampling`** | `[100, 500, 1000, 1500, 2000, 2500, 3000]` | 独立变量的采样方法和范围。 |
| **`default_independent_values`** | `{"pulse.power": 1500.0}` | 独立扫描变量在模型中的原始默认值。 |
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


### Startup Inventory vs pulse power

![Startup Inventory vs pulse power](line_Startup_Inventory_vs_pulse.power.svg)


## 约束求解性能指标分析图


### Required TBR vs pulse power

![Required TBR vs pulse power](line_Required_TBR_vs_pulse.power.svg)


## 性能指标总表 (分组: `plasma.Fueling_Efficiency`, `plasma.Burn_Fraction`)


#### 数据子表 (原始默认值: `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.05`)

##### 性能指标

|   pulse power (MW) |   Startup Inventory (kg) |
|-------------------:|-------------------------:|
|                100 |                     1.51 |
|                500 |                     2.05 |
|               1000 |                     2.73 |
|               1500 |                     3.41 |
|               2000 |                     4.09 |
|               2500 |                     4.77 |
|               3000 |                     5.45 |


##### “Required TBR” 相关数据

|   pulse power (MW) |   Required TBR |
|-------------------:|---------------:|
|                100 |         1.0586 |
|                500 |         1.0273 |
|               1000 |         1.0234 |
|               1500 |         1.0234 |
|               2000 |         1.0195 |
|               2500 |         1.0195 |
|               3000 |         1.0195 |



---

> 其他参数组合下的数据子表：

#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.02` 时)

##### 性能指标

|   pulse power (MW) |   Startup Inventory (kg) |
|-------------------:|-------------------------:|
|                100 |                     1.68 |
|                500 |                     2.87 |
|               1000 |                     4.36 |
|               1500 |                     5.85 |
|               2000 |                     7.33 |
|               2500 |                     8.82 |
|               3000 |                    10.31 |


##### “Required TBR” 相关数据

|   pulse power (MW) |   Required TBR |
|-------------------:|---------------:|
|                100 |         1.082  |
|                500 |         1.0508 |
|               1000 |         1.0469 |
|               1500 |         1.0469 |
|               2000 |         1.0469 |
|               2500 |         1.0469 |
|               3000 |         1.0469 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.03` 时)

##### 性能指标

|   pulse power (MW) |   Startup Inventory (kg) |
|-------------------:|-------------------------:|
|                100 |                     1.59 |
|                500 |                     2.41 |
|               1000 |                     3.45 |
|               1500 |                     4.49 |
|               2000 |                     5.53 |
|               2500 |                     6.57 |
|               3000 |                     7.6  |


##### “Required TBR” 相关数据

|   pulse power (MW) |   Required TBR |
|-------------------:|---------------:|
|                100 |         1.0703 |
|                500 |         1.0391 |
|               1000 |         1.0352 |
|               1500 |         1.0312 |
|               2000 |         1.0312 |
|               2500 |         1.0312 |
|               3000 |         1.0312 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.04` 时)

##### 性能指标

|   pulse power (MW) |   Startup Inventory (kg) |
|-------------------:|-------------------------:|
|                100 |                     1.54 |
|                500 |                     2.19 |
|               1000 |                     3    |
|               1500 |                     3.82 |
|               2000 |                     4.63 |
|               2500 |                     5.44 |
|               3000 |                     6.26 |


##### “Required TBR” 相关数据

|   pulse power (MW) |   Required TBR |
|-------------------:|---------------:|
|                100 |         1.0625 |
|                500 |         1.0312 |
|               1000 |         1.0273 |
|               1500 |         1.0273 |
|               2000 |         1.0234 |
|               2500 |         1.0234 |
|               3000 |         1.0234 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.06` 时)

##### 性能指标

|   pulse power (MW) |   Startup Inventory (kg) |
|-------------------:|-------------------------:|
|                100 |                     1.49 |
|                500 |                     1.95 |
|               1000 |                     2.55 |
|               1500 |                     3.14 |
|               2000 |                     3.73 |
|               2500 |                     4.32 |
|               3000 |                     4.92 |


##### “Required TBR” 相关数据

|   pulse power (MW) |   Required TBR |
|-------------------:|---------------:|
|                100 |         1.0547 |
|                500 |         1.0234 |
|               1000 |         1.0195 |
|               1500 |         1.0195 |
|               2000 |         1.0195 |
|               2500 |         1.0195 |
|               3000 |         1.0156 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.07` 时)

##### 性能指标

|   pulse power (MW) |   Startup Inventory (kg) |
|-------------------:|-------------------------:|
|                100 |                     1.48 |
|                500 |                     1.89 |
|               1000 |                     2.42 |
|               1500 |                     2.95 |
|               2000 |                     3.48 |
|               2500 |                     4.01 |
|               3000 |                     4.53 |


##### “Required TBR” 相关数据

|   pulse power (MW) |   Required TBR |
|-------------------:|---------------:|
|                100 |         1.0547 |
|                500 |         1.0234 |
|               1000 |         1.0195 |
|               1500 |         1.0156 |
|               2000 |         1.0156 |
|               2500 |         1.0156 |
|               3000 |         1.0156 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.08` 时)

##### 性能指标

|   pulse power (MW) |   Startup Inventory (kg) |
|-------------------:|-------------------------:|
|                100 |                     1.47 |
|                500 |                     1.83 |
|               1000 |                     2.32 |
|               1500 |                     2.8  |
|               2000 |                     3.28 |
|               2500 |                     3.77 |
|               3000 |                     4.25 |


##### “Required TBR” 相关数据

|   pulse power (MW) |   Required TBR |
|-------------------:|---------------:|
|                100 |         1.0508 |
|                500 |         1.0195 |
|               1000 |         1.0156 |
|               1500 |         1.0156 |
|               2000 |         1.0156 |
|               2500 |         1.0156 |
|               3000 |         1.0156 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.09` 时)

##### 性能指标

|   pulse power (MW) |   Startup Inventory (kg) |
|-------------------:|-------------------------:|
|                100 |                     1.46 |
|                500 |                     1.79 |
|               1000 |                     2.24 |
|               1500 |                     2.69 |
|               2000 |                     3.13 |
|               2500 |                     3.58 |
|               3000 |                     4.02 |


##### “Required TBR” 相关数据

|   pulse power (MW) |   Required TBR |
|-------------------:|---------------:|
|                100 |         1.0508 |
|                500 |         1.0195 |
|               1000 |         1.0156 |
|               1500 |         1.0156 |
|               2000 |         1.0117 |
|               2500 |         1.0117 |
|               3000 |         1.0117 |




#### 数据子表 (当 `plasma.Fueling_Efficiency=0.5` & `plasma.Burn_Fraction=0.1` 时)

##### 性能指标

|   pulse power (MW) |   Startup Inventory (kg) |
|-------------------:|-------------------------:|
|                100 |                     1.45 |
|                500 |                     1.76 |
|               1000 |                     2.18 |
|               1500 |                     2.6  |
|               2000 |                     3.01 |
|               2500 |                     3.43 |
|               3000 |                     3.85 |


##### “Required TBR” 相关数据

|   pulse power (MW) |   Required TBR |
|-------------------:|---------------:|
|                100 |         1.0508 |
|                500 |         1.0195 |
|               1000 |         1.0156 |
|               1500 |         1.0117 |
|               2000 |         1.0117 |
|               2500 |         1.0117 |
|               3000 |         1.0117 |





---

# AI模型分析提示词 (qwen-flash)

```markdown
**角色：** 你是一名聚变反应堆氚燃料循环领域的专家。

**任务：** 请**完全基于**下方提供的**两类数据表格**，对聚变堆燃料循环模型的**敏感性分析**结果进行深度解读。

**分析要点 (必须严格依据数据表格作答)：**

1.  **全局敏感性分析 (参考“性能指标总表”) :**
    *   分析性能指标总表（ `Startup_Inventory`, `Doubling_Time` 以及以 `Required_` 开头的求解指标等）呈现出怎样的**总体趋势**？请进行量化描述。
    *   如果存在多个性能指标，分析哪个性能指标对独立变量 `pulse.power` 的变化最为敏感？哪个最不敏感？

2.  **交互效应分析：** 本次分析包含了多变量的交互效应。请分析独立变量 `pulse.power` 与背景扫描参数 (`plasma.Fueling_Efficiency`, `plasma.Burn_Fraction`) 之间的交互作用对各项性能指标的影响。请注意，独立变量或背景扫描参数中，可能包含常规的模型参数，也可能包含为满足特定性能目标（限制倍增时间Double_Time达到倍增）而求解出的特殊变量（约束限制变量Double_Time）。请讨论在不同的变量组合下，性能指标的敏感性有何不同？是否存在显著的交互效应？

3.  **综合结论：**
结合所有分析（包括主趋势、背景参数交互效应），总结在不同的运行场景下，调整 `pulse.power` 对整个氚燃料循环系统的综合影响和潜在的利弊权衡。
    *   基于这些发现，可以得出哪些关于系统设计或运行优化的初步建议？
```



---

# AI模型分析结果

### **聚变堆氚燃料循环模型敏感性分析深度解读**

---

#### **1. 全局敏感性分析：性能指标总体趋势与变量敏感性量化**

**（1）性能指标的总体趋势分析**

基于“性能指标总表”中所有数据子表的系统性比较，可以得出以下**量化趋势**：

- **`Startup_Inventory`（初始氚库存量）随 `pulse.power` 增加而单调上升**。  
  在所有背景参数组合下，当 `pulse.power` 从 100 MW 增至 3000 MW 时，`Startup_Inventory` 均呈现持续增长。其增长率在不同 `plasma.Burn_Fraction` 条件下存在显著差异：
  - 当 `plasma.Burn_Fraction = 0.02` 时，`Startup_Inventory` 从 1.68 kg 增至 10.31 kg，增幅达 **513.7%**；
  - 当 `plasma.Burn_Fraction = 0.1` 时，增幅为 **130.4%**（1.45 → 3.85 kg）。
  - **平均增幅为 250% 以上**，表明高脉冲功率对初始库存需求具有强烈的正向驱动作用。

- **`Required_TBR`（所需氚增殖比）随 `pulse.power` 增加而下降，并趋于稳定**。  
  所有数据子表显示，`Required_TBR` 在低功率段（< 1000 MW）快速下降，随后进入平台期：
  - 以 `plasma.Burn_Fraction = 0.02` 为例，`Required_TBR` 从 1.082 降至 1.0469（降幅约 3.2%），且在 1000 MW 后不再变化；
  - 以 `plasma.Burn_Fraction = 0.1` 为例，`Required_TBR` 从 1.0508 降至 1.0117（降幅约 3.7%），并在 1500 MW 后稳定；
  - **最大降幅出现在 `Burn_Fraction=0.02` 时，为 3.2%**，最小降幅为 `Burn_Fraction=0.09` 时的 3.7%（实际更小，因起始值更高）；
  - 所有组合中，`Required_TBR` 在 **≥1500 MW** 后均达到或接近最终稳定值，表明系统已进入“饱和响应”状态。

> ✅ **结论**：`Startup_Inventory` 对 `pulse.power` 呈强正相关，且非线性增长；`Required_TBR` 呈强负相关，但存在明显的饱和阈值（约 1500 MW），超过后基本不再改善。

**（2）各性能指标对 `pulse.power` 的敏感性排序**

- **最敏感指标：`Startup_Inventory`**  
  —— 其变化幅度最大，且对功率变化的响应最剧烈。例如，在 `Burn_Fraction=0.02` 时，`Startup_Inventory` 在 3000 MW 下比 100 MW 高出 **8.63 kg**，相对增量高达 513.7%。即使在最优燃烧条件下（`Burn_Fraction=0.1`），也增加 2.4 kg（165.5%）。  
  —— 敏感性系数（ΔY/ΔX）在多数组合中 > 0.001 kg/MW，最高可达 **0.0030 kg/MW**（`Burn_Fraction=0.02`）。

- **次敏感指标：`Required_TBR`**  
  —— 其变化主要集中在 100–1500 MW 区间，之后趋于平坦。整体变化范围为 **0.0037 至 0.036**（即从 1.0508 降至 1.0117），但仅在前半段敏感。  
  —— 敏感性系数在 100–1000 MW 区间可达 **-0.00003 至 -0.00006 /MW**，但在 ≥1500 MW 后趋近于零。

- **最不敏感指标：无（所有指标均有响应）**  
  —— 但若论“边际效应衰减速度”，则 `Required_TBR` 的敏感性衰减速率最快，说明其对功率提升的收益递减最为明显。

> ✅ **结论**：`Startup_Inventory` 是对 `pulse.power` 变化最敏感的性能指标，其响应强度远超 `Required_TBR`，后者虽初始敏感，但迅速进入平台区。

---

#### **2. 交互效应分析：`pulse.power` 与 `plasma.Fueling_Efficiency`、`plasma.Burn_Fraction` 的协同影响**

本分析中，`plasma.Fueling_Efficiency` 固定为 0.5，因此**无此变量的交互效应**。但 `plasma.Burn_Fraction` 作为背景扫描参数，与 `pulse.power` 构成了关键的多维交互关系。分析如下：

##### **（1）`plasma.Burn_Fraction` 对 `Startup_Inventory` 的主导作用**

- 在相同 `pulse.power` 下，`Startup_Inventory` 随 `plasma.Burn_Fraction` 增加而**显著降低**：
  - 以 `pulse.power = 100 MW` 为例：
    - `Burn_Fraction = 0.02`：1.68 kg
    - `Burn_Fraction = 0.1`：1.45 kg
    - **降幅达 13.7%**
  - 以 `pulse.power = 3000 MW` 为例：
    - `Burn_Fraction = 0.02`：10.31 kg
    - `Burn_Fraction = 0.1`：3.85 kg
    - **降幅达 62.6%**

> 🔍 **关键发现**：`Burn_Fraction` 提升能极大缓解高功率下的库存压力。这种效应在高功率下尤为突出——**高燃烧效率可抵消高功率带来的库存增长需求**。

##### **（2）`plasma.Burn_Fraction` 对 `Required_TBR` 的显著优化能力**

- `Required_TBR` 随 `Burn_Fraction` 增加而**系统性降低**，且该趋势在所有功率水平上保持一致：
  - 在 `pulse.power = 100 MW` 时：
    - `Burn_Fraction = 0.02` → 1.082
    - `Burn_Fraction = 0.1` → 1.0508
    - **降低 2.9%**
  - 在 `pulse.power = 3000 MW` 时：
    - `Burn_Fraction = 0.02` → 1.0469
    - `Burn_Fraction = 0.1` → 1.0117
    - **降低 3.36%**

> 🔍 **关键发现**：`Burn_Fraction` 的提升直接降低了系统对氚增殖比的要求，尤其在高功率下，其优化潜力更大。这表明：**高燃烧效率可有效补偿高功率运行带来的氚损失风险**。

##### **（3）交互效应总结：功率与燃烧效率的互补关系**

- 存在**显著的正向交互效应**：  
  `pulse.power ↑` 会**加剧**对 `Startup_Inventory` 的需求，但 `plasma.Burn_Fraction ↑` 可**有效抑制**这一增长趋势。  
  二者共同作用下，`Startup_Inventory` 的增长率被显著削弱。例如：
  - 当 `Burn_Fraction = 0.02` 时，`Startup_Inventory` 随功率增长呈近似指数上升；
  - 当 `Burn_Fraction = 0.1` 时，其增长趋于线性甚至平缓。

- `Required_TBR` 的改善也依赖于 `Burn_Fraction`。在相同功率下，`Burn_Fraction` 越高，`Required_TBR` 越低，且其**收敛速度更快**。例如：
  - 在 `Burn_Fraction = 0.02` 时，`Required_TBR` 在 1000 MW 后稳定；
  - 在 `Burn_Fraction = 0.1` 时，`Required_TBR` 在 1500 MW 后稳定，且最终值更低。

> ✅ **结论**：`plasma.Burn_Fraction` 与 `pulse.power` 之间存在**强互补交互效应**。高燃烧效率可部分甚至完全抵消高脉冲功率带来的负面效应，是实现高功率运行下系统可持续性的关键调控手段。

---

#### **3. 综合结论与设计优化建议**

##### **（1）系统综合影响评估**

| 运行场景 | `pulse.power` | `plasma.Burn_Fraction` | 影响特征 |
|--------|-------------|----------------------|--------|
| 低效运行 | 低（100 MW） | 0.02 | 初始库存高（1.68 kg），TBR要求高（1.082），系统难启动 |
| 高效运行 | 高（3000 MW） | 0.1 | 初始库存仅 3.85 kg，TBR要求低至 1.0117，系统可持续性强 |

> 📌 **核心权衡**：  
> - **高 `pulse.power`** → 增加初始库存需求（不利），但降低 `Required_TBR`（有利）；  
> - **高 `plasma.Burn_Fraction`** → 显著降低初始库存与 TBR 要求（双重利好），并有效缓解高功率的负面影响。

##### **（2）设计与运行优化建议**

1. **优先提升 `plasma.Burn_Fraction`，而非盲目提高 `pulse.power`**  
   —— 数据表明，将 `Burn_Fraction` 从 0.02 提升至 0.1，可在 **3000 MW** 下使 `Startup_Inventory` 从 10.31 kg 降至 3.85 kg（降幅 62.6%），同时 `Required_TBR` 从 1.0469 降至 1.0117。  
   —— **建议将燃烧效率作为首要优化目标**，通过改进等离子体约束、减少湍流损失、优化加热方式等手段实现。

2. **高功率运行需配套高燃烧效率才能经济可行**  
   —— 若 `Burn_Fraction` 保持在 0.02 水平，即使功率提升至 3000 MW，`Startup_Inventory` 需达 10.31 kg，远超常规储库容量。  
   —— **建议设定运行边界：只有当 `Burn_Fraction ≥ 0.06` 时，才考虑 `pulse.power ≥ 2000 MW` 的配置。**

3. **功率提升存在“边际收益递减”点（约 1500 MW）**  
   —— `Required_TBR` 在 1500 MW 后基本不变，意味着继续提升功率无法进一步改善氚自持能力。  
   —— **建议将运行功率控制在 1500–2000 MW 区间，以平衡成本与效益。**

4. **系统设计应具备“动态匹配”能力**  
   —— 由于 `Burn_Fraction` 对系统性能影响巨大，建议在控制系统中集成实时反馈机制，根据当前燃烧效率动态调整 `pulse.power`，避免在低效状态下强行高功率运行。

---

### ✅ **最终总结**

本次敏感性分析揭示了聚变堆氚燃料循环系统的核心设计规律：  
> **高脉冲功率的运行潜力，必须由高燃烧效率来支撑。**  

- `Startup_Inventory` 对 `pulse.power` 敏感度最高，但可通过提升 `Burn_Fraction` 有效抑制；
- `Required_TBR` 的改善具有饱和特性，且对 `Burn_Fraction` 极为敏感；
- 两者之间存在显著的**正向交互效应**，构成系统可持续运行的关键杠杆。

**核心设计原则**：  
> **“效率优先，功率适配”** —— 不应追求极致功率，而应以燃烧效率为核心驱动力，构建高效、安全、可持续的氚燃料循环系统。
```

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

# AI模型分析提示词 (qwen-flash)

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

### **聚变堆氚燃料循环模型敏感性分析深度解读报告**

---

#### **1. 全局敏感性分析（基于“性能指标总表”）**

**（1）总体趋势量化描述：**

- **`Startup_Inventory`（启动库存量）**：
  - 随着 `pulse.width` 从 50 增加至 99，**所有数据子表中均呈现单调递增趋势**。
  - 在 `plasma.Burn_Fraction = 0.02` 时，增量最大：从 4.01 kg 增至 6.23 kg，**增长幅度达 55.4%**；
  - 在 `plasma.Burn_Fraction = 0.1` 时，增长最小：从 2.07 kg 增至 2.71 kg，**增长幅度为 30.9%**。
  - 整体上，`Startup_Inventory` 随 `pulse.width` 增大而显著上升，且其增长速率受 `plasma.Burn_Fraction` 显著影响。

- **`Required_TBR`（所需氚增殖比）**：
  - 在大多数情况下，`Required_TBR` 在 `pulse.width < 99` 时保持稳定，仅在 `pulse.width = 99` 时出现下降。
  - 当 `plasma.Burn_Fraction = 0.02` 时，`Required_TBR` 恒定为 1.0469，**对 `pulse.width` 无变化响应**；
  - 当 `plasma.Burn_Fraction ≥ 0.05` 时，`Required_TBR` 在 `pulse.width = 99` 时出现**首次下降**：从 1.0234 降至 1.0195（降幅 0.38%），并在更高 `Burn_Fraction` 下持续降低至 1.0117（`plasma.Burn_Fraction = 0.1`）。
  - 总体而言，`Required_TBR` 对 `pulse.width` 的变化**不敏感**，仅在高燃烧分数下于最大脉冲宽度处表现出微弱下降。

- **综合对比**：
  - `Startup_Inventory`：**强正相关**，随 `pulse.width` 增加而持续上升；
  - `Required_TBR`：**极弱非线性响应**，几乎不变，仅在特定条件下于末端略有下降。

**（2）敏感性排序：**

- **最敏感的性能指标**：**`Startup_Inventory`**
  - 理由：在所有参数组合下，其值随 `pulse.width` 增加而系统性、可量化地增加，且变化范围最大（如从 2.07 到 6.23），是唯一表现出**一致且显著趋势**的指标。
  
- **最不敏感的性能指标**：**`Required_TBR`**
  - 理由：在绝大多数配置中，其值在 `pulse.width` 变化范围内**完全不变**，仅在 `plasma.Burn_Fraction ≥ 0.05` 时于 `pulse.width = 99` 出现微小下降，且该变化并非单调或普遍，表明其对 `pulse.width` 的依赖极低。

> ✅ 结论：`Startup_Inventory` 是对 `pulse.width` 变化最敏感的指标；`Required_TBR` 几乎不受其影响。

---

#### **2. 交互效应分析：`pulse.width` 与 `plasma.Burn_Fraction` 之间的协同作用**

本分析通过固定 `plasma.Fueling_Efficiency = 0.5`，改变 `plasma.Burn_Fraction`，研究其与 `pulse.width` 的**多维交互效应**。关键发现如下：

##### **（1）`Startup_Inventory` 的交互特性：**

- **`plasma.Burn_Fraction` 越高，`Startup_Inventory` 的增长斜率越小**。
  - 当 `Burn_Fraction = 0.02`（最低）时，`Startup_Inventory` 从 4.01 增至 6.23，**每增加 10 单位脉冲宽度，平均增加约 0.222 kg**；
  - 当 `Burn_Fraction = 0.1`（最高）时，`Startup_Inventory` 从 2.07 增至 2.71，**每单位脉冲宽度增加约 0.064 kg**。
  - **即：`Burn_Fraction` 越高，`Startup_Inventory` 对 `pulse.width` 的敏感度越低**。

- **物理机制解释**：
  - 更高的 `Burn_Fraction` 意味着等离子体中氚的利用率更高，单位时间释放的能量更多，因此在相同脉冲宽度下能维持更高效的氚循环。
  - 这导致即使延长脉冲宽度，系统对初始库存的需求增幅减缓，形成“**边际效益递减**”效应。

##### **（2）`Required_TBR` 的交互特性：**

- **`Required_TBR` 的变化仅出现在 `plasma.Burn_Fraction ≥ 0.05` 时，且仅在 `pulse.width = 99` 处发生**。
  - 在 `Burn_Fraction = 0.05` 时，`Required_TBR` 从 1.0234 → 1.0195（下降 0.38%）；
  - 在 `Burn_Fraction = 0.07` 时，`Required_TBR` 在 `pulse.width = 70` 后首次下降至 1.0156；
  - 在 `Burn_Fraction = 0.1` 时，`Required_TBR` 在 `pulse.width = 80` 后降至 1.0117。
  - **关键发现**：`Required_TBR` 的下降**并非由 `pulse.width` 单独驱动**，而是**依赖于高 `Burn_Fraction` 条件下的阈值突破**。

- **交互机制解析**：
  - `Required_TBR` 是一个**约束求解目标**，其值由优化算法在满足 `sds.inventory` 限制下寻找最小 `bz.TBR`。
  - 当 `Burn_Fraction` 较低（如 ≤ 0.04）时，系统无法在 `pulse.width` 增加时进一步提升氚增殖效率，故 `Required_TBR` 保持恒定；
  - 当 `Burn_Fraction` 达到一定阈值（≥ 0.05），系统具备更高的自持能力，使得在长脉冲（尤其是 99）下，**可通过更低的 TBR 实现库存约束**，从而触发 `Required_TBR` 下降。
  - 因此，`pulse.width` 与 `Burn_Fraction` 存在**非线性协同效应**：只有当 `Burn_Fraction` 足够高时，延长 `pulse.width` 才能有效降低 `Required_TBR`。

> ✅ 结论：`plasma.Burn_Fraction` 与 `pulse.width` 之间存在**显著的负向交互效应**——高燃烧分数可**抑制**`Startup_Inventory` 的增长，并**激活**`Required_TBR` 的优化潜力。这表明二者不是独立变量，而是构成一个**性能优化的协同工作区**。

---

#### **3. 综合结论与设计优化建议**

结合全局趋势与交互效应，得出以下核心结论：

##### **（1）`pulse.width` 的影响具有双重性：**

- **正面效应**：
  - 在高 `Burn_Fraction` 条件下（≥ 0.05），延长脉冲宽度（如从 90 → 99）**可降低 `Required_TBR` 要求**，从而减轻增殖包层设计压力，提高系统经济性。
  - 适用于追求**高自持率与低增殖比需求**的先进聚变堆设计。

- **负面效应**：
  - 无论 `Burn_Fraction` 如何，延长脉冲宽度**必然增加 `Startup_Inventory`**，意味着需要更多的初始氚库存，这对新堆启动阶段构成**重大挑战**。
  - 尤其在低燃烧分数场景（如 `Burn_Fraction = 0.02`），`Startup_Inventory` 增幅高达 55%，严重制约系统启动可行性。

##### **（2）系统运行策略权衡：**

| 场景 | 推荐 `pulse.width` | 理由 |
|------|-------------------|------|
| **低燃烧效率（≤ 0.04）** | **不宜过长**（建议 ≤ 80） | `Startup_Inventory` 增长剧烈，而 `Required_TBR` 无改善，得不偿失。 |
| **中高燃烧效率（≥ 0.05）** | **可适度延长至 99** | 能实现 `Required_TBR` 下降，同时 `Startup_Inventory` 增长可控（< 30%）。 |

##### **（3）设计与运行优化建议：**

1. **优先提升 `plasma.Burn_Fraction`**：
   - 应将技术重点放在提升等离子体燃烧效率（如改进加热方式、磁场约束稳定性），以**打开 `pulse.width` 优化潜力的“开关”**。
   - 仅当 `Burn_Fraction ≥ 0.05` 时，延长脉冲宽度才具备实际价值。

2. **避免盲目延长脉冲宽度**：
   - 在未达到足够燃烧效率前，延长 `pulse.width` 会**加剧启动库存负担**，且无益于 `TBR` 优化，属于“无效投入”。

3. **采用分阶段运行策略**：
   - 初期使用较短脉冲（如 70–80）以控制 `Startup_Inventory`；
   - 待系统进入稳态并实现高燃烧效率后，逐步过渡至长脉冲（如 99），以释放 `Required_TBR` 优化空间。

4. **优化目标函数需耦合多指标**：
   - 单纯最小化 `Required_TBR` 可能忽视 `Startup_Inventory` 的约束；
   - 建议建立**加权综合目标函数**，平衡启动成本与长期增殖效率。

---

### ✅ **最终总结**

- `pulse.width` 对 `Startup_Inventory` 敏感，对 `Required_TBR` 几乎不敏感；
- `plasma.Burn_Fraction` 与 `pulse.width` 存在**强交互效应**：高燃烧分数是启用长脉冲优势的前提；
- **最优运行区间**存在于 `plasma.Burn_Fraction ≥ 0.05` 且 `pulse.width = 99`；
- **设计核心建议**：**先提升燃烧效率，再利用长脉冲实现系统优化**，避免“为长而长”的误区。

> 本分析揭示了聚变堆氚循环系统中“脉冲长度”并非孤立参数，其价值高度依赖于燃烧效率这一基础性能。未来设计应围绕“高效燃烧+合理脉冲”协同优化，方能实现经济可行的氚自持。
```

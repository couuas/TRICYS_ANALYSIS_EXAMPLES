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

# AI模型分析提示词 (qwen3-max)

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

作为聚变反应堆氚燃料循环领域的专家，我将严格依据所提供的数据表格，对“DoubleTime_PLASMA_Analysis”案例中关于 **plasma.Burn_Fraction** 的敏感性分析结果进行深度解读。所有结论均基于表格中的数值数据，不引入任何外部假设或图表信息。

---

### 1. 全局敏感性分析

本分析中，唯一的因变量为 **Required_TBR**（即为满足特定氚增殖目标所需的最小包层氚增殖比），其值随独立变量 **plasma.Burn_Fraction**（等离子体燃耗分数）变化，并在四种不同的 **Doubling_Time** 约束下（0.5年、1.0年、1.5年、2.0年，对应小时数分别为4380、8760、13140、17530）进行评估。

#### 总体趋势（量化描述）：

- **Required_TBR 随 Burn_Fraction 增加而单调下降**，但下降幅度逐渐减小，呈现**边际递减效应**。
  
  以 **Doubling_Time = 0.5年** 为例：
  - Burn_Fraction 从 0.02 增至 0.05（+0.03），Required_TBR 从 1.30078 降至 1.21094，降幅为 **0.08984**。
  - 从 0.05 增至 0.10（+0.05），Required_TBR 仅从 1.21094 降至 1.18359，降幅为 **0.02735**。
  - 在 Burn_Fraction ≥ 0.09 后，Required_TBR 基本趋于稳定（如 0.09 与 0.10 时均为 1.18359）。

  类似趋势在其他 Doubling_Time 约束下均存在，表明系统对 Burn_Fraction 的响应具有**强非线性饱和特性**。

- **Required_TBR 对 Doubling_Time 约束高度敏感**：
  - 在固定 Burn_Fraction = 0.05 时：
    - Doubling_Time = 0.5年 → Required_TBR = 1.21094
    - Doubling_Time = 2.0年 → Required_TBR = 1.07031
    - 差值达 **0.14063**，相对降幅约 **11.6%**。
  - 这表明更宽松的倍增时间要求（即允许更慢的氚库存增长）可显著降低对包层TBR的要求。

#### 敏感性比较：

由于本分析中**仅有一个因变量（Required_TBR）**，不存在多个性能指标的横向比较。但可从其对不同约束条件的响应强度判断其**对约束条件的敏感性远高于对 Burn_Fraction 的敏感性**。例如：

- Burn_Fraction 从 0.02 → 0.10（+400%），Required_TBR 最大降幅约 0.117（在0.5年约束下）。
- 而 Doubling_Time 从 0.5年 → 2.0年（+300%），Required_TBR 降幅达 0.246（在 Burn_Fraction=0.02 时）。

因此，**Required_TBR 对 Doubling_Time 约束值的变化更为敏感**，而对 Burn_Fraction 的变化敏感性次之，且呈现饱和。

---

### 2. 交互效应分析

本分析包含两个背景参数维度：
- **plasma.Fueling_Efficiency**：在配置中固定为 0.5（default_simulation_values），且性能指标总表仅提供该单一取值下的数据，**未展示其变化**。因此，**无法分析其与 Burn_Fraction 的交互效应**。表格中虽列为背景扫描参数，但实际数据仅对应一个值（0.5），故交互分析仅限于 **Burn_Fraction 与 Doubling_Time 约束值**。

#### Burn_Fraction 与 Doubling_Time 约束的交互效应：

- **交互效应显著存在**：Burn_Fraction 对 Required_TBR 的影响程度**依赖于 Doubling_Time 的约束严格程度**。
  
  具体表现为：
  - 在**严格约束**（Doubling_Time = 0.5年）下，Burn_Fraction 的提升对降低 Required_TBR 的效果**最显著**（从 1.30078 → 1.18359，降幅 9.0%）。
  - 在**宽松约束**（Doubling_Time = 2.0年）下，相同 Burn_Fraction 提升带来的 Required_TBR 降幅较小（从 1.11328 → 1.05469，降幅 5.3%）。

  这说明：**当系统要求快速氚库存倍增时，提高等离子体燃耗分数对缓解包层TBR压力具有更高边际价值**。

- **饱和点随约束宽松而提前**：
  - 在 0.5年约束下，Required_TBR 在 Burn_Fraction ≥ 0.09 后才趋于稳定。
  - 在 2.0年约束下，Burn_Fraction ≥ 0.08 时已基本稳定（0.08: 1.05859；0.09: 1.05859；0.10: 1.05469，变化极小）。
  
  表明：**宽松的倍增时间目标会降低系统对高 Burn_Fraction 的依赖**，更早达到TBR优化的“收益递减”拐点。

综上，**Burn_Fraction 与 Doubling_Time 约束之间存在显著正向交互效应**：约束越严格，Burn_Fraction 的提升对 Required_TBR 的改善作用越强。

> 注：关于 plasma.Fueling_Efficiency，由于数据表中仅提供其默认值（0.5）下的结果，**无法评估其与 Burn_Fraction 的交互作用**。若需分析该参数的交互效应，需补充其在不同取值（如0.3、0.7等）下的 Required_TBR 数据。

---

### 3. 综合结论与初步建议

#### 综合影响与权衡：

- **提高 plasma.Burn_Fraction 有助于降低对包层TBR的要求**，从而减轻氚自持设计压力，提升燃料循环可行性。
- 然而，这种收益**非线性递减**，且在 Burn_Fraction 超过约 0.08–0.09 后趋于饱和，继续提升燃耗分数对TBR的改善有限。
- **该效益在要求短氚倍增时间（如0.5年）的场景下最为显著**，表明高燃耗运行模式更适合于需要快速建立氚库存或支持多堆启动的早期部署阶段。
- 相反，在允许较长倍增时间（如2年）的稳态运行场景中，系统对 Burn_Fraction 的依赖较低，可接受较低燃耗以换取等离子体稳定性或工程可行性。

#### 初步设计与运行建议：

1. **针对不同部署阶段设定 Burn_Fraction 目标**：
   - **启动/扩张期**（需短 Doubling_Time）：应优先优化等离子体性能，将 Burn_Fraction 提升至 0.08–0.10 区间，以最大限度降低 Required_TBR，缓解包层设计压力。
   - **稳态运行期**（Doubling_Time ≥ 1.5年）：Burn_Fraction 可维持在 0.05–0.07，避免过度追求高燃耗带来的等离子体控制难度或材料负荷增加。

2. **包层TBR设计裕度应与运行策略协同**：
   - 若包层实际TBR能力有限（如仅达1.07–1.08），则必须配合较长的 Doubling_Time（≥1.5年）或接受较低的 Burn_Fraction（≤0.04）。
   - 反之，若追求0.5年倍增时间，则包层TBR需至少支持1.18以上（对应 Burn_Fraction=0.10），否则需进一步提升燃耗或引入外部氚源。

3. **未来分析建议**：
   - 补充 **plasma.Fueling_Efficiency** 的多值扫描数据，以评估其与 Burn_Fraction 的联合影响（例如：低加料效率是否可通过高燃耗补偿？）。
   - 探索 Burn_Fraction 与 TBR 之外的系统指标（如启动库存、循环滞留量）的耦合关系，以全面评估燃料循环稳健性。

---

**总结**：在给定数据范围内，**plasma.Burn_Fraction 是调节氚燃料循环自持能力的有效杠杆，但其效益受倍增时间目标显著调制，且存在明确的工程收益饱和点**。系统设计应根据氚战略目标（快速扩张 vs. 稳态运行）动态权衡燃耗水平与包层性能要求。
```

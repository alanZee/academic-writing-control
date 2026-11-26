# 学术论文写作原则：现象解释、机理论证与方法优势归因

## 1. 核心原则

**对观测事实明确陈述，对机理解释审慎推断，对因果关系严格论证。**

- **论断强度应与证据强度相匹配。** 不夸大研究结果所能支持的结论，也不弱化已经充分验证的发现。
- 解释现象、解释机理时，优先采用**关联性（association）、一致性（consistency）、证据支持（evidential support）**的论述方式，而非直接作出因果归因（causal attribution），除非该因果关系具有充分的理论或实验依据。
- 尤其对于**方法创新类论文**，不要仅凭良好的验证结果，就将性能优势归功于某项创新设计。应区分方法是否有效、具体设计是否有效，以及设计为何有效。
- 审慎表达应首先体现在**论证逻辑**上，而不是简单添加 may、might、possibly 等不确定性修饰词。
- 审慎不等于含糊。应尽可能给出具体、有物理或数学依据、能够被检验的解释。

## 2. 根据证据强度选择论断方式

| 证据层级 | 证据基础 | 推荐论断 |
|---|---|---|
| L1：客观观测 | 图表、实验数据、计算结果 | X 增大时，Y 呈现下降趋势 |
| L2：关联性发现 | 同步变化、统计关联、参数扫描 | X 的增大伴随着 Y 的下降 |
| L3：机理推断 | 理论分析、物理知识、诊断结果与观测相符 | 这一现象与 X 机理所预期的结果一致 |
| L4：设计作用验证 | 控制变量实验、消融实验、针对性比较 | 在所考察条件下，引入 X 改善了 Y |
| L5：因果机理论证 | 充分的理论推导、针对机理的干预实验等 | X 通过 M 机理导致了 Y |

**注意事项：**

- 多个现象同时出现，不代表它们之间存在因果关系。
- 性能对比能够验证方法的有效性，但不一定能够验证具体设计的独立贡献。
- 消融实验能够在控制充分的条件下验证某项设计的作用，但不一定能够揭示其发挥作用的内在机理。
- 现象与某一机理一致，并不意味着排除了其他可能的机理。
- 上述层级是写作判断的参考框架，而非绝对的证据等级体系。

## 3. 推荐的论证逻辑

### 3.1 优先采用“机理预测—观测验证”的论证方式

推荐建立以下论证链条：

**设计特性或物理因素 → 理论依据 → 预期机理 → 可预期的现象 → 实际观测结果**

具体而言：

1. 说明方法的某项设计特性，或流动系统中的某个物理因素。
2. 基于已有理论、数学性质或物理知识，分析其可能发挥的作用。
3. 说明若该机理成立，可以预期观察到什么现象。
4. 将实际观测结果与预期现象进行比较。
5. 在证据允许的范围内，给出机理解释。

**推荐：** 基于机理推断出预期现象，再讨论实际观测与其是否一致。

**避免：** 观察到良好结果后，未经充分分析，直接反向归因于某项创新设计。

对于由实验结果启发的事后机理解释，应如实将其表述为一种可能的解释，不应包装成事先提出并得到验证的假说。

### 3.2 优先解释具体的中间现象

解释方法优势时，不应仅建立“创新设计—性能提升”的宽泛联系，而应尽可能说明设计所对应的具体作用。

例如：

- 物理约束与非物理解的减少；
- 局部建模与局部流动结构的捕捉；
- 多尺度建模与不同尺度动力学的表征；
- 动力学约束与长期预测误差的累积；
- 能量传递机制与扰动增长率的变化。

若能够观察或量化这些中间现象，对方法优势的解释通常会更有说服力。

### 3.3 区分一致性与机理验证

- 若仅观察到预期的最终结果，应表述为**与机理或设计预期一致**。
- 若还观察到机理所预期的中间过程，可进一步表述为**为该机理提供支持**。
- 若通过针对性实验区分了竞争性解释，或直接验证了关键作用路径，则可根据证据作出更明确的机理论断。

**一致性是机理推断的依据之一，而非机理成立的充分条件。**

## 4. 推荐话术

以下话术为参考性表达，应根据具体语境与证据强度选择，不应机械套用。

### 4.1 预期一致性（Consistency with expectations）

适用于将良好的验证结果与方法的设计动机联系起来。

- This result is **consistent with the expected benefits of** X.

  这一结果与 X 所预期的收益一致。

- This behaviour is **in line with the expected effect of** X.

  这一行为与 X 所预期的作用一致。

- This finding is **consistent with the rationale underlying** X.

  这一发现与 X 背后的设计逻辑相符。

### 4.2 机理一致性（Mechanistic consistency）

适用于根据理论、物理机理或数学性质解释观测现象。

- This observation is **consistent with the mechanism of** X.

  这一现象与 X 机理一致。

- This behaviour is **consistent with the interpretation that** X.

  这一行为与 X 所对应的解释相符。

- This is **what one would expect if** X were to Y.

  若 X 发挥 Y 作用，则这一现象正是可以预期的。

- Such behaviour **would be expected from** X.

  根据 X 可以预期出现这一行为。

### 4.3 假说支持（Support for a hypothesis）

适用于具有一定理论或实验依据，但尚不足以完全确立机理的情况。

- These observations **lend support to the hypothesis that** X.

  这些观测结果为 X 假说提供了支持。

- This finding **provides further evidence for** X.

  这一发现为 X 提供了进一步的证据。

- Taken together, these results **suggest that** X.

  综合这些结果，可以推测 X。

### 4.4 关联性描述（Association）

适用于客观描述多个现象之间的联系，而不对其因果关系作出判断。

- The increase in X is **accompanied by** a decrease in Y.

  X 的增大伴随着 Y 的减小。

- X **is associated with** improved Y.

  X 与 Y 的改善存在关联。

- The variation in X **closely follows** that in Y.

  X 的变化与 Y 的变化趋势高度一致。

### 4.5 合理解释（Plausible explanation）

适用于提出尚未得到充分验证的机理解释。

- X **provides a plausible explanation for** this observation.

  X 为这一现象提供了一种合理的解释。

- One possible interpretation is that X.

  一种可能的解释是 X。

- This behaviour **may reflect** X.

  这一行为可能反映了 X。

### 4.6 解释边界与竞争性机理

适用于存在其他合理解释，或当前证据无法区分不同机理的情况。

- These observations do not necessarily imply that X.

  这些现象并不必然意味着 X。

- The present results do not distinguish between X and Y.

  目前的结果尚不足以区分 X 与 Y。

- This interpretation does not preclude the contribution of X.

  这一解释并不排除 X 的贡献。

## 5. 应谨慎使用的因果性表达

当缺乏充分的因果证据时，谨慎使用以下表达：

| 表达类型 | 常见英文表达 |
|---|---|
| 直接因果 | cause, lead to, result in, give rise to |
| 直接归因 | be due to, be attributed to, arise from |
| 强调决定作用 | be responsible for, determine, govern |
| 强调设计功劳 | thanks to, owing to, benefit from |
| 隐性因果连接 | thereby, thus, consequently, hence |
| 强机理论断 | demonstrate the mechanism, establish, prove, confirm |

上述表达并非禁用词。对于具有充分依据的数学推导、物理关系和受控实验结论，可以正常使用。

**尤其注意隐性因果关系。** 即使没有使用 cause 或 lead to，句子之间的衔接方式也可能暗含未经验证的因果推断。

## 6. 正反示例

### 示例一：解释方法的性能优势

**不推荐：直接归因**

The superior long-term prediction accuracy is attributed to the physics-informed architecture.

**次选：仅弱化因果判断**

The improved long-term prediction accuracy may be attributed to the physics-informed architecture.

**推荐：预期一致性**

The improved long-term prediction accuracy is consistent with the expected benefits of incorporating physical constraints into the model.

**更推荐：具体机理与观测的一致性**

The slower accumulation of prediction errors is consistent with the hypothesized role of physical constraints in limiting nonphysical deviations during temporal evolution.

### 示例二：解释流动稳定性的变化

**不推荐：未经验证的因果归因**

The reduction in the growth rate is caused by the enhanced viscous dissipation.

**推荐：关联性描述**

The reduction in the growth rate is accompanied by an increase in viscous dissipation.

**更推荐：基于物理机理的解释**

The reduction in the growth rate is consistent with the stabilizing role of viscous dissipation in the perturbation energy balance.

若进一步通过能量方程定量验证了黏性耗散对净能量增长率的贡献，则可在相应的数学与物理意义下作出更明确的论断，但仍应区分直接的能量收支贡献与参数变化背后的完整因果机理。

### 示例三：避免过度谨慎

**不推荐：弱化已经明确验证的事实**

The proposed model appears to potentially achieve a lower prediction error than the baseline.

**推荐：直接陈述客观结果**

The proposed model achieves a lower prediction error than the baseline across all tested cases.

对于数据直接支持的事实，无须使用不必要的审慎措辞。

## 7. 高水平论文原文参考

以下为真实文献中的原文节选，用于学习论证方式，而非直接照搬至其他论文。

**（1）He et al. (2016), CVPR**

*Deep Residual Learning for Image Recognition*, §3.1.

> suggesting that identity mappings provide reasonable preconditioning.

**值得学习：** 将实验中观察到的残差响应特征作为推断优化机理的依据，使用 suggesting 区分客观观测与机理解释。

**（2）Lappalainen et al. (2024), Nature**

*Connectome-constrained networks predict neural activity across the fly visual system*.

DOI: 10.1038/s41586-024-07939-3

> Consistent with our hypothesis, our results showed that ...

**值得学习：** 将验证结果与事先提出的研究假说联系起来，并通过具体的参数实验探讨设计特性的作用。

**（3）Lozano-Durán et al. (2021), Journal of Fluid Mechanics**

*Cause-and-effect of linear mechanisms sustaining wall turbulence*.

DOI: 10.1017/jfm.2020.902

> We show that transient growth is sufficient for sustaining realistic wall turbulence.

**值得学习：** 通过针对性的数值干预实验验证机理，在具备充分证据时使用明确、有力的论断，而非一味追求审慎措辞。

**补充语言资源：** University of Manchester, Academic Phrasebank，重点参考 *Discussing findings* 与 *Being cautious* 两个部分。

## 8. 撰写与修改时的执行要求

对于涉及现象解释、机理论证及方法优势归因的内容：

- **首先判断证据，再选择论断方式。**
- 优先采用具有具体理论或物理内涵的一致性表达，而非空泛地声称结果符合预期。
- 不凭空补充未经验证的机理，不虚构理论依据、实验结果或文献支持。
- 不将相关性、一致性、必要性、充分性及因果性混为一谈。
- 结论的适用范围不得超出研究所覆盖的条件。
- 对重要的、尚未充分验证的机理解释，应适当指出其证据边界；不必对每个次要推断重复添加局限性说明。
- 不机械堆砌审慎措辞，不因追求严谨而削弱已经充分验证的学术贡献。
- 不机械要求每个现象均采用完整的机理论证结构，应根据现象的重要程度与研究重点决定论述深度。

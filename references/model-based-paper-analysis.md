# Wang 等（2026）：方法、控制效果与效率怎样形成论证

用于查找方法替代、模型验证、迁移和效率论证的原文依据。[留档PDF](../assets/wang-et-al-2026-model-based-flow-control.pdf)的书目信息、许可与版本见[样本来源](source-profile.md)；与Li–Zhang的对照及通用选择见[跨文献综合](cross-source-synthesis.md)。

## 阅读边界与定位约定

- 源文：`Model-based reinforcement learning for active flow control: escalating performance and accelerated training`，DOI `10.1080/19942060.2026.2628971`。本笔记只分析所给出版 PDF，不联网核验其引用、不独立复现计算结果。
- 已通读提取全文，并逐页查看 PDF 物理页 2–17 的渲染图，核对两栏顺序、段首缩进、跨栏/跨页续段及相关图表。下文 `P` 为 PDF 物理页，`p` 为印刷页；本文件封面占一页，所以正文 `P = p + 1`，正文第一页未印页码但按 p1 定位。
- 实际章节为 §1 Introduction；§2 Numerical method（2.1 Flow configuration；2.2 Framework and algorithm of DRL；2.3 Model-free reinforcement learning；2.4 Surrogate model and MBRL）；§3 Results and analysis（3.1 MFRL for AFC；3.2 MBRL for AFC；3.3 MBTT for AFC；3.4 Discussion）；§4 Conclusions。引言中的章节导航与实际主章节一致。
- 以下按已核对的段首锚点讨论段落，不把断行当段落。公式引出句、式后定义按同一说明单元处理，不做全文段落数量统计。
- “观察”指原文、图表直接展示或明确报告；“作者解释”指文中的因果归因；“可迁移决策”是本笔记对写作组织的分析，不冒充论文实证结论。

## 文章究竟在证明什么

核心问题是 CFD 环境交互昂贵，限制 RL 策略学习。文章让 surrogate 预测传感器状态增量及即时奖励，承担策略训练环境，再把学得策略放回 CFD 测试。主张有三层：环境替代可用；在所测圆柱工况中获得减阻；surrogate 环境的单 episode 交互时间显著缩短。高 Re 下的 MBTT 是对控制质量不足的补充支线，不能把它混写成所有工况均获益的独立通用改进。

证据链按阅读顺序为：§2 定义环境与接口 → §3.1 建立 CFD/MFRL 工作基线 → §3.2 先检查 surrogate 预测，再检查 surrogate 训练策略回到 CFD 后的控制效果 → §3.3 检查直接跨 Re 使用的失配，再用低 Re 策略初始化目标 Re 的重训 → §3.4 汇总性能并给 episode 计时 → §4 收束。预测验证与闭环控制检验是两个不同门槛；前者并不替代后者。

## 各节内部的功能推进

### Abstract（P2/p1）

单个摘要段由应用价值起笔，迅速落到 RL 时间成本，提出 surrogate/MBRL，报不同 Re 的减阻数值，再以高 Re 数据与预测困难引入 transfer training，给 Re1000 的 36.2%，最后声明训练加速和外推潜力。其信息次序是“问题—替代机制—控制结果—困难工况补救—计算收益”。但摘要将计时概括为达到收敛的时间缩短，正文直接展示的计时对象实际上是 episode wall-clock time，迁移时应保留这个区别。

### §1 Introduction（P2–4/p1–3）

| 段首锚点与定位 | 段内功能推进 | 为主旨承担的任务 |
|---|---|---|
| `Drag reduction is a crucial topic...`，P2/p1 左栏起、右栏续 | 减阻价值 → passive/active 分类 → closed-loop 优势 → 非线性和高维动作难题 → DRL 候选 | 把应用问题缩到需要学习型反馈控制的算法问题 |
| `DRL integrates...`，P2/p1 右栏末至 P3/p2 左栏 | 解释 agent 交互与奖励 → 按代表性成果串起已有 AFC 实践 → 文献综述收束 | 证明“RL 能用于 AFC”已有基础，让本文无需从零证明研究方向 |
| `Despite these promising demonstrations...`，P3/p2 左栏至右栏上 | 承认已有成功 → DIDO 维数困难 → MARL 分解 → symmetry-aware architecture | 把高维表达/分解困难单列为相邻问题，说明本文不是唯一效率路线 |
| `Moreover, in the practical application...`，P3/p2 右栏至 P4/p3 左栏上 | 将瓶颈精确定位到 CFD 计算 → 并行环境/transfer 等已有办法 → 指出每次 CFD 仍慢 → 学习探索受限 | 建立本文真正处理的缺口；其“尚未解决”措辞很强，不可脱离检索复用 |
| `While traditional model reduction approaches...`，P4/p3 左栏 | POD 传统 → 深度 surrogate → world-model 概念 → AFC 先例 → offline RL 联系 → 工程搭建复杂度 → 低/高 Re 场景梯度 | 说明替代环境这条路线为何合理、也已有先例；新意转向可用参考实现与复杂工况验证 |
| `In light of the core challenge...`，P4/p3 左栏末至右栏上 | 重申成本问题 → 方法目的 → 开放参考实现贡献 → 章节路线 | 封闭引言的论证漏斗，承诺接下来要交付的方法与检验 |

观察：维数、MARL 和对称网络在引言与讨论形成前后呼应，但本研究并未把它们纳入自己的实验。可迁移的是“承认互补路线并界定自己处理的瓶颈”，不是把所有相关进展都展开成与主问题同等篇幅。

### §2.1 Flow configuration（P4–5/p3–4）

- `Figure 1 shows...`：几何域和坐标 → 喷口位置/尺寸 → 两喷口质量约束 → 物理解释。先定义可控对象，再给约束理由。
- `Assuming the fluid flow...` 及式后定义：不可压缩方程 → 变量/无量纲量 → Re。这里是可复现物理定义，不是结果证据。
- `At the inlet...` 及式后说明：入口分布 → 平均速度 → 出口/壁面边界。
- `Figure 2 presents...`：网格与局部加密 → Fluent/压力速度耦合/空间离散/步长 → 表面力积分与系数定义。由数值实现走向后续量化指标。
- `Based on the above method...`：基准阻力和 Strouhal 与文献一致的简短检验，建立 CFD 作为后续“真实环境”的可信起点。

### §2.2 Framework and algorithm of DRL（P5–6/p4–5）

- `In the application of DRL...`：把 CFD 解释为动态环境 → agent 定义 → 初始化 → state → action → 环境演化 → 新 state/reward → policy 更新 → 迭代终止。一个长段沿闭环时序推进，图3提供角色对应关系。
- `With the above process...`：压缩闭环逻辑 → 指名 PPO。段落任务是从一般交互机制落到所选算法，不再扩展物理问题。

### §2.3 Model-free reinforcement learning（P6–8/p5–7）

- `Figure 4 illustrates...`：用环境是否为 CFD 定义 MFRL → state/action/reward 接口 → 固定几何与唯一动作变量 → 151 探针 → policy 输出与采样 → 为避免跳变而引出执行器松弛律；式后续写动作持续时间、每 episode 交互数和 CFD 步数。它把“算法动作”与“实际施加动作”分开，避免只报算法名。
- `The reward of each action...`：目标为减阻与抑升力波动 → reward 公式 → 时间平均窗口。研究目标映射成优化目标。
- `In addition...`：交代 episode 的连续/重置概率，补足训练时序协议。

### §2.4 Surrogate model and MBRL（P8/p7）

- `In MBRL, the trained surrogate model...`：一句建立环境替代 → 100 episode、8000 transition 数据来源 → CFD transition 生成 → surrogate 输入/输出映射 → surrogate 与 policy 交互 → 快速映射与成本目的。功能是明确“替代什么”，并没有声称预测完整流场。
- `Table 1 shows...`：具体网络向量与三层结构 → 层数选择解释 → L2 正则化 → MSE 训练目标 → Model_Re 命名。把架构、损失、命名绑定到后文各 Re 比较。层数增减收益的说法未见本段对应消融图，不能迁移为已实证的最佳架构选择。

### §3.1 MFRL for AFC（P8–9/p7–8；图6–7位于P10/p9）

- `In this part, we first validate...`：明确 Re100 基线 → 训练协议 → Fig5 reward → 约150 episode收敛。先回答策略是否学会，再看真实控制结果。
- `Figure 6 presents...`：无控制时间序列 → 有控制平均阻力 → 波动幅值 → 文献对照。平均收益和稳定性并列。
- `Moreover, we conduct...`：明确选最小阻力时刻快照 → Fig7 三类场 → 速度/分离解释 → 压差数值 → 涡脱解释 → 小节收束。结果与物理解释在同一长段，后半“延迟分离/涡致阻力”等并非都由独立诊断检验证明，不能把示意场图当完整机制证据。

### §3.2 MBRL for AFC（P9–12/p8–11）

- `This section focuses...`，P9/p8右栏：声明两个任务（构建 surrogate、验证 MBRL） → 回顾训练数据。给出本节“双检验”的阅读契约。
- `To comprehensively evaluate...`，P9/p8右栏：Fig8/Table2 训练和测试损失 → 种子一致性及外部仓库位置 → 不同 Re 误差 → 高 Re 误差的作者解释 → 36探针对照与相对误差 → 同状态/动作下预测未来状态的小结。它先验证环境近似；36点误差不是长期闭环控制验证，也不代表完整流场重构验证。
- `Based on the agent model established previously...`，P9/p8右栏末、P10/p9底部两栏、P11/p10左栏上：使用 Model100 训练环境 → Fig9 无控/MFRL/MBRL对照 → 动作、均值、波动 → Fig10 流场对照 → 差异集中在压力 → 压差降低。视觉确认这是被多幅浮动图隔开的同一个段落。Fig9题注（P12/p11）明确将 surrogate-trained agents 放回 true CFD solver 验证，是从预测模型进入闭环控制的关键证据切换。
- `The MBRL framework is then extended...`，P11–12/p10–11：分别建立 Re200/500/1000 模型及各自agent → Fig11不同工况控制收益 → Re1000相对Re500退化 → 用模型误差/局部最优解释 → 小结。这里是“各Re分别训练”，不是单一策略跨Re泛化。
- `In sum, this section establishes...`，P12/p11：汇总相对 MFRL 的改善 → 压力差异 → 多Re适用。属于阶段结论，为下一节“低Re策略能否直接迁移”留出不同问题。

### §3.3 MBTT for AFC（P13–15/p12–14）

- `While the Re = 100 case serves...`，P13/p12左栏：以低Re标定引出跨Re问题 → 直接部署Re100策略到200/500/1000 → Fig12的均值和波动 → 跨Re能力减弱 → 文献关联解释。它先给不重训的直接迁移诊断，与上一节各Re分别训练严格不同。
- `Compared with ordinary DRL...`，P13/p12右栏上：策略质量依赖 surrogate 准确性 → 高误差可能损害策略 → 提出MBTT → 把目标policy的随机初始化换成Re100预训练参数 → 分别在Model200/500/1000继续交互 → 确定性测试。迁移对象是策略网络参数；本段没有说fine-tune surrogate。
- `Figure 13 illustrates...`，P13/p12右栏中：报告MBTT控制结果 → 三个Re减阻率。先回答该分支能否控制，下一段才比较是否值得采用。
- `In comparison with the MBRL method...`，P13/p12右栏末跨P14/p13两栏至P15/p14左栏上：先声明收益依Re而变 → Re200均值略差但波动较规则 → Re1000显著改善 → 三个解释性原因 → Re200/500可能负迁移 → 定位MBTT为模型不够准时的补充。`can potentially`、`may`、`might`说明这些原因是解释假说；三点在逻辑上有较强重复，不等于三项已验证机制。
- `To further understand...`，P15/p14左栏：固定Re1000，三组场对照 → 场形差异较小、压力差明显 → 压差2.68/1.82/1.28 → 连接减阻。以最突出收益工况做机制说明，而不是重新平铺所有Re。

### §3.4 Discussion（P15–17/p14–16，图14/Table3/Fig15集中P16/p15）

- `This section further discusses...`，P15/p14左栏至右栏上：定义两个评价轴（减阻、成本） → Table3汇总 → MBRL收益解释 → MBTT困难工况用途 → 外部研究数值对照。它将分散实验拼回题目双主张，但外部数字的公平性需各自协议支撑，不能从并排表格自动推出公平优越性。
- `Moreover, it is noteworthy that CFD...`，P15/p14右栏：环境成本原因 → surrogate替代 → 硬件 → Fig15单episode时间 → 效率解释 → 3D/高分辨率扩展推断。实测计时与外推在同一段，边界需要显式区分。
- `These results are encouraging...`，P15/p14右栏末跨P17/p16左栏：点名可扩展性和互补DRL进展 → 当前2D/Re范围 → surrogate误差及长期积累问题 → 不宜直接照搬当前架构 → neural operators等未来路线 → 定位为中间一步。它是在讨论适用边界，不能当已经完成的3D证据。
- `Beyond improving the accuracy...`，P17/p16左栏：明确正交互补 → DIDO/MARL → symmetry-aware networks → 可组合路线。回应引言的邻接方向，使本文贡献嵌入更大技术图景，但均属将来结合设想。

### §4 Conclusions（P17/p16）

- `To address the challenge...`：回扣时间成本 → MBRL方案 → 多Re检验 → MBTT → 所有策略回原环境测试 → 引出结论项。
- 三条编号项分别承载：Re100的MFRL/MBRL减阻对照与动作解释；低Re经验用于Re1000及36.2%；学习效率与应用前景。不是又一个结果分析节。
- `In summary, the proposed...`：把“surrogate学习+原环境验证”重述为框架贡献，再提出拓展方向。该末段与前述开头/编号项存在重复，可借其回扣作用，不必照搬重复幅度。

## 摘要的九句如何分配论证责任（P2/p1）

| 句序 | 语义与句法动作 | 为何放在此处/使用边界 |
|---|---|---|
| S1 | AFC作主语，系表结构给减阻应用价值 | 建立任务背景；宽泛应用价值不能代替后面的具体问题 |
| S2 | To tackle前置目的，this study presents提出MBRL | 将宽背景收窄到时间成本，方法名有了问题来源 |
| S3 | surrogate models作主语，被动说明构建范围，replacing交代替代对象 | 确定方法改动的是训练环境，不是所有CFD工作或PPO更新规则 |
| S4 | strategy作主语，报告各Re减阻率，分词引出效果概括 | 第一条结果线是控制质量；数字仍需与正文/表格核对 |
| S5 | Considering前置困难，提出transfer training | 将工况扩展中的问题接到有针对性的分支 |
| S6 | Upon retraining and fine-tuning限定条件，给Re1000结果 | 结果与重训条件同句出现；不能省略成直接泛化 |
| S7 | Meanwhile转换评价轴，比较策略优化速度 | 回收标题的加速承诺；其convergence概括须与Fig.15的episode计时区别对待 |
| S8 | This study作主语，概括框架贡献 | 从分项结果回到方法意义，不能再引入未经验证的效果 |
| S9 | MBRL method作主语，并列适配、优化与未来应用 | 收束并外推；借鉴回扣功能，不复制比实际范围更强的应用承诺 |

其摘要把“控制收益—困难工况的适配—成本收益”排为三组，并不是正文目录的机械压缩。新稿若核心主张是知识关系而非效率，应改变结果选择和顺序，不要求照凑九句。

## 四个典型段的逐句拆解

### A. 引言定位段：`In light of the core challenge...`（P4/p3，跨左栏末到右栏上）

| 句 | 功能与句法 | 指代/衔接与证据边界 |
|---|---|---|
| A1：以 `In light of...` 起笔，提出 develop MBRL by integrating surrogate 与RL | 前置原因/依据状语承接前文；主句 `this study aims to develop` 明确本研究目的；`by integrating` 交代实施机制 | `the core challenge` 精确回指 CFD wall-clock 成本，不是笼统的RL所有困难。此句是研究目的，尚非成果证明 |
| A2：`A key contribution...reference implementation...` | 系表结构给贡献类型，`aiming to lower...` 给预期用途 | 从算法概念转到公开可用实现的实用贡献；避免声称首次提出world model。降低采用门槛是目的，未展示用户研究证明 |
| A3：`The remainder...: Section 2 introduces...` | 冒号后给方法导航，列并行对象 | 方法范围包含flow、DRL、MFRL、MBRL，与已提出的替代机制匹配；`and so on` 不够精确，不值得学习 |
| A4：`Section 3 presents...performance...mechanisms` | 简洁主谓宾，承诺结果与物理解读 | 把检验责任放在性能和机理，不只报网络训练损失 |
| A5：`Finally...Section 4` | 结尾时序副词与章节导航 | 功能是结束引言；原句语法欠稳（`conclusions and outlines direction`），不复制其句式 |

跨段关系：前一段已经承认surrogate/world-model的既有成果和实施复杂性，本段不应重复文献，而应把缺口转为本文的可检验任务。可迁移的结构是“明确瓶颈 → 本文动作 → 贡献种类 → 后文承担的验证”；不是每篇稿都需要长篇world-model背景。

### B. 预测验证到控制检验的衔接段：`Based on the agent model established previously...`（P9–11/p8–10；Fig9证据在P12/p11）

| 句 | 功能/句法 | 指代与观察—解释边界 |
|---|---|---|
| B1：`Based on...we substituted...Model_100` | 前置依据状语+作者实施动作；括号解释模型训练Re | 回指前文已经训练并评估的surrogate。正文的`agent model`术语容易混淆，改写时应明确“环境模型”，与policy分开 |
| B2：`Figure 9 illustrates...three distinct scenarios` | 图定位+并列三条件 | 同一图比较无控/MFRL/MBRL，提供外部基线和任务收益；检验环境必须连同题注读取 |
| B3：`This figure allows us to compare...` | `This figure`回指图9；纯元话语 | 不增加数据或推理，可删，避免“图允许我们看”的冗余 |
| B4：`Compared with...MBRL leads to an increased jet velocity...` | 前置比较框架+主要观察；分词补周期性 | 先报动作差异，给后续减阻结果可理解的物理入口 |
| B5：`The increase in jet velocity reduces...14.6%...which is higher...` | 主语把动作变化名词化；关系从句接外部结果比较 | 14.6%为原文报告；“动作增大导致改善”的因果强于简单共现，缺少动作幅度受控的单因素证据，迁移应保留层次 |
| B6：`Additionally...oscillations...0.2%` | 并列增补第二指标 | 不只看均值，还看波动；观察性结果 |
| B7：`In other words...superior performance` | 总括性重述 | 概括B4–B6；`superior`适用范围应绑定本工况与所用指标，不可泛化 |
| B8：`Furthermore, Figure 10 compares...` | 切换证据种类，列velocity/pressure/vorticity | 从“效果多少”进入“场上哪里不同”；图不是装饰而是承担下一层问题 |
| B9：`It can be observed that...similar...velocity and vorticity` | 非人称观察句+两类场的一致性 | 先排除直观上没有明显分开的特征，给真正差异留位置 |
| B10：`However, a clear difference...pressure` | 转折+短主句 | `However`为具体对比，连到B9的相似，并非无信息自我防御 |
| B11：`As indicated...2.29...1.92...which directly leads...` | 图内标签定位+量化对照+结果关系从句 | 压差数值把定性场比较拉回量化证据。因果力度依赖压力阻力定义及足够采样，不能从单帧“directly”外推所有动力学机制 |

跨段关系：上一段通过train/test与36点预测回答“近似环境是否足够拟合观测”，本段切换到“该环境中学出的策略能否在原CFD控制”。前者是必要背景，后者才支持AFC效益。下段才把相同协议推广到各个Re分别训练的agent。最可迁移的决策是保留这三个层级，不能用低MSE替代控制效益，也不能把各Re独立训练称为一个policy泛化。

### C. 迁移分支的动机与协议段：`Compared with ordinary DRL...`（P13/p12右栏上）

| 句 | 功能与句法 | 指代/边界 |
|---|---|---|
| C1：`Compared with ordinary DRL...so...closely related...accuracy` | 比较开头，`so`连接环境机制与策略质量 | 解释为什么模型误差会成为MBRL的关键变量；是方法论论证，不是误差因果实验 |
| C2：`Facing more complex environments...may result...` | 分词状语界定工况，`may`标记可能性 | 承接前段直接迁移波动与前节高Re误差，不把相关性写成确定根因 |
| C3：`To address this problem, we propose...MBTT...` | 目的状语+提出动作+全称缩写 | `this problem`主要回指模型误差影响策略；让新增方法有具体任务，不是为了再增加一个方法名 |
| C4：`Instead of initialising...the strategy involves...` | `Instead of`作明确协议对照；改变初始化 | 对照有实质信息：目标策略随机/正交初始化改为低Re知识初始化，不是宣传性的“不是X而是Y” |
| C5：`This is achieved by employing...parameters...which subsequently...` | 被动实现句+定语从句描述后续交互 | `This`指transfer knowledge，具体载体是预训练policy权重；分别与三个目标Re surrogate交互。句子将多个步骤压得较长，写作可拆“初始化”和“目标环境重训” |
| C6：`A deterministic test...was then performed...` | 被动语态+then时序+评估目的 | 训练之后测试，是协议闭环。此句本身没有详细说明solver，但全篇Fig9/结论补足原环境检验身份，自己的稿件宜在本处也写清楚 |

跨段关系：前段先测试低Re策略直接部署，暴露不同任务范围；本段给参数迁移并重训协议；下一段报MBTT结果；再下一段与从头MBRL比较，指出中Re并非都改善。可迁移的是“诊断 → 有针对性的改动 → 重新测试 → 与同任务基线比较”。fine-tuning在此属于MBTT实现步骤，并没有一条独立于MBTT的fine-tune实验支线，也未证明减少surrogate预测误差。

### D. 成本比较段：`Moreover, it is noteworthy that CFD...`（P15/p14右栏，Fig15在P16/p15）

| 句 | 功能与句法 | 指代/边界 |
|---|---|---|
| D1：`Moreover...CFD...so...takes a long time` | 加法转场，把讨论从控制收益切换到计算代价；因果连接 | 回扣引言成本缺口；`it is noteworthy`不增加信息，可省 |
| D2：`Taking the example...surrogate models mimic...thereby...` | 范围状语+替代机制+结果分词 | 将“为什么会快”联系具体案例；仍属机制解释 |
| D3：`For example, this work was executed on hardware...` | 被动执行条件陈述 | 给CPU/GPU型号，让计时有硬件语境；不等于线程数/训练预算全部交代完整 |
| D4：`As shown in Figure 15...40 min per episode...whereas...0.84 s` | 图证据+同句对照，单位和分母清楚 | 本段最关键的直接计时证据；对象为每episode，不能改称端到端训练总时间或达到同等效果的时间 |
| D5：`This substantial acceleration...` | `This`回指D4差值；概括效率意义 | 可以解释迭代环境更便宜，但未量化总学习成本 |
| D6：`Moreover...simplified scenario` | 重设适用范围 | 从实测转向复杂环境讨论的边界提示 |
| D7：`As the complexity escalates...potentially...` | 条件/情景从句+例子+潜在影响 | 3D或高分辨率CFD成本上升的推理，非本文已完成实验 |
| D8：`At such junctures...while...holds promise...` | 回指假设情景，延伸MBRL可能性 | 同句把未来优势写得较强；不能默认surrogate误差、数据成本和网络成本不随问题增长 |
| D9：`This extension would...thus...potential` | 指代扩展方案，would标记设想 | 结尾是在提出前景，不是证实高维/高性能计算能力 |

跨段关系：前段Table3完成质量汇总，这一段补效率维度，回应题目“performance and accelerated training”的双目标。后一段又承认scalability需要更好的surrogate，这是对D7–D9乐观外推的限制。可迁移的是“计时对象和条件先说清，再谈意义”；不能学习把单episode加速扩大成已证实总训练提速。

## 如何迁移到新稿

把本篇的原段与具体任务匹配：方法替代先交代角色和接口；结果按模型预测、原系统闭环效果和适用范围分层；迁移比较说清重训状态；成本结论使用实际测量的分母。相应的通用选择集中在[跨文献综合](cross-source-synthesis.md)，执行检查在[主张检查](control-claim-checks.md)。这些是按主张选用的规则，不要求其他控制论文补出相同实验。

## 不能照搬的措辞或推理

- **“模型准确→策略必然更优”**：train/test或36点误差不能替代闭环CFD测试，也没有证明误差大小与控制回报之间的因果函数。
- **“训练更快→探索更多→更大jet→减阻更多”**：文章提出这条解释，但所见证据没有相同wall-clock/相同交互预算的控制实验把每个箭头单独证实。写作技能应要求归因证据，不能将该链条作为默认解释模板。
- **“fine-tune提高模型准确性”**：本节重训的是policy初始化与交互过程，不是展示surrogate再拟合误差下降；“以先验政策缓解坏模型下探索”是作者解释。
- **“不同Re都提升/跨Re通用”**：MBTT的Re200、500减阻率低于MBRL；不同Re训练各自agent也不能支持单个agent的通用能力。
- **“orders of magnitude faster convergence”**：Fig15给的是单episode2400 s vs0.84 s，没有同时呈现数据生成、模型训练、各方法收敛episode、达到同效果的总时间。应记为原文摘要的概括与正文计时范围不完全一致。
- **机制的`directly leads`**：压力贡献可与阻力定义直接关联，但一帧velocity/vorticity图不足以证明分离延迟、全程涡致阻力抑制等完整因果机制；不要照搬“clearly demonstrate”等力度。
- **高维外推**：2D Re100–1000的结果不是3D或充分湍流验证。原文也在§3.4讨论surrogate架构的扩展困难。
- **冗余表达**：`This figure allows us to compare`、`it is noteworthy`、`In other words`重复上句、`Clearly`和`significantly`无统计定义等不能当学术句式资产。学习功能，重新写短句。
- **术语混用**：原文`agent model`有时指surrogate、§2.4一句把surrogate输入写为进入policy network，读者易混淆。可迁移写法应固定“environment/surrogate model”和“policy/agent”。
- **数值与标注不一致**：§3.2正文的高Re减阻24.60/30.61/22.03%与摘要/Table3的25.4/31.2/21.8%不同；Re100正文/摘要14.6%而Table3为14.9%；Fig12明确`Agent_100_MBRL`，Table3相应跨Re数值却列在`Agent_100_MFRL`行。图8与Table2部分损失数值也不完全一致。写作分析可引用为“原文报告”，不可把它们整合成一个已核验数值表。
- **不用复制它的强外部优越性结论**：文献并排数值没有自动完成几何、动作幅值、reward、预算、采样窗口对齐。仅做局部写作借鉴时，也要让评价尺度来自自己的协议。

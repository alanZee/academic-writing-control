# 从材料到连续段落：完整起草示例

用于已有事实但尚未成段的起草任务，配合[章节写法](section-playbook.md)；只需句法改写时用[段落与语言](paragraph-and-language.md)。两组均为**原创、虚构教学输入**，数字、实验和结果不属于任何源论文或用户项目。只迁移组织决策，不迁移事实；不需要为新稿补做示例中的实验。

每组展示输入边界、组织决策、成稿和核对。两段、三段是本练习的选择，不是写作配额；不要求日常交付附带这些分析表。主张边界以[主张检查](control-claim-checks.md)为准。

## 1. 非RL方法段：传感器位置与柔性梁反馈控制

### 输入材料与范围

任务：撰写“传感器位置比较”的两段英文方法正文，不写结果。前文已定义悬臂梁力学模型、长度L、横向位移y及坐标x；本段只补比较协议，不承担整篇方法的复现说明。

**给定事实：**

- 目的为比较相同固定反馈增益下，测量位置改变时的振动响应，不优化增益。
- 两个独立工况分别在x=0.7L和0.9L测量横向速度v_s；尖端横向力执行器相同。控制律u=-g v_s，g=0.8 N s m^-1；u限制在±2 N，每1 ms更新并保持至下一次更新。
- 每个工况都从静止开始，在x=0.5L施加幅值0.1 N、频率5 Hz的正弦横向外力，持续0—20 s；反馈也在t=0开启。其余模型、初态、外力及执行器设置相同。
- 两个工况均独立记录尖端位移与执行器力，每1 ms采样；用5—20 s内的位移RMS评价响应，同时报告执行器力RMS。该窗口用于排除最初5 s，不声称已经证明达到稳态。

**假说：** 无需在本方法段加入机制假说。

**未给信息：** 两布局的控制结果、模态形状、可观测性分析、功率或能耗。不得补写哪个位置更好、为什么更好或是否稳定。

### 组织决策

第一段交代比较问题及唯一设计变量，把“测量速度—反馈力—限幅与更新”接成控制接口；第二段规定共同激励、起点、读出量及窗口。第二段沿用第一段的两种位置，读者无需重新辨认比较对象。

增益、限幅、时间窗都改变比较含义，保留在正文。前文已定义的力学模型不在本段重复；没有给定的求解设置也不编造。执行器力RMS用于描述力的大小，不能改称能耗。

### 成稿

We compare two sensor locations to examine how measurement position affects the vibration response under a fixed feedback gain. The transverse velocity v_s is measured at either x = 0.7L or x = 0.9L and used to command a transverse force at the beam tip according to u = -g v_s, with g = 0.8 N s m^-1. The commanded force is limited to ±2 N and updated every 1 ms, with each value held until the next update. The gain and actuator settings are identical for the two locations.

For each location, the beam starts from rest and is subjected to a sinusoidal transverse force of amplitude 0.1 N and frequency 5 Hz at x = 0.5L over 0–20 s; feedback is activated at t = 0. The model, initial condition and external forcing are otherwise unchanged. Tip displacement and actuator force are recorded separately at 1 ms intervals in both cases. Their root-mean-square values are evaluated over 5–20 s, excluding the first 5 s from the comparison. The displacement measure quantifies the vibration response, while the force measure describes the actuation applied over the same interval.

### 语义核对与可变编排

| 输入中的关键含义 | 成稿如何保留 | 不能追加的推论 |
|---|---|---|
| 测点不同，增益与执行器设置相同 | 首段先说明变量，再明确共同设置 | 不能宣称比较了各布局优化后的最优性能 |
| 控制律、限幅、保持和更新间隔 | 完整保留，未替换成RL或状态估计器 | 不能由负反馈符号推断闭环稳定 |
| 相同初态、外力和开启时刻 | 第二段以For each location连接 | 未给结果，不能提前宣布某测点优势 |
| 独立记录尖端位移；比较5—20 s | 读出量与策略观测量分开 | 策略并未获得尖端位移这一额外输入 |
| 排除最初5 s | 只说明排除时段 | 不能改称已达到稳态 |
| 力RMS | 描述actuation大小 | 不能替换为功率或净节能 |

若前文尚未交代激励，可先介绍共同试验条件，再介绍两种测量位置和控制接口，最后交代评价量。重排仍保留全部事实和同样的认识边界；这组练习不要求固定“控制律先行”。

## 2. 流动控制结果段：反馈与一个固定输入的比较

### 输入材料与范围

任务：撰写三个连续的英文结果段。前文已定义二维圆柱算例、Re、以D/U标度的时间、升力系数C_L及射流输入q。以下均是教学材料中已给定的观察，不需要新做计算。

**给定事实：**

- 在Re=100，从t=150的同一受控状态继续两条轨迹，其他条件相同。一支保留反馈；另一支将q固定为原反馈轨迹在t=130—150内的时间平均值，执行器保持开启。
- t=150—170内两支均保持低幅振荡；此后固定输入支的升力振荡增大，反馈支保持低幅振荡。
- t=200—250内，C_L标准差在反馈支为0.04，固定输入支为0.18。此数值描述这两条轨迹，未提供多次独立重复或统计检验。
- 给定图6(a)是两支C_L时序，图6(b)是输入q的时序；输入图确认上述处理。未给颜色、插图或其他面板。

**假说：** 作者尚未提出经过检验的具体作用机制。比较能够说明这一固定输入是否维持原反馈响应。

**未给信息：** 其他常值输入的效果、流场稳定性、压力重分布、涡量相消、功耗、平均阻力。不能从此比较补写这些结论。

### 组织决策

第一段建立比较目的、共同起点和输入处理，防止把“固定输入”读成“关闭控制”。第二段先概括已支持的响应差异，再交代共有的初始阶段和定量窗口。第三段收束到此项处理的结论，不推及所有常值输入，也不为了段尾有“意义”而编造机理。

图按承担的证据任务出现：输入面板证明处理，响应面板支持比较；正文不必遵循面板字母顺序。末段可以与第二段合并，本例分开是为了展示综合判断如何回接第一段的问题。

### 成稿

To examine whether a constant input maintains the response achieved with feedback, we continue two trajectories from the same controlled state at t = 150 for Re = 100. One retains feedback, whereas the other holds q at its time-averaged value along the original feedback trajectory over t = 130–150. The actuator remains active in both cases, and all other conditions are unchanged. Figure 6(b) shows the corresponding input histories.

The fixed-input trajectory develops larger lift oscillations than the feedback trajectory after t = 170 (figure 6a). Both initially retain low-amplitude oscillations over t = 150–170, after which the oscillations grow under the fixed input while remaining small with feedback. Over t = 200–250, the standard deviation of C_L is 0.18 for the fixed input and 0.04 for feedback.

The constant input therefore does not maintain the low fluctuation level achieved with feedback over the comparison window. The difference emerges despite the shared initial controlled state and the use of the preceding mean feedback input, distinguishing the subsequent responses to these two input histories.

### 语义核对与替代编排

| 检查点 | 成稿中的处理 |
|---|---|
| 固定输入与关闭控制不同 | 明确执行器保持开启，未写control removal |
| 常值来源 | 保留130—150的平均窗口，不称t=150瞬时输入，也不虚构严格相同的后续平均流量 |
| 共有阶段与差异阶段 | 保留150—170低幅和随后分化，未将全时域描述为固定输入更差 |
| 数字、统计量与窗口 | 保留0.18/0.04、标准差、200—250，不改成峰值或显著性结论 |
| 图面证据 | 只使用给定面板，不增加颜色、场图或新图号 |
| 认识范围 | 只判断所测常值与反馈；不写所有常值控制无效、闭环稳定或已知机制 |

如果读者已在前文知道分支设置，可直接以前置发现开头：

> At Re = 100, the constant input equal to the preceding mean feedback input does not maintain the low lift fluctuations achieved with feedback over the comparison window.

随后接入原有分支协议、两个时间阶段和数值比较。该句用确定语气是因为练习已提供相应结果；前置不会使它变成假说。相反，即使把“这是由于某种涡量相消机制”放在段末，现有输入仍不支持这项解释。

## 3. 迁移到其他起草任务

按当前任务辨认已有事实、作者解释和缺失信息，再决定哪些条件读者必须先知道。选择能让比较回答问题的段落职责，写出连续正文后核对事实与强度。必要的结构调整可改变句序、段数和图的引用次序；不能改变结果、比较方向或解释等级。材料仅支持局部正文时交付该部分，把重要缺项留在简短说明中，不把练习框架当作新增实验或写满整节的要求。

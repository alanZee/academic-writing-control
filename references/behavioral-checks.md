# 行为试用：维护时的有限检查

仅用于修改 skill 后检查实际输出，不是每次写作前的必经流程。正常写作不要加载本文件。可复用输入和判据；历史回答只用于复核，不能当作新执行者的标准答案。

## 使用方式与判据

给独立执行者 skill 入口和对应任务输入，按当前授权使用可用的隔离执行方式；不要同时给判据、历史回答或其他执行者输出。限制为只读 skill 与所给教学材料，不接触真实项目或实验。没有独立执行条件时可自查，但应标明自查，不声称独立试用。

| 任务 | 输出层面的通过条件 |
|---|---|
| T1 局部润色 | Re、数值、时间窗、比较基准、均值变化和每例一条轨迹均保留；不添加显著性、机制、稳态或普适结论；完成局部文本任务 |
| T2 已有效文本审查 | 能接受已有“发现先行”的段落，不强迫重排或为了模仿样本制造缺陷；只交付判断和理由 |
| T3 非RL连续起草 | 两段有分工且衔接；保留两时段、六个指标值、共同条件和单条记录；不增RL、图号、功率、机制或稳定性结论 |
| T4 机制假说润色 | 保留可能解释、竞争解释、现有测量不能判别及单一激励频率范围；不要求先补实验才能润色 |

按含义与任务完成情况判断，不能只匹配句式或关键词。每项区分通过、存在具体问题、无法判断；失败时记下原输出和问题，修正后只重跑受影响任务。不把这些试用变成所有未来请求的硬性验收表。

## 固定输入

以下均为虚构教学材料，前文已定义相关物理量。各任务独立。

### T1

参照Li–Zhang的写法，仅润色下面这段英文，输出改写和一句简短中文说明：
At Re = 120, feedback control is effective in reducing the standard deviation of the lift coefficient from 0.48 to 0.06 over t = 200–300, compared with the uncontrolled case evaluated over the same interval. The mean drag coefficient changes little. These values are obtained from one trajectory for each case.

### T2

审查以下结果段是否需要语言修改，只给判断和必要理由：
Controller A yields a smaller tracking error during the initial transient, whereas controller B yields a smaller error in the latter half of the evaluation window. Both controllers are evaluated under the same forcing and actuator limits. The comparison distinguishes transient tracking from the subsequent controlled response.

### T3

根据以下作者材料写两个连续英文结果段，简短说明组织理由。这是非RL的柔性面板振动控制研究。前文已定义位移、执行器力及其单位。不要补写方法细节。
两种固定增益反馈控制器A/B，在相同外部激励、初态、力限幅下各有一条完成的20 s记录。0—4 s中A的峰值位移1.2 mm、B为1.8 mm。10—20 s中A/B的位移RMS分别0.30/0.20 mm，执行器力RMS分别0.9/1.4 N。作者要说明启动响应与后段振动控制存在不同表现，后段较低位移伴随较高力RMS；未提供功率、能耗、统计检验或稳定性证明。未给图表。

### T4

润色以下英文段落，保持原意：
The reduced oscillation may be associated with a change in the phase relation between the applied force and the measured velocity. The available measurements cannot distinguish this explanation from the proposed redistribution of the response between modes. The observed attenuation is confined to the forcing frequency examined here.

## 1.5.0 试用记录

执行日期：2026-10-29；候选版本：1.5.0。四个执行者各自从无会话历史的上下文开始，读取同一候选 skill，按需读取参考材料；未提供本文件的判据、历史回答或预期答案。模型沿用主会话配置，未另外指定。复核者为主代理，不是人类读者。

| 任务 | 代理复核结果 | 具体依据 |
|---|---|---|
| T1 | 通过 | 保留Re=120、0.48/0.06、200—300、相同对照窗、平均阻力变化较小及每例一条轨迹；去掉空泛effective in，没有新增百分比或机制 |
| T2 | 通过 | 明确判为无需修改，接受发现先行、条件随后出现的段落；未提供强制重写 |
| T3 | 通过所列语义与组织判据 | 两段分别组织启动与后段响应，六个数值和各自指标、时间窗保留；未引入RL、能耗、图号或稳定性 |
| T4 | 通过 | 保留may、两种解释、不可判别状态和所测激励频率；没有把润色变成补实验前置条件 |

T3仍有可选的压缩空间：第一段末尾再次概括启动优势，第二段末尾再次概括后段力RMS差异。它不改变事实或段落分工，但不能据此声称文风已经最优。现有重复诊断规则足以处理，无需为一次输出再增加普遍禁令。本轮未修改判据来迎合输出，也未因句式偏好重跑任务。

**验证边界：** 这只是每类一次的输出层面试用，没有修改前后的对照、多人阅读或整稿评测。只读资源范围也由试用任务明确限制，因此不能据此单独证明无该限制时的工具调用行为。格式/链接检查另行进行；这些结果不证明实验正确、论文投稿就绪或写作质量稳定提升。

### 当次实际输出

以下保存原始最终回答，不是后加工后的标准答案。未来执行者不要预读。

#### T1

At Re = 120, feedback control reduces the standard deviation of the lift coefficient from 0.48 in the uncontrolled case to 0.06 in the controlled case, with both values evaluated over t = 200–300. The mean drag coefficient changes little. These statistics are obtained from one trajectory for each case.

改写以定量比较直接呈现控制效果，保留相同时间窗、平均阻力变化较小及每种情形仅一条轨迹的统计范围。

#### T2

无需语言修改。首句清楚保留了两个控制器在不同时间阶段的各自优势；第二句交代共同的比较条件；末句概括比较所区分的响应阶段，未夸大为整体优越性或长期稳定性。措辞准确、衔接自然，没有必须消除的重复或歧义。

#### T3

Controller A produced a smaller startup displacement peak than controller B in the flexible panel. The comparison used one completed 20 s record per fixed-gain feedback controller, with the same external excitation, initial state and actuator force limit. Over 0–4 s, the peak displacement was 1.2 mm for A and 1.8 mm for B, indicating a lower startup peak with A under the tested conditions.

Over 10–20 s, controller B instead yielded the lower displacement RMS: 0.20 mm, compared with 0.30 mm for A. This lower vibration level was accompanied by a higher actuator force RMS, at 1.4 N for B versus 0.9 N for A over the same interval. The two records therefore distinguish A’s lower startup peak from B’s lower later-stage displacement RMS, with the latter accompanied by a greater RMS force.

组织理由：第一段建立共同条件并聚焦启动峰值，第二段承接后段表现及其力 RMS 差异。保留两个时间窗和指标的区别，将结论限定于所给记录；不将力 RMS 解读为功率或能耗，也不引出统计显著性、稳定性或虚构图号。

#### T4

The reduction in oscillation may be associated with a change in the phase relation between the applied force and the measured velocity. However, the available measurements cannot distinguish this explanation from the proposed redistribution of the response between modes. The observed attenuation is limited to the forcing frequency examined here.

## 1.7.0 ARS＋Humanizer联合复核试用

执行日期：2026-10-29。三个执行者各自从无会话历史的上下文开始，读取同一1.7.0候选skill；只提供任务、输入和必要资源范围，不提供下列判据或其他执行者输出。模型沿用主会话配置，复核者为主代理。以下输入均为虚构教学材料。

### 判据与实际结果

| 任务 | 预设判据 | 代理复核结果 |
|---|---|---|
| H1 清理结构残留 | 删除无信息开头、拔高收尾和聊天包装；保留所有数值、比较条件及单条轨迹范围；只输出最终正文 | 通过：保留Re=80、1.40/1.28、100–150、相同窗口、每例一条轨迹及两例0.05；未增加机制或统计显著性 |
| H2 保留有效表达 | 不机械改写robust control、真实rather than对比、时间范围和机制限定；允许无需修改 | 通过：明确建议保留，说明技术词、计量区别和不可判别性各自的作用 |
| H3 LaTeX只审查 | 不修改文件；不建议删除数学粗体、公式、引用键、回指和链接目标；遇到歧义不补造科学身份 | 通过：只给建议，保留技术内容；识别跨轨迹比较与时间变化的歧义，未补造轨迹身份。原文件前后SHA256一致 |

H3给出的“redistribution of energy”以确认指代为条件，不是直接替作者确定机制；该建议仍需作者按实际含义选择。三个任务均未核验实验、外部引用或编译PDF。每类只执行一次，不能推为整稿效果、多人读者体验或普遍可靠性证明。只读资源范围由试用提示明确限制，因此不能单凭本轮结果证明所有自由工具使用场景的范围控制。

### 任务输入

#### H1 输入

请用该skill润色以下英文结果段，只交付最终正文：
Certainly! It is important to note that, at Re = 80, feedback decreases the mean drag coefficient from 1.40 in the uncontrolled case to 1.28 over t = 100–150. Both cases are evaluated over the same interval using one trajectory per case. The standard deviation of the lift coefficient remains 0.05 in both cases. This is the real breakthrough. I hope this helps!

#### H2 输入

仅审查以下文字是否需要语言修改，给出简短判断与必要理由。robust control为本稿已定义的方法类别，相关量也已定义。
We use robust control for the prescribed interval of stiffness uncertainty. We compare interaction budgets rather than wall-clock training times. Over t = 100–150, the observed attenuation may reflect a change in the phase relation, although the measurements do not distinguish this explanation from the proposed redistribution between modes.

#### H3 输入

请仅审查 `latex-review.tex` 的表达是否有需要优化的地方，给出具体建议，不修改文件。它是自足的教学片段；图号、引用键、公式和外链均作为作者提供的文本内容，不需要核验外部来源。

```latex
\subsection{Controlled response}
\label{sec:controlled}
The perturbation velocity is denoted by $\mathbf{u}'$. Its energy is defined as
\begin{equation}
E(t)=\frac{1}{2}\int_{\Omega}\mathbf{u}'\cdot\mathbf{u}'\,\mathrm{d}\Omega.
\label{eq:energy}
\end{equation}
It is important to note that the mean of $E(t)$ in \eqref{eq:energy} decreases from 0.30 to 0.20 over $t=100$--$150$ in the two trajectories compared in figure~\ref{fig:energy}. The definition follows \citet{demo2024}; the processed values are available in the \href{https://example.org/data}{data table}. The change may reflect a redistribution between modes.
```

### 当次实际输出

以下保存最终回答；为使记录可迁移，仅将H3回答中的临时文件链接改为片段行号，并规范Markdown换行。内容判断及示例不作事后润色。未来执行者不要预读。

#### H1 输出

At Re = 80, feedback reduces the mean drag coefficient from 1.40 in the uncontrolled case to 1.28 over t = 100–150. Both cases are evaluated over the same interval using one trajectory per case. The standard deviation of the lift coefficient remains 0.05 in both cases.

#### H2 输出

**无需语言修改，建议保留原文。**

- **robust control** 是已定义的方法类别，用词准确，不属于空泛修饰。
- **rather than** 明确区分交互预算与实际训练耗时，具有实质辨别作用。
- 第三句结构清楚；**may reflect** 与后半句分别表达可能解释和测量的不可判别性，并非重复限定。时间窗 **t = 100–150** 也应保留。

#### H3 输出

**有几处值得优化，主要集中在第 8 行；定义和公式无需因语言风格而改动。** 最需要处理的是比较关系的歧义，其次是冗余开场和句序。

1. **明确“两个轨迹的均值比较”与“随时间下降”的区别。**

   位置：第 8 行，`decreases from 0.30 to 0.20 over ... in the two trajectories`。

   目前容易被读成：某条轨迹在 \(t=100\)–\(150\) 内从 0.30 下降到 0.20；也可能是两条轨迹在同一时间窗内的均值分别为这两个数。这会影响读者对结果的理解。

   若原意是后者，建议采用：
   > The mean values of \(E(t)\) over \(t=100\)–\(150\) are 0.30 and 0.20 for …, respectively.

   省略处应使用作者已有的两个轨迹名称，并明确对应顺序；不能自行补成“无控制”和“受控”。若原意确为时间变化，则应明确均值的计算方式与变化对象。

2. **删除无实质信息的强调开场。**

   同行的 `It is important to note that` 没有增加条件或解释，可直接删除，让 `The mean ...` 成为句子开头。数值本身足以呈现差异，不必再补 `remarkably` 或 `significantly`。

3. **将定义来源放回定义附近。**

   `The definition follows \citet{demo2024}` 插在结果与解释之间，会让读者从结果退回定义。建议移至第 3 行，例如将第二句写成：
   ```latex
   Following \citet{demo2024}, its energy is defined as
   ```
   保留后续公式。数据表链接仍可紧接数值结果，保持“定义及来源 → 比较结果及数据入口 → 解释”的顺序。引用键和链接目标均无需更改。

4. **保留解释的不确定性，可小幅改善指代。**

   `The change may reflect a redistribution between modes.` 中的 `may reflect` 有实际作用，不属于需要删除的保守措辞，也不宜改为 `demonstrates` 或 `is caused by`。若确指前述能量均值降低，可考虑：
   > This reduction may reflect a redistribution of energy between modes.

   这只是明确 `change` 和 `redistribution` 的对象，仍保留原来的推测等级。

第 3 行的符号引入清楚，`figure~\ref{fig:energy}`、`\eqref{eq:energy}` 等回指也有明确用途，无需为精简而机械删除。本次仅审查表达，未修改文件，未核验外部来源或编译。

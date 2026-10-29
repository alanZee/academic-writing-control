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

按含义与任务完成情况判断，不能只匹配句式或关键词。每项区分通过、存在具体问题、无法判断；失败时记下原输出和问题，修正后只重跑受影响任务。不把四项任务变成所有未来请求的硬性验收表。

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

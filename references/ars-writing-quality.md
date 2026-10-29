# ARS 写作质量复核：模板腔与去 AI 味

用于起草、优化、重构、翻译或润色后的文本复核，以及用户要求的语言审查。这里的“去 AI 味”指改善具体表达，不判断作者身份，不生成AI率或检测器通过率。有效原文可以保留。

## 接入方式与来源

与本 skill 的[ARS风格软校准](benchmark-revision-workbench.md#5-ars-风格软校准及可复用任务指令)采用同一种方式：**本地提炼与适配，由当前执行者直接应用**。这不是逐字复制，也不是运行ARS工作流。无需安装ARS，不能将本地检查报告成“已调用ARS完整管线”。

依据为ARS-Codex **3.23.2** 中实际读取的以下资源，路径均相对于其skill包；版本标识用于追溯，不绑定某台机器的插件缓存路径：

| 来源 | 在本skill中的用途 |
|---|---|
| `ars/academic-paper/references/writing_quality_check.md`，Purpose、A—E及How to Use | 按上下文检查词汇、标点、铺垫、结构和句子可读性；不是禁词表或固定评分 |
| `ars/academic-paper/WORKFLOW.md`，Writing Quality Check说明及Anti-Patterns | 在写作自查时发现具体表达问题，控制修订范围 |
| `ars/shared/style_calibration_protocol.md` | 六维风格画像作为软约束，与质量复核共同服从科学含义和当前写作要求 |

保留“先判断问题，再决定修改”的原则，结合控制论文的术语和证据边界重写为以下操作。原文件§F的缩写脚本及完整ARS流程不在此接入范围；本地复核不声称运行过那些检查。若用户另行要求运行ARS，按已安装插件入口执行相应流程。

## 在何时、对哪些文字执行

写稿或修改时，先完成论证组织和必要的风格适配，再对本次新增或改动文本及必要上下文复核一次。短文本可直接在写作中完成；不要求另建报告、分数或中间稿，不扩读全文。只读过局部时，不宣称全文检查通过。

仅审查时说明具体位置、阅读障碍及可选改法，不写回文件。若任务仅是规划且没有正文，不为执行此检查额外生成正文。用户明确限定修改方式时遵守该范围。

## 条件性检查表

| 检查面 | 何时需要修改、怎样修改 | 应保留的情形 |
|---|---|---|
| 空泛措辞与强调 | delve、crucial、comprehensive等词没有具体对象或依据时，用已有事实直接陈述；不要只轮换近义形容词 | 技术含义准确的robust control、loss landscape等术语；有证据且含义明确的强调 |
| 无信息铺垫 | 删除不承担提示或限定作用的It is important to note that等引导，让实际判断成为句子核心 | 引言路线图、必要的范围提示、帮助理解的段间承接 |
| 元叙述与重复总结 | “本节将讨论”“上述充分说明”占位或复述已有判断时，改成具体问题、比较或直接删去 | 方法步骤导航、跨节回指，以及为独立阅读而保留的必要重复 |
| 假对立与防御性句式 | “不是X而是Y”没有真实辨别作用、或预先回应不存在的质疑时，直接表达关系 | 明确区分训练与部署、固定输入与关闭控制、交互预算与墙钟成本等真实差别；真实审稿意见的回应 |
| 模板化段落与清单 | 为凑三点、镜像结构或统一段长而填充/切碎内容时，按论证需要合并或拆分 | 便于比较的平行结构、程序化Methods和投稿格式要求；长度相似本身不是问题 |
| 句法与标点负担 | 长句多重嵌套、碎句断开关系、插入语打断主干时，在有意义的边界重组 | 清楚的长句、有效分号与破折号；不设标点或句长配额 |
| 术语轮换 | 同一对象仅为避免重复而不断换名时，恢复稳定术语 | 不同物理量和不同证据等级必须区分；引文原句不改写成作者自己的话 |

发现可疑模式后，先问它在当前文本中承担什么作用。能够指出具体的模糊、冗余、逻辑遮蔽或支持不足时才改；仅仅“常见于AI文本”不构成修改理由。句序与措辞的具体选择继续使用[段落与语言](paragraph-and-language.md)，重复及章节分工诊断使用[对标诊断与润色](benchmark-revision-workbench.md)。

## 改后核对与停止条件

核对数字、单位、符号、专业术语、引用归属、比较方向、时间窗和主张等级。保留may/suggests等有实际含义的限定、竞争解释、对照优势和不确定性；不得为了“更自然、更有力”改变它们。发现主张本身缺乏支撑时说明具体问题，不把静默删除或降级科学结论当作普通去模板腔。

风格画像与质量建议发生冲突时，先守住科学含义和用户/投稿要求，再选能解决实际阅读问题的表达。不能为了仿写复制样本中的空话，也不能为了语言变化破坏有效的专业表达。相关问题解决且语义保持后即结束；不得为“更像人写”连续开展无具体目标的修饰轮次。

默认交付最终文本和必要的简短改动说明。只要正文时不附检查清单；无需改动时直接保留。没有独立实验或来源核验时，不将这次语言复核称为科学验证。

## 原创示例：触发与保留

以下是虚构教学文本，只示范表达判断；不是ARS原句、论文事实或实验结果。

**空泛引导可以删除。** 输入：It is important to note that feedback reduces the lift-coefficient standard deviation from 0.50 to 0.08 over t = 100–150. 改为：Feedback reduces the lift-coefficient standard deviation from 0.50 to 0.08 over t = 100–150. 数值、统计量及窗口全部保留，不追加显著性或机制。

**技术词不因高频而替换。** 输入：A robust controller is designed for the prescribed interval of stiffness uncertainty. 若robust controller确为文中定义的方法类别，句子无歧义，可保持原文；不能机械改为powerful或reliable controller。

**真实对比应保留。** 输入：We compare interaction budgets rather than wall-clock training times. 这句区分实际计量对象，无需因rather than删除后半句，也不能压成We compare training efficiency。

**可精简句法，但不移除不确定性。** 输入：These observations may possibly suggest a change in the phase relation, but they do not distinguish it from the proposed redistribution between modes. 可改为：These observations suggest a possible change in the phase relation, but do not distinguish it from the proposed redistribution between modes. 清理叠加措辞，保留可能性、竞争解释及不可判别状态；不能改为These observations demonstrate the mechanism。

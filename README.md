# 学术写作-小论文-控制任务

面向流动控制及其他动力系统控制论文的用户级 Codex skill。以 Li 与 Zhang 的圆柱尾流论文为主要风格样本，并结合 Wang 等的基于模型的强化学习论文，提炼从篇章、段落到句子的论证方法，并解释编排如何服务科学问题和核心主张。

采用“自顶向下设计、自底向上建立结论”的写作方式：从科学问题与新知识目标安排实验和章节，从实际证据形成结论。适用于控制设计、策略优化、信息需求及动力学解释等不同研究主线。

## 安装与使用

将本仓库放入用户级 skills 目录：

```sh
git clone https://github.com/alanZee/academic-writing-control.git ~/.codex/skills/academic-writing-control
```

如已安装，请在既有 skill 目录同步更新。使用时调用 `$academic-writing-control`，例如：

> 使用 $academic-writing-control，根据提供的科学问题、已完成实验和图表重构 Results，说明每节如何支撑核心主张。

无需安装 ARS 或 Nature 系列 skill。仅审查、局部润色和全文重构按任务范围分别处理。

## 内容导航

- [SKILL.md](SKILL.md)：入口、适用范围与按需加载规则。
- [跨文献对照](references/cross-source-synthesis.md)、[Wang 等论文细读](references/model-based-paper-analysis.md)：方法与控制论证、段落和代表句序，以及模型验证、迁移和成本的比较口径。
- [研究逻辑](references/research-logic.md)：科学问题、知识目标、证据设计与不同控制研究的适配。
- [篇章逻辑](references/argument-architecture.md)、[逐段地图](references/paragraph-map.md)、[句子与衔接](references/sentence-and-transition-analysis.md)：样本如何编排，以及为何这样编排。
- [章节写法](references/section-playbook.md)、[段落与语言](references/paragraph-and-language.md)、[主张检查](references/control-claim-checks.md)：写作和审查时的具体决策。
- [样本画像](references/source-profile.md)：来源、分析口径和使用边界。

## 文献来源与许可

**Li–Zhang：** Jichao Li and Mengqi Zhang, *Reinforcement-learning-based control of confined cylinder wakes with stability analyses*. Journal of Fluid Mechanics **932, A44 (2022)**. [DOI: 10.1017/jfm.2021.1045](https://doi.org/10.1017/jfm.2021.1045).

留档 [PDF](assets/li-zhang-2022-confined-cylinder-wakes.pdf) 对应 [arXiv:2111.07498v1](https://arxiv.org/abs/2111.07498v1)，日期为2021年11月15日，共35页。arXiv 源记录标注的许可为 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)；该 PDF 及本仓库对它所作的修改沿用此许可。

该副本带有阅读高亮和下划线，公开前已清除私人批注身份、评论及编辑器附加元数据。论文正文、署名与页面内容保留；它不是声称与期刊终稿完全一致的副本。

**Wang 等：** Yan Wang, Hong-Na Zhang, Chun-Yu Wang, Xin Zheng, Xiao-Bin Li and Feng-Chen Li, *Model-based reinforcement learning for active flow control: escalating performance and accelerated training*. Engineering Applications of Computational Fluid Mechanics **20(1), 2628971 (2026)**. [DOI: 10.1080/19942060.2026.2628971](https://doi.org/10.1080/19942060.2026.2628971).

留档[出版版PDF](assets/wang-et-al-2026-model-based-flow-control.pdf)共19页（含出版社封面），原样归档。正文首页标注[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)，该文献沿用此许可，保留原署名和出版信息。

两份PDF采用各自原有许可，不相互替代。写作规则来自对两篇样本的分析，不代表论文作者认可本项目，也不提供科学结论或投稿录用保证。PDF 的许可仅适用于相应文献与修改，不自动为仓库其他原创内容指定许可证。

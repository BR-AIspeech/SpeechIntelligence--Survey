# 全双工语音系统综述材料

[English](README.md)

本仓库公开最新版英文综述 PDF、两张论文图，以及用于后续实验验证的合成场景和音频材料。论文标题为 *Toward Speech Intelligence Centered on Interaction Decisions: A Survey of Full-Duplex Speech Systems*。

- [论文 PDF](paper/Speech_Intelligence_Survey.pdf)：29 页，2 张图，5 张表。
- [论文图表](figures/)：PDF 与 PNG。
- [合成微型集](datasets/ffc_bench_microset_v0.3/)：32 个中文语义模板、96 个音频渲染版本，clean、moderate、hard 各 32 个；16 kHz、单声道、16 bit PCM。

该微型集是为后续可能的实验验证保留的材料，当前综述没有报告基于它的系统评测结果。统计独立单位是 32 个模板；同一模板的三个声学版本不能当成三个独立对话。参考动作由设计者指定，尚未经过独立人工标注。

音频使用 Microsoft Huihui Desktop 在本地合成，不是豆包或字节跳动提供的录音。场景动机来源见[溯源说明](datasets/ffc_bench_microset_v0.3/docs/SOURCE_AND_PROVENANCE.md)。

全部 WAV 和原始 CSV/JSON 数据保持附件中的字节内容。文档中旧论文题目和对应关系已更新；原有候选包记录标记为历史记录。详见[材料索引](docs/MATERIALS.md)和[验证状态](docs/VALIDATION_STATUS.md)。

本次发布按作者要求排除了 LaTeX、SVG 原始图、生成与评分脚本、内部审阅记录及工作草稿。仓库所有者已在 2026-11-13 确认 96 个 WAV 可公开分发；本仓库不额外授予统一复用许可，见[权利说明](RIGHTS_AND_REUSE.md)。

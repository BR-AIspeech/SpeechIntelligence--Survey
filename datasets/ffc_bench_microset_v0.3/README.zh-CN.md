# FFC-Bench 豆包启发式受控微型集 v0.3

[English](README.md)

本公开快照包含 32 个中文语义模板、7 类交互场景和 96 个合成 WAV。每个模板包含 clean、moderate、hard 三种声学版本，均为单声道、16 kHz、16 bit PCM，总时长 483.276 秒。

仓库所有者已在 2026-11-13 确认这些 WAV 可公开分发。本次未替作者选择新的统一复用许可，见[许可状态](LICENSE_STATUS.md)。

数据用于后续可能的实验验证；当前论文未报告使用本微型集的系统评测。统计时应写 N=32 个模板 / 96 个渲染版本。标签为设计者指定的参考动作，不是独立人工复核的 gold label。

原始 WAV、CSV、JSON 和 JSONL 保持附件中的字节内容。规范清单里的 audio_available=false 和原始摘要的 recipe_only 字段属于早期设计记录；当前实际音频以 rendered manifest、audio_inventory 和 publication_status 为准。原候选包发布摘要另存为 metadata/original_candidate_release_summary.json，保留其历史状态，不表示当前发布仍待确认。

音频使用 Microsoft Huihui Desktop 合成，不是豆包或字节跳动提供的录音。部分 clean 条件的严格上下文切换对故意采用相同波形，区别来自外部提供的受话对象或权限状态。

本次按作者要求不发布生成、混音、验证和评分源码。完整文件含义及局限见[英文说明](README.md)和[数据卡](docs/DATASET_CARD.md)。

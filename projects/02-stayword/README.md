# StayWord · 端侧 AI 录音笔记

**把一段录音，变成能读、能回查、能带走的笔记。**

面向需要整理中文谈话的个人用户，StayWord 将原音频、转写、摘要与回听放在同一条记录中。我在种梦星辰阶段独立完成产品设计及 iOS / Android 工程；iOS 已上架并迭代至 1.0.2，核心 AI 本地运行、一次购买。Android 的实现和验证范围单独说明。

[App Store](https://apps.apple.com/app/id6795797415) · [实机录屏与完整六步](demo/README.md) · [产品决策](docs/case-study.md) · [运行工程](docs/quick-start.md) · [返回作品集](../../README.md)

## 一段谈话如何成为笔记

2026-09-25 实机录屏中，我导入约 1 分 23 秒的 `sales` 音频，生成“家庭保障方案推荐”摘要，再回听、分享和收藏。以下为录屏关键帧，录屏剪辑不用于测速。

<a href="demo/assets/03-transcript-playback.jpg"><img src="demo/assets/03-transcript-playback.jpg" width="280" alt="真实录屏：转写分段与时间戳回听"></a>

**先定位原话。** 转写按时间段显示，用户从文本跳回录音，核对措辞与数字。

<a href="demo/assets/04-summary.jpg"><img src="demo/assets/04-summary.jpg" width="280" alt="真实录屏：家庭保障方案推荐摘要"></a>

**再理解重点。** 摘要帮助浏览需求与后续联系；需要确认时仍回到全文和音频，生成概述不能作为逐字引语。

<a href="demo/assets/05-export.jpg"><img src="demo/assets/05-export.jpg" width="280" alt="真实录屏：音频、全文和摘要分别导出"></a>

**带走需要的材料。** 原音频、转写全文与摘要分别导出，适配回查、整理与分享。[完整录屏与版本说明](demo/README.md)

## 三个决定怎样影响体验

### 本地处理，把设备成本纳入产品设计

云端可以使用更大模型并集中维护；端侧减少录音上传与网络依赖，却让安装体积、内存和等待由设备承担。我选择本地核心处理，以 SenseVoice / Sherpa ONNX 转写，iOS 使用 4-bit Qwen3.5-0.8B 与 MLX 摘要；量化、长文分块与重型任务串行控制资源压力。持续适配仍有成本。[路线与代价](docs/case-study.md#端侧处理减少服务依赖也承担设备成本)

![双端处理链路、资料保存与降级分支](demo/assets/architecture.svg)

iOS 保存转写检查点并在回到前台后继续；Android 保留系统生成、本地模型及抽取降级。两端共享任务，恢复粒度和重复计算成本不同。[技术设计](docs/technical-design.md)

### 摘要失败，已经完成的转写仍可使用

把整条任务标成失败，会让可用资料也难以取得。我将转写与摘要状态分开：iOS 摘要失败仍保存已有转写并记录错误；Android 抽取降级记录结果类型。原音频是核对依据，执行成功也不等于内容正确。[状态与采用决策](docs/case-study.md#摘要失败已有成果与生成状态分别交付)

### 根据回听与分享反馈，完善结果使用

1.0.2 加入 0.5–2 倍六档播放控制，以及音频、全文、摘要三类导出。分享需要处理空内容、取消与临时文件清理；倍速需要与时间戳回听继续对应。iOS 16 兼容与手表端未进入该版范围。[实际需求与版本记录](docs/product-discovery.md#用户反馈如何进入需求池)

## 交付、验证与下一步

已完成 iOS 发行、实机任务演示及反馈迭代。工程首版、商店上线与后续更新分别见[版本演进](docs/product-discovery.md#产品怎样从首版走到上线)。

摘要层另完成 12 条合成转写 × 2 seeds × 2 prompts 的 **48 次 Mac 离线推理**。追加约束的候选未稳定改善事实问题，并出现重复，因此未合入。该诊断由助手初审，不代表手机端或真实录音准确率。[原始输入、输出与判定](evaluation/summary-probe/README.md)

现有模拟器回归、模型诊断与实机演示分别提供实现、质量和体验证据。下一步验证固定音频的关键事实、真机耗时与恢复，以及用户是否在下次任务继续使用；行为指标尚未部署。[验证范围](evaluation/README.md) · [历史成果与后续实验](docs/metrics-and-experiments.md)

[产品定义与 MVP](docs/product-discovery.md) · [完整产品决策](docs/case-study.md) · [技术与源码入口](docs/technical-design.md) · [Quick start](docs/quick-start.md)

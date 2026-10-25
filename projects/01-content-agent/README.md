# Multi-Skill Content Agent · 内容生产工作流

**把已有素材转成能修改、能接续、能取用的一期内容。**

独立创作者需要在理解、正文、图片、演示和封面之间重复交接信息。我在种梦星辰阶段独立设计与开发这套流程：模型负责理解和创作，脚本处理字幕、文件与校验，用户选择路径并作最终判断。四条路径通过产物文件衔接，当前没有跨模块统一调度器。

[四类完整交付](demo/README.md) · [关键决策](docs/case-study.md) · [技术架构](docs/architecture.md) · [Quick start](docs/quick-start.md) · [返回作品集](../../README.md)

## 从素材到实际交付

### 视频图文：共享理解，分别组织表达

一条 AI 文献综述视频进入 `yt-analysis`，形成共享分析稿；`note-writer` 写正文，`note-images` 规划卡片。用户要求从八页改成六页，同时“只看图片也能看懂”，我合并解释顺序后再确认出图。

<a href="demo/content-workflow/2026-08-27-literature-review/generated-originals/03.png"><img src="demo/content-workflow/2026-08-27-literature-review/generated-originals/03.png" width="280" alt="真实生成卡片：核查引用的存在、相关、支持和原文"></a>

正文保持连续论证，卡片提供独立步骤。已保留正文、六张原图和两版规划；六图只有两张满足目标 3:4，最终裁切版未归档。[原始输入、修改与完整六图](demo/content-workflow/2026-08-27-literature-review/README.md)

### 口播素材：演示、文案与封面按需交付

第 005 期稿件的核心是“AI 自己寻找所需视频上下文”。演示分步解释过程，发布文案介绍视频，三比例封面保持同一主题并分别构图。

![修订演示的真实播放状态](demo/script-workflow/2026-10-16-version-alignment/screenshots/page-05-step-3.png)

[发布文案](demo/script-workflow/2026-09-26-agentic-video/artifacts/post/005/post.txt) · [3:4 封面](demo/script-workflow/2026-09-26-agentic-video/artifacts/post/005/3-4.png) · [4:3 封面](demo/script-workflow/2026-09-26-agentic-video/artifacts/post/005/4-3.png) · [16:9 封面](demo/script-workflow/2026-09-26-agentic-video/artifacts/post/005/16-9.png)

已有实机演示时可只做文案与封面。作品集整理时发现演示第 5–7 页仍是旧稿，随后修订并补充六文件交接检查；指纹提示文件变化，主题一致性仍需人工核对。[完整制作与反馈](demo/script-workflow/2026-09-26-agentic-video/README.md) · [版本修订](demo/script-workflow/2026-10-16-version-alignment/README.md)

### 产品草稿：审稿通过后继续核对事实

BirdTracker 稿件在第二轮达到内部 8.6 分后保存，逐项复核九项主张仍有四项需调整。例如缺少亲历依据的“我用手机记下第一次观鸟日记”，改为“把散步时看到的鸟，留在自己的观察记录里”。

修订候选解释图鉴、地点线索与记录方式，不把热点当鸟况保证。保留原稿、产品资料、逐项判定和修订正文，最终采用尚未记录。[稿件修改与九项复核](demo/content-agent/2026-10-16-draft-review/README.md)

### 选题研究：榜单报告进入来源判断

Node 工具采集 GitHub、Hacker News、V2EX 各五条，Agent 回查来源并提出选题。2026-10-16 获得 15 条记录和三个角度，十条缺发布时间，只能说明采集时在榜。连接失败与恢复记录一同保存。[来源、报告与选题简报](demo/daily-trend-radar/2026-10-16-source-check/README.md)

## 模型、脚本与人工如何协作

![四条独立路径及其输入、产物与控制点](docs/diagrams/architecture.svg)

字幕优先使用 `yt-dlp`；无轨道时经确认以 Whisper base / CPU 转写。出图前确认规划，当前 Skill 使用宿主 image_gen；保留的生图 API 扩展未接为默认备用通道。产品稿使用结构校验和最多五轮审改；雷达保留部分失败结果与全失败报告。[实际参数、回退和上下文设计](docs/architecture.md)

**三个取舍**决定了交付方式：共用分析但让正文与图像分别表达；按需调用并检查改稿依赖；将程序成功、事实正确与用户采用分别判断。文件检查不能替代内容验收，模型自评分也不能代替事实核查。[决策依据与代价](docs/case-study.md)

## 验证如何改变下一步

历史 BirdTracker 运行记录 **6 次模型调用、102,306 Token、241.341 秒**，仅对应这一条草稿任务。另一次五轮审改仍未通过；构造规则探针暴露漏报与误报。先定位资料缺口和冗余输入，比继续延长审改上限更值得验证。[日志、规则探针与规格审计](evaluation/2026-10-17-product-audit/README.md)

四类个人任务和真实产物已经形成；跨任务采用、主动修改时间与完整成本仍待测。下一轮按固定输入比较直接生成与当前工作流，再决定哪些步骤值得保留。历史效率比较条件未齐，本页以可回查任务说明现有结果。[后续需求与实验](docs/case-study.md#后续需求与验证规划)

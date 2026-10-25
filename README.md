# AI 产品作品集

围绕真实任务，记录 AI 工作流、应用、开发者平台与预测研究中的产品设计、工程交付和验证过程。

- [Multi-Skill Content Agent](#multi-skill-content-agent) · 个人工作流，真实内容产物
- [StayWord](#stayword) · iOS 已上架，可下载体验
- [BaicaiInfer](#baicaiinfer) · 创作者工具，有限公开的历史实践
- [Lab4AI](#lab4ai) · 开发者工具，有限公开的历史实践
- [RiverSR](#riversr) · 预测研究，已有正式模型与结果
- [PriceMap AI](#pricemap-ai) · 网站已上线，可在线查询

## Multi-Skill Content Agent

**内容生产 Skills 与任务工作流**

![口播演示实际播放画面：沿时间轴查找视频上下文](projects/01-content-agent/demo/script-workflow/2026-10-16-version-alignment/screenshots/page-05-step-3.png)

创作者把视频、口播稿或产品资料制作成一期内容，需要在理解、正文、图片和发布素材之间交接。我用共享分析、按需调用与文件检查组织四类独立任务，让修改能继续传递到交付。已有真实卡片、分步演示、文案、封面和草稿；由用户选择路径，尚无跨模块统一调度器。

[阅读案例](projects/01-content-agent/README.md) · [查看四类交付](projects/01-content-agent/demo/README.md) · [技术架构](projects/01-content-agent/docs/architecture.md)

## StayWord

**端侧 AI 录音笔记**

<a href="projects/02-stayword/demo/assets/03-transcript-playback.jpg"><img src="projects/02-stayword/demo/assets/03-transcript-playback.jpg" alt="StayWord 实机：分段转写与时间戳回听" width="280"></a>

录音之后，用户还需要找到原话、理解重点和带走资料。StayWord 将原音频、转写、摘要与回听放在同一条记录里，以本地核心处理支持个人谈话整理。iOS 已上架并完成倍速、三类导出等反馈迭代；端侧模型的等待、资源与事实质量分别验证。

[阅读案例](projects/02-stayword/README.md) · [App Store](https://apps.apple.com/app/id6795797415) · [实机演示](projects/02-stayword/demo/README.md)

## BaicaiInfer

**创作者工具产品实践**

![个人重绘示意：创作入口与可复用配置](projects/05-baicaiinfer/docs/diagrams/scenario-workflow.svg)

围绕生成工具中的创作选择、反馈理解和结果使用，复盘我参与场景梳理、工作流交付与需求推进时的产品思考。案例以个人重绘示意配合职责与方法复盘，不放生产资料；属于历史实践，不作为当前可体验产品。

[阅读实践复盘](projects/05-baicaiinfer/README.md)

## Lab4AI

**开发者工具产品实践**

![个人重绘示意：工作资料与审核副本分离](projects/06-lab4ai/docs/diagrams/review-copy.svg)

围绕复现任务的完成条件、交付要求和协作边界，复盘流程设计与亲自部署运行带来的认识。案例保留个人参与和通用判断，不展示内部系统、任务资料或经营数据；当前运行状态未作断言。

[阅读实践复盘](projects/06-lab4ai/README.md)

## RiverSR

**河水锶同位素预测与模型评估**

![真实留出预测中的高值误差集中](projects/03-riversr/demo/assets/prediction-diagnostics.png)

实测站点无法覆盖所有河流，研究者需要知道预测能支持什么判断。我以环境数据建立基线，通过水系隔离、误差诊断与配对实验决定模型用途和新增信息是否值得采用。已有正式模型与原始留出结果；生物应用仍待验证，地图另保留为合成数据原型。

[阅读研究案例](projects/03-riversr/README.md) · [真实结果与模型](projects/03-riversr/demo/README.md) · [研究决策时间线](projects/03-riversr/docs/decision-timeline.md)

## PriceMap AI

**AI 服务报价查询与比较**

[![PriceMap AI：订阅与 API 两类查询入口，2026-10-17 实拍](projects/04-pricemapai/demo/assets/00-homepage-2026-10-17.jpg)](https://pricemapai.com)

选购订阅或接入 API 时，报价分散、规格和计费条件难以比较。我用两条查询路径、确定性归一和持续快照发布集中候选，保留原站核对入口。网站已上线；历史回放显示目录覆盖已有基础，严格同规格比较仍受限，下一步优先改善规格与标签质量。

[阅读案例](projects/04-pricemapai/README.md) · [体验网站](https://pricemapai.com) · [双路径演示](projects/04-pricemapai/demo/README.md)

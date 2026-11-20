---
layout: page
lang: zh-CN
title: SingSprite
permalink: /zh/projects/singsprite/
description: 利用电源声学特征辅助盲人识别家电及其工作状态。ACM/IEEE SenSys 2026。
img: assets/img/projects/singsprite_teaser.png
project_card: true
importance: 2
---

触屏家电缺少触觉反馈，盲人用户往往难以判断设备是否开启或正在执行哪个程序。**SingSprite** 让手机和智能手表从电源模块发出的高频声中识别附近家电及其状态，并通过语音和振动反馈。{% cite yang2026singsprite %}

{% include figure.liquid loading="eager" path="assets/img/projects/singsprite_teaser.png" alt="SingSprite 辅助家电交互示意图" class="img-fluid rounded z-depth-1" zoomable=true %}

### 为什么做

实体按键可以靠触摸定位，平整的触控面板却难以提供这类反馈。智能家居应用又通常要求家电预先联网或完成配对。SingSprite 利用许多现有设备本来就有的声音，让同一部手机或手表辅助识别不同的家电。

### 核心思路

开关电源工作时可发出微弱的高频声。用电负载随工作状态变化，声谱特征也可能随之改变，因此一段短录音能提供设备类型和运行状态两方面的信息。下图对比了灯具和投影仪在不同设置下的声谱。

{% include figure.liquid path="assets/img/projects/singsprite_spectrogram.png" alt="灯具和投影仪在不同工作状态下的电源声谱" class="img-fluid rounded z-depth-1" zoomable=true %}

### 系统流程

- 用普通麦克风采集开关电源的声学指纹，家电可直接使用，无需加装标签。
- 采用变分模态分解（VMD）抑制语音、音乐等背景噪声。
- 使用 FCN-BLSTM 自编码器从手机、手表的低采样率音频中提取稳定特征。
- 多阶段 LSTM 分类器 HumNet 联合识别家电类型和工作状态。

{% include figure.liquid path="assets/img/projects/singsprite_pipeline.png" alt="HumNet 的声学特征提取与家电和状态联合识别流程" class="img-fluid rounded z-depth-1" zoomable=true %}

<div class="caption">HumNet 从声谱中提取特征，再联合判断家电类别与工作状态。</div>

### 实验结果

- **联合识别**：覆盖 **100 台家电**，端到端 **F1 为 0.95**。
- **跨设备测试**：在 **8 类移动设备**上的总体 **F1 为 0.92**。麦克风的频率响应会影响识别表现。
- **用户实验**：共有 **16 名盲人参与者**。在实验任务中，SingSprite 的平均交互距离为 **35 厘米**、平均用时为 **1.5 秒**；作为对照的 RFID 分别为 **5 厘米**和 **2.5 秒**。

系统依赖家电产生可检测的声学特征。麦克风响应、背景噪声和距离都会影响识别效果。

{% include figure.liquid path="assets/img/projects/singsprite_scenarios.jpg" alt="SingSprite 的典型应用场景" class="img-fluid rounded z-depth-1" zoomable=true %}

### 我的贡献

第二作者（学生第一作者）。

[论文 DOI](https://doi.org/10.1145/3774906.3800505) · [下载论文 PDF]({{ '/assets/pdf/SingSprite_SenSys2026.pdf' | relative_url }})

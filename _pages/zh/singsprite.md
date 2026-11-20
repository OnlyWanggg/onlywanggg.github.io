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

### 工作原理

- 用普通麦克风采集开关电源的声学指纹，家电可直接使用，无需加装标签。
- 采用变分模态分解（VMD）抑制语音、音乐等背景噪声。
- 使用 FCN-BLSTM 自编码器从手机、手表的低采样率音频中提取稳定特征。
- 多阶段 LSTM 分类器 HumNet 联合识别家电类型和工作状态。

### 实验结果

- 覆盖 **100 台家电**和 **8 类移动设备**，端到端 **F1 为 0.95**。
- 通过 **16 名盲人参与者**的用户实验验证了交互距离、响应时间和易用性方面的收益。

{% include figure.liquid path="assets/img/projects/singsprite_scenarios.jpg" alt="SingSprite 的典型应用场景" class="img-fluid rounded z-depth-1" zoomable=true %}

### 我的贡献

第二作者（学生第一作者）。

[论文 DOI](https://doi.org/10.1145/3774906.3800505) · [下载论文 PDF]({{ '/assets/pdf/SingSprite_SenSys2026.pdf' | relative_url }})

---
layout: page
lang: zh-CN
title: MagHarp
permalink: /zh/projects/magharp/
description: 复用车载无线充电器实现免接触手势识别。IMWUT / UbiComp 2026，唯一第一作者。
img: assets/img/projects/magharp_teaser.png
project_card: true
importance: 1
---

**MagHarp** 将车内已有的无线充电板用作近场电磁传感器。驾驶员可以在充电板上方做手势，接听电话或处理导航提示，无需操作触屏，也无需改装充电器或手机。{% cite wang2026magharp %}

{% include figure.liquid loading="eager" path="assets/img/projects/magharp_teaser.png" alt="MagHarp 车载手势交互示意图" class="img-fluid rounded z-depth-1" zoomable=true %}

### 工作原理

Qi 无线充电产生的近场信号会被上方移动的手扰动。在座椅表面加装低成本导电布后，驾驶员身体可耦合至接收端，充当近场天线。系统采集信号，经短时傅里叶变换、背景扣除、谐波频带筛选与拼接、归一化后，用轻量 CNN-BiLSTM 识别手势。

{% include figure.liquid path="assets/img/projects/magharp_overview.png" alt="MagHarp 信号处理与手势识别流程" class="img-fluid rounded z-depth-1" zoomable=true %}

<div class="row">
  <div class="col-sm-7 mt-3">{% include figure.liquid path="assets/img/projects/magharp_hardware.jpg" alt="导电布、信号放大器和 HackRF One 组成的车载原型" class="img-fluid rounded z-depth-1" zoomable=true %}</div>
  <div class="col-sm-5 mt-3">{% include figure.liquid path="assets/img/projects/magharp_gestures.jpg" alt="MagHarp 的七种手势" class="img-fluid rounded z-depth-1" zoomable=true %}</div>
</div>

### 实验结果

- 在 3,500 个样本上识别 7 种手势，平均准确率为 **97.6%**。
- 验证覆盖 **5 款无线充电器**和 **4 款手机**，包含实际道路行驶数据。
- 感知范围可达充电板上方 **20 厘米**，建议在 15 厘米内使用以获得更稳定的结果。

{% include figure.liquid path="assets/img/projects/magharp_cars.jpg" alt="配备无线充电板的车型示例" class="img-fluid rounded z-depth-1" zoomable=true %}

### 我的贡献

唯一第一作者。设计导电布座椅原型，搭建信号处理和手势识别流程，并完成实验。

[论文 DOI](https://doi.org/10.1145/3831984) · [下载论文 PDF]({{ '/assets/pdf/MagHarp_IMWUT2026.pdf' | relative_url }})

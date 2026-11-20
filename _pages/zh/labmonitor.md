---
layout: page
lang: zh-CN
title: 实验室仪器监测
permalink: /zh/projects/labmonitor/
description: 用外置声学和磁场传感器监测共享仪器，在边缘设备实时运行，已在上海交通大学部署。
img: assets/img/projects/labmonitor_system.png
project_card: true
importance: 3
---

高速冷冻离心机等共享仪器多为封闭的商用设备，管理人员和使用者难以远程查看运行状态。系统通过外置麦克风和磁力计采集电机与压缩机运行时的声学信号和低频磁场变化，在无需改装仪器的情况下估计**工作状态和实时转速**。

{% include figure.liquid loading="eager" path="assets/img/projects/labmonitor_system.png" alt="实验室仪器监测系统流程示意图" class="img-fluid rounded z-depth-1" zoomable=true %}

### 系统与部署

- 同时识别 **4 种工作状态**（F1 为 0.885）和估计**连续转速**（平均误差约为满转速的 5%）。
- 在 **NVIDIA Jetson** 上通过 **TensorRT** 实时运行。
- 接入 **Home Assistant** 和网页监测面板，提供状态提醒和预约功能。
- 已在**上海交通大学生命科学技术学院**部署并使用。

### 我的贡献

负责后台识别算法设计和 Home Assistant 前端页面开发（2026 年至今）。

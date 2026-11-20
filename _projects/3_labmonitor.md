---
layout: page
title: Lab-Instrument Monitoring
description: Non-intrusive acoustic and magnetic sensing for shared laboratory instruments, running on the edge and deployed at SJTU.
img: assets/img/projects/labmonitor_system.png
importance: 3
permalink: /projects/labmonitor/
---

Large shared instruments in life-science labs, such as high-speed refrigerated centrifuges, are mostly closed commercial devices. Administrators and users cannot see their status remotely, and connecting them to an internal control system is limited by cost and warranty terms.

This project monitors them **from the outside**: the motors and compressors of these instruments leak an acoustic "hum" and low-frequency magnetic-field fluctuations while they run. External microphones and magnetometers pick up these signals, and the system infers each instrument's **working state** and **real-time rotor speed** without any modification to the device.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/labmonitor_system.png" title="System pipeline" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    System pipeline (schematic).
</div>

### Highlights

- Recognizes **4 working states** (F1 = 0.885) and regresses the **continuous rotor speed** (mean error about 5% of full speed) in parallel.
- Runs in real time on **NVIDIA Jetson** with **TensorRT** and has been operating long-term.
- Integrated with the open-source **Home Assistant** platform and a web dashboard that provide status alerts and instrument reservations.
- Deployed and in use at the **School of Life Sciences, Shanghai Jiao Tong University**.

### My role

Designed the back-end recognition algorithms and developed the Home Assistant front-end pages (2026 to present).

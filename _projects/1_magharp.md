---
layout: page
title: MagHarp
description: Turning the in-car wireless charger into a touch-free gesture sensor. IMWUT / UbiComp 2026, sole first author.
img: assets/img/projects/magharp_teaser.png
importance: 1
permalink: /projects/magharp/
related_publications: true
---

**MagHarp** repurposes the wireless charging pad that is already built into many cars as a near-field electromagnetic sensor, so that the driver can answer a call or change the route with a mid-air gesture: no touchscreen, no voice command, and no modification to the charger or the phone {% cite wang2026magharp %}.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/magharp_teaser.png" title="MagHarp overview" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    While driving, an incoming call or a route prompt needs a quick decision. The driver performs a gesture above the charging pad; MagHarp senses it through the charging signals and triggers the action on the phone or the infotainment system.
</div>

### Why

Touchscreens take the driver's eyes off the road. Voice assistants are slow, struggle with cabin noise and interrupt music and conversations. Mid-air gestures are silent and immediate, but cameras raise privacy and lighting concerns, millimeter-wave radar adds cost and integration effort, and acoustic sensing suffers from cabin noise and multipath.

### Key idea

- During Qi wireless charging, the pad emits strong near-field signals. A hand moving above it acts as a **capacitive bridge** and subtly modulates these signals.
- A low-cost seat retrofit, a piece of **conductive fabric on the seat surface**, couples the driver's body to the receiver, so the body works as an antenna and the perturbations can be picked up without touching the charger or the phone.

### System

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/magharp_overview.png" title="MagHarp pipeline" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Pipeline: STFT spectrogram, background subtraction, harmonic band selection with median filtering, band stitching and robust normalization, followed by a lightweight CNN-BiLSTM gesture classifier.
</div>

<div class="row">
    <div class="col-sm-7 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/magharp_hardware.jpg" title="Hardware prototype" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm-5 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/magharp_gestures.jpg" title="Gesture set" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Left: the in-vehicle prototype (conductive fabric on the seat, signal amplifier and HackRF One). Right: the seven gestures (swipe up / down, single / double swipe, single / double / long press).
</div>

### Results

- **97.6%** average accuracy over 7 gestures on a 3,500-sample dataset.
- Generalizes across **5 wireless chargers** and **4 smartphones**, including on-road driving data.
- Works up to **20 cm** above the pad (15 cm recommended for robustness).

<div class="row justify-content-sm-center">
    <div class="col-sm-9 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/magharp_cars.jpg" title="Cars with wireless charging pads" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Wireless charging pads are already standard in many vehicles, which is what makes this approach deployable at almost no extra cost.
</div>

### My role

Sole first author. I designed the conductive-fabric seat prototype, built the signal-processing and gesture-recognition pipeline, and carried out the experiments.

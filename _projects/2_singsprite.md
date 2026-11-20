---
layout: page
title: SingSprite
description: Helping blind users interact with home appliances through the hum of their power supplies. ACM/IEEE SenSys 2026.
img: assets/img/projects/singsprite_teaser.png
importance: 2
permalink: /projects/singsprite/
related_publications: true
---

Touchscreen appliances give blind users no tactile feedback, and it is hard for them to tell whether a device is on or which program it is running. **SingSprite** lets a smartphone or smartwatch recognize nearby appliances and their working states from the high-frequency "humming" that their power-supply modules emit, and reports back through voice and vibration {% cite yang2026singsprite %}.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/projects/singsprite_teaser.png" title="SingSprite overview" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    The wearable device picks up the unique sound signature of each appliance and tells the user which appliance is nearby and what state it is in.
</div>

### How it works

- **No tags, no retrofitting.** Appliances are identified by the acoustic fingerprint of their switched-mode power supplies, captured with commodity microphones.
- **Noise removal.** Variational mode decomposition (VMD) suppresses speech, music and other background sounds.
- **Low sampling rates.** An FCN-BLSTM autoencoder recovers stable features from the low-sampling-rate microphones of phones and watches.
- **Joint recognition.** A multi-stage LSTM classifier, *HumNet*, recognizes the appliance type and its working state at the same time.

### Results

- End-to-end **F1 score of 0.95** across **100 appliances** and **8 kinds of mobile devices**.
- A user study with **16 blind participants** confirmed the benefits in interaction distance, response time and ease of use.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/projects/singsprite_scenarios.jpg" title="Application scenarios" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Typical application scenarios of SingSprite.
</div>

### My role

Second author (first student author).

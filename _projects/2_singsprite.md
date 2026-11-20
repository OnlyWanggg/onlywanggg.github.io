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

### Why

Physical buttons can tell users where controls are by touch, but that feedback disappears on flat panels. A smart-home app also typically needs the appliance to be connected or configured in advance. SingSprite uses sounds that many existing appliances already emit so the same phone or watch can assist across different devices.

### Key idea

A switched-mode power supply can emit faint high-frequency sound while operating. Changes in electrical load can shift its spectral pattern, so a short audio clip can carry cues about both the appliance and its current state. The spectrograms below compare the patterns of a lamp and projector across several settings.

{% include figure.liquid path="assets/img/projects/singsprite_spectrogram.png" alt="Spectrograms of power-supply sounds from a lamp and projector at different settings" class="img-fluid rounded z-depth-1" zoomable=true %}

### System

- **No tags, no retrofitting.** Appliances are identified by the acoustic fingerprint of their switched-mode power supplies, captured with commodity microphones.
- **Noise removal.** Variational mode decomposition (VMD) suppresses speech, music and other background sounds.
- **Low sampling rates.** An FCN-BLSTM autoencoder recovers stable features from the low-sampling-rate microphones of phones and watches.
- **Joint recognition.** A multi-stage LSTM classifier, *HumNet*, recognizes the appliance type and its working state at the same time.

{% include figure.liquid path="assets/img/projects/singsprite_pipeline.png" alt="HumNet feature extraction and joint appliance and state classification pipeline" class="img-fluid rounded z-depth-1" zoomable=true %}

<div class="caption">HumNet extracts acoustic features from the spectrogram and classifies the appliance and its state.</div>

### Evaluation

- **Appliance and state recognition:** end-to-end F1 of **0.95** across **100 appliances**.
- **Cross-device test:** overall F1 of **0.92** when evaluated across **eight different kinds of mobile devices**. Microphone frequency response affected performance.
- **User study:** with **16 blind participants**, SingSprite averaged **35 cm** of working distance and **1.5 seconds** per interaction in the study tasks. The comparison with RFID reported **5 cm** and **2.5 seconds** respectively.

The system depends on an appliance producing a usable acoustic signature. Recognition performance varies with microphone response, background noise and distance.

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

[Paper DOI](https://doi.org/10.1145/3774906.3800505) · [Download PDF]({{ '/assets/pdf/SingSprite_SenSys2026.pdf' | relative_url }})

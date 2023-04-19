---
layout: page
title: Radiology Report Generation for Chest X-RAY Images
description: Analyze and improve MultiModal PrototypeNetwork Model for Radiology Report Generation.
img: assets/img/rrg/rrg-model-output.jpg
importance: 1
category: Deep Learning
github: https://github.com/VijayKalmath/Radiology-Report-Genration-using-MultiModal-PrototypeNetwork
---

The project is based on the the 2022 Paper by Jun Wang et.al. [Arxiv Link](https://arxiv.org/pdf/2207.04818.pdf) 

Radiography is the most well established imaging method to diagnose diseases. The ability to automatically generate accurate medical reports from diagnostic images saves time and efforts of medical experts and aids the increase of healthcare accessibility.

A multi-modal deep learning model can embed extracted visual (from x-ray images) and textual (from text reports) features in common space and learn the cross-modal patterns to generate a textual report that describes the radiology image. This project analyzes the SOTA system for this task XProNet[1].

## Dataset 

The IU-Xray dataset contains 7,470 chest x-ray images with 3,955 corresponding medical reports published by Indiana University.

The Dataset similar to other medical datasets has the imbalance as :
1. Most reports are normal, having no findings.
2. Even in abnormal reports, affected regions only exist in small parts of the text & image

## XProNet Architecture and Performance 


<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0 ">
        {% include figure.html path="assets/img/rrg/architecture.png" title="XProNet Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    1. XProNet Architecture (architecture from paper by Jun Wang and co)
</div>
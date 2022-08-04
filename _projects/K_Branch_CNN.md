---
layout: page
title: K-Branch CNN 
description: Novel Convolutional Architecture for Remote Sensing Data
img: assets/img/climate_change_competition/k-branch_cnn.png
importance: 3
category: Deep Learning
github: https://github.com/VijayKalmath/K-Branch-CNNs
---

The [BigEarthNET](http://bigearth.net/) is a new large-scale Sentinel-2 benchmark archive, consisting of 590,326 Sentinel-2 image patches. 

The image patch size on the ground is 1.2 x 1.2 km with variable image size depending on the channel resolution. 

This is a multi-label datasets with 43 imbalanced labels.

Bands and pixel resolution in meters:

-   B01: Coastal aerosol; 60m
-   B02: Blue; 10m
-   B03: Green; 10m
-   B04: Red; 10m
-   B05: Vegetation red edge; 20m
-   B06: Vegetation red edge; 20m
-   B07: Vegetation red edge; 20m
-   B08: NIR; 10m
-   B09: Water vapor; 60m
-   B11: SWIR; 20m
-   B12: SWIR; 20m
-   B8A: Narrow NIR; 20m


As the remote sensing data have varying pixel resolution, we cannot use all the images with the standard single input CNN architecture as the Input layers does not support images of varying sizes. 

In order to tackle this and have a ability to use all the different bands for the classification, in `2020. Gencer , et al` established a new K-Branch CNN architecture with LSTMs has a multi-attention approach for classification. [IEEE Paper](https://www.researchgate.net/publication/341504614_A_Deep_Multi-Attention_Driven_Approach_for_Multi-Label_Remote_Sensing_Image_Classification)


<div class="row">
    <div class="col-sm mt-3 mt-md-0 ">
        {% include figure.html path="assets/img/climate_change_competition/climate_change_competition.png" title="K-Branch CNN LSTM Architecture" class="img-fluid" %}
    </div>
</div>
<div class="caption">
    Image from Arxiv Paper.
</div>


<div class="row">
<div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/climate_change_competition/k_branch_implementation.png"  title="Tensorflow Implementation" class="img-fluid" %}
    </div>
</div>
<div class="caption">
    Tensorflow Implemetation of the Model from the Paper.
</div>
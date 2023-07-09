---
layout: page
title: BigEarthNet Classification using Transfer Learning.
description: Climate Change Machine Learning Competition - Won Gold Medal.
img: assets/img/climate_change_competition/bigearthnet.png
importance: 6
category: Deep Learning
github: https://github.com/VijayKalmath/XCeption-TransferLearning
---

## Climate Change Land use Image Prediction Machine Learning Competition

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

The competition data was modified to have 3 Labels instead of the 43 imbalanced labels.

Since the images are remote sensing data , for the competition I built 3-channel images or 5 channel images representations of the remote sensing data.  

After trying various architectures , I tried transfer learning with XCeptionNet which got a validation accuracy of 92% when trained with Adam optimizer , Sparse categorical crossentropy loss and a learning-rate scheduler callback.
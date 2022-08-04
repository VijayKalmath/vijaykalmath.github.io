---
layout: page
title: Spectral Representations for Convolutional Neural Networks
description: Implementation of Spectral Representations for Convolutional Neural Networks
img: assets/img/spectral_representations/rgb_pooling.png
importance: 2
category: Deep Learning
github: https://github.com/VijayKalmath/Spectral-Representations-for-Convolutional-Neural-Networks
---


The project is based on the the 2015 Paper by Oren Rippel et.al. [Arxiv Link](https://arxiv.org/pdf/1506.03767.pdf)

The proposals in the paper are aimed at improving the performance of Convolutional Neural Networks by exploiting the spectral domain of images (Fast Fourier Transforms are used to quickly convert images from spatial to spectral domain).

 
Essentially the proposals can be summarized into two main hypothesis :

1. `Spectral Pooling` where the pooling operation happens in the spectral domain of the input images. 
2. `Spectral Dropout` where frequencies are stochastically choosen to be dropped to mimic the regularization effect of standard dropout.
3. `Spectral Parameterization` where the image filters are initialized in the spectral domain.

We were able to successful implement all the Novel Ideas presented in the paper and replicate the results seen by the Authors.

## Spectral Pooling 

Spectral Pooling is a dimension reduction technique the authors introduced wherein the spectral representation of the image is truncated using a low pass filter and the image is later rebuilt with inverse transformations. 

This technique is supported by the fact that higher frequencies in the spectral representations of the images tend to encode noise and edges. Removing these frequencies leads to both dimension reduction while minimizing the loss of information. 

The implementation involves :

1. DFT of the image and shifting of the zero-frequency component. 
2. Implement a low pass filter and process the DFT image with the filter.
3. DFT images after low pass need to adhere to standards which involves treating corner cases when the shapes are odds.
4. Take Inverse DFT to get the spatial representation of the new image.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/spectral_representations/grayscale_pooling.png" title="Grayscale spectral Pooling" class="img-fluid" %}
    </div>
</div>

<div class="caption">
    Spectral Pooling for grayscale Images
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/spectral_representations/rgb_pooling.png" title="Rgb spectral Pooling" class="img-fluid" %}
    </div>
</div>
<div class="caption">
    Spectral Pooling for RGB Images
</div>

We can clearly see that the spectral pooling is much better at keeping the overall structure of the image intact through the extreme amounts of pooling.

We can see that in the most extreme case of dimension  reduction(by a factor of 4096), the max pooling output has lost all resemblances to the original image but in the spectral
pooling with just 8 frequencies , we can still see the silhouette of the man taking the photo.


## Spectral Representation 

In traditional CNN all the learnable parameters (weights of the filter as well as the associated bias terms) are defined in the real (spatial) domain. 

In this implementation however, the aim was to design a CNN with spectrally parameterized filters. 

We did this by initializing our parameter weights as complex valued coefficients of the DFT of the filter weights rather than the filter weights themselves. 

To do this we first created a custom “spectralConv2D” layer in Keras. 

Within this layer we built two separate kernels for representing the real and imaginary parts of our complex-valued kernel.

This was done since Keras doesn’t provide support for learning complex parameters directly. Next, we combine these two kernels into a single complex filter using tf.complex. 

We then take the inverse DFT of this filter so as to get its spatial representation which is ultimately used in the convolution operation with the input tensor (which was already in the spatial domain).


## Results 

We built different CNN architectures and their spectral equivalent wherein the Convolutional Layers are replaced with spectral CNNs , max-pooling layers are replaced with spectral pooling and dropout layers with spectral dropout layers. 

The trainings show that the spectral CNN Architectures were always faster in attaining the validation accuracy achieved by the  standard CNN Architecture. 

The Spectral CNN Architectures showed training speed-up by almost 2.1 to 5 times. 

Furthermore the Spectral CNNs were able to achieve higher validation accuracy with respect to the standard CNN architecture.
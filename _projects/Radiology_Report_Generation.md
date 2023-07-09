---
layout: page
title: Radiology Report Generation for Chest X-RAY Images
description: Analyze and Improve Resnet-Bert based MultiModal-PrototypeNetwork Model for Radiology Report Generation.
img: assets/img/rrg/rrg-model-output.jpg
importance: 1
category: Deep Learning
github: https://github.com/VijayKalmath/Radiology-Report-Genration-using-MultiModal-PrototypeNetwork
---

The project is based on the the 2022 Paper by Jun Wang et.al. [Arxiv Link](https://arxiv.org/pdf/2207.04818.pdf) 

Our work with XProNet mainly focused on building an inference pipeline and analyzing the generated texts from XProNets for radiology images for Accenture. 

Radiography is the most well established imaging method to diagnose diseases. The ability to automatically generate accurate medical reports from diagnostic images saves time and efforts of medical experts and aids the increase of healthcare accessibility.

A multi-modal deep learning model can embed extracted visual (from x-ray images) and textual (from text reports) features in common space and learn the cross-modal patterns to generate a textual report that describes the radiology image. This project analyzes the SOTA system for this task XProNet.

## Dataset

The IU-Xray dataset contains 7,470 chest x-ray images with 3,955 corresponding medical reports published by Indiana University.

The Dataset similar to other medical datasets has an inherent imbalance as :

1. Most reports associated to the images are normal, having no findings.
2. Even in abnormal reports, affected regions only exist in small parts of the text & image

Pseudo Label Generation Cross-modal prototypes require category information for each sample that corresponds to the 14 different chest disorders in literature and is often not provided in the datasets. To address this problem for prototype learning, the XProNet authors utilize CheXbert, an automatic radiology report labeler, to generate a pseudo label for each image-text pair.

<div class="row">
    <div class="col-md-6 mt-2 mt-md-0 ">
        {% include figure.html path="assets/img/rrg/example-dataset-entry.png" title="IU-Xray Dataset" class="img-fluid rounded" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/rrg/data-frequency.png"  title="IU_XRay Data Imbalance" class="img-fluid rounded" %}
    </div>
</div>
<div class="caption">
    1.  Example of frontal (left) and lateral (right) images for a given patient
    2.  Frequency of pseudo-labels in IU-X Ray Dataset
</div>

## XProNet Architecture and Performance

Before delving into the analysis of XProNet and our project centered around this model, it is essential to understand the architecture of XProNet. 

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0 ">
        {% include figure.html path="assets/img/rrg/architecture.png" title="XProNet Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0 ">
        {% include figure.html path="assets/img/rrg/rrg-model-output.jpg" title="XProNet Architecture Training" class="rounded z-depth-1" max-height="315px" %}
    </div>
</div>
<div class="caption">
    3. XProNet Architecture (architecture from paper by Jun Wang and co)
    4. Generated reports across training epochs.
</div>

The XProNet model architecture comprises three key components:

1. Image Feature Extractor :

    ResNet-101 is utilized as the image feature extractor in XProNet. It extracts informative features from Chest X-ray images at the last convolutional layer before the final average pooling operation.

2. Cross-modal Prototype Network:

    Cross-modal learning enables joint learning of image and text representations. XProNet incorporates a matrix that learns and stores cross-modal patterns, serving as intermediate representations. Cross-modal prototype querying measures similarity between single-modal representations and cross-modal prototype vectors under the same label. The top-ranked vectors are selected and interact with single-modal representations in a weighted-sum manner.

3. Report Generator Transformer
    The report generation is performed by a Transformer, which consists of encoder and decoder blocks with multiheaded attention. Visual features from querying and responding are fed into the Encoder. The fused output of the Encoder, combined with textual features, is input to the Decoder to predict the current output text.

## Project Work

As mentioned before, our work with XProNet mainly focused on building an inference pipeline and analyzing the generated texts from XProNets for radiology images.

<ins> Inference Pipeline</ins>

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0 ">
        {% include figure.html path="assets/img/rrg/inference-pipeline.png" title="XProNet Architecture" class="img-fluid rounded" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0 ">
        {% include figure.html path="assets/img/rrg/inference-pipeline-results.png" title="XProNet Architecture" class="img-fluid rounded" %}
        {% include figure.html path="assets/img/rrg/inference-pipeline-table.png" title="XProNet Architecture" class="img-fluid rounded" %}

    </div>
</div>
<div class="caption">
    4. XProNet Training vs Inference Pipeline
    5. Comparison of BLEU scores with new Inference pipeline and table
</div>

The XProNet system utilizes a cross-modal prototype matrix to store the relationships between image features and text features. This matrix is also dependent on a multi-label vector, referred to as the pseudo-label, which identifies the presence of 14 different chest diseases. The pseudo-label is generated by feeding the natural language report through the CheXBert model. Regrettably, this interdependence between the natural language report and the generation of pseudo-labels renders the XProNet system inapplicable for inference for health applications.

We build the inference pipeline with a component we call the Pseudo-label Generator. This component is capable of generating pseudo-labels from chest X-ray images through a multi-label classification task, effectively identifying the presence of each of the 14 different chest diseases. The Pseudo-label Generator serves as a robust replacement for the CheXBert module, as it operates independently of the natural language report.

To construct the Pseudo-label Generator multi-label classification model, we utilize a ResNet-101 to extract visual features from Chest X-ray images. The final layer of the ResNet-101 is replaced with a dense layer of size 14, equipped with a sigmoid activation function, to output the binary values associated with the 14 disorders. We use the IU-XRay images and the pseudo-labels generated by CheXBert as the target for training. We follow the same data splits proportions as XProNet to divide the IU-Xray dataset into train (70%), validation (10%) and test (20%) sets. The model is trained for 30 epochs using the Adam optimizer and a step-wise learning rate scheduler.

The comparison of performance with the new inference pipeline with the Pseudo-Label Generator indicates a very slight decrease in performance on the test set for IU-Xray.This indicates that the Inference Pipeline built is almost as good as the original architecture proposed while eliminating the dependency of Radiology Reports much before generating them from the Chest X-ray images

<ins> Mode Collapse</ins>

One of the notable observations during training of the XProNet model was that the model generated reports which were similar in appearance for multiple images in the test and validation data set.

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0 ">
        {% include figure.html path="assets/img/rrg/mode-collapse.png" title="XProNet Architecture" class="img-fluid rounded" %}
    </div>
</div>
<div class="caption">
    6. Frequency of unique reports generated for the test data set 
</div>

Figure 6 illustrates the frequency of unique generated reports by the XProNet for the test IU-XRay images. While the test dataset contains <ins> 396 unique ground truth natural language reports, the XProNet model only generates 18 unique reports </ins>, which is indicative of a Mode Collapse issue. This suggests that the model is unable to generate diverse reports for the test dataset.

A closer examination of the generated reports reveals that the <ins> 18 unique reports only contain 37 unique words </ins>, indicating that the unique reports are not significantly different from one another and only vary by a few words or word order. In comparison, the ground truth reports contain <ins> 634 unique words </ins>. This drastic decrease in the number of unique words suggests that the XProNet model is unable to capture all of the natural language information and is in- stead defaulting to a limited set of words and reports. This further supports the conclusion that the model is experiencing Mode Collapse.

We found through experimentation with differing inputs that for two different radiology images with different issues, if we use a single pseudo-label then the reports generated are exactly the same indicating that the transformers are over-dependent on the pseudo=labels. 

Further works to understand this dependence on pseudo-label generation needs to be analyzed along with prototype matrix analysis. 

Team Members : Vijay S Kalmath, Amrutha Varshini Sundar, Andrew Schaefer, Ayush Sinha, Prabha Kiranmai Vasireddy, Navjot Singh.
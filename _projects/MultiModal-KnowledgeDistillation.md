---
layout: page
title: Analyzing Student Models in Multi-Modal Knowledge Distillation
description: Research into MultiModal Knowledge Distillation with CLIP models
img: assets/img/multimodal_kd/mmkd.png
importance: 3
category: Deep Learning
github: https://github.com/VijayKalmath/MultiModal-KnowledgeDistillation
---

Title: Analyzing Student Models in Multi-Modal Knowledge Distillation

Project Summary:
Our project focused on the in-depth analysis of student models in the context of multi-modal knowledge distillation. We aimed to leverage the powerful CLIP (Contrastive Language-Image Pretraining) model for this purpose. 

As part of our experiments, we utilized a <u> ViT-based CLIP model </u> as the teacher model, consisting of 12 layers, while developing a student model based on the ViT architecture with half the number of layers. 

The training process involved working with the <u> Conceptual Captions </u> dataset, although we encountered technical issues that limited our ability to utilize the complete dataset.



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/multimodal_kd/methods.png" title="Multi-modal training approach"  class="img-fluid" %}
    </div>
</div>
<div class="caption">
    Triplet loss function - training and analysis of Distilled Clip Models.
</div>



To effectively train our student models, we adopted a comprehensive approach. We employed a triplet loss function, which facilitated the comparison of student embeddings, and incorporated a knowledge distillation (KD) loss function to measure the similarity between the teacher and student embeddings for both transformers. 

Throughout the experimentation, we explored different KD loss functions to identify the most effective approach.

The evaluation of our student models involved conducting zero-shot classification experiments to assess their top-5 accuracy on popular benchmark datasets such as CIFAR10, CIFAR100, and STL10. Additionally, we investigated the cosine similarity between gender terms and professions to gain insights into the propagation of biases in the knowledge distillation process.



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/multimodal_kd/results.png" title="Multi-modal training results"  class="img-fluid" %}
    </div>
</div>
<div class="caption">
    Multi-Modal Knowledge Distillation Results
</div>



The results of our analysis showcased consistent performance across the different loss functions employed, indicating that the top-5 accuracy on the evaluation datasets remained relatively similar. However, due to limitations in computing power and an insufficient dataset, the performance of our student models fell short compared to the fully pretrained CLIP model.


Of particular interest was the discovery that a combination of Mean Squared Error (MSE) and cosine loss for knowledge distillation yielded the best performance among the tested approaches. To ensure a fair comparison, we trained a CLIP model from scratch using our limited dataset, and the obtained results were on par with those achieved through knowledge distillation. This finding highlights the potential of our student models to reach the performance levels of the teacher model when provided with additional data and enhanced computing power.

Furthermore, our investigation into bias propagation revealed that the mappings between top professions and gender terms exhibited minimal changes in the student models. This observation suggests that the student models achieved a satisfactory level of debiasing, thereby reinforcing their potential for real-world applications.

Throughout the project, we gained valuable insights and learnings. Notably, we recognized the significant scale of data required for effective knowledge distillation, highlighting the need for extensive datasets to capture the complexity of the pre-trained teacher models. Additionally, we realized that the field of multimodal knowledge distillation still presents limitations and challenges, necessitating further research and advancements. Furthermore, the importance of computational resources and hyperparameter tuning became evident in achieving optimal performance.

It is crucial to acknowledge that models, regardless of their sophistication, are not immune to biases. Ethical considerations and involvement from legal teams play a pivotal role in ensuring the safe and responsible development of AI models. Ultimately, the success in the field of machine learning relies on collaboration, teamwork, and a holistic approach that extends beyond training large, high-performing models.
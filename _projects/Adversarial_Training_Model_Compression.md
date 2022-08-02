---
layout: page
title: Adversarial Training in Distillation of BERT
description: Language Model Compression and their Robustness 
img: assets/img/distilBert_modelcompression.png
importance: 1
category: work
github: https://github.com/VijayKalmath/AdversarialTraining_in_Distilation_Of_BERT
---

In the recent years, transformer-based language learning models like BERT have been one of the most popular architectures used in the research related to natural language processing. 

Productionizing these models under constrained resources to allow for the low latency the internet demands requires model compression. 

While model compression has been proven to perform with similar accuracy levels and with faster inference speeds , their robustness or lack thereof is usually overlooked. 

In this project we look at how we can use adversarial training either before or after model compression to preserve the robustness of the BERT Models.

 This paper evaluates the performance of various models built on the ideas of adversarial training and GAN BERT finetuned on SST-2 dataset. Further the experiments in this paper seek to find evidence on whether knowledege distillation preserves robustness in the student models.

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0 ">
        {% include figure.html path="assets/img/adversarial_training_model_compression/ganbert.png" title="GanBERT Architecture" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/adversarial_training_model_compression/textattack.png"  title="TextAttack Framework" class="img-fluid rounded z-depth-1" %}
    </div>

</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>

We explore two basic strategies for building robust models that are immune to adversarial attacks - Adversarial training and GAN-Bert training. 

Adversarial training mainly involves the technique of data augmentation during the finetuning step of the model while GAN Bert training involves self creation of perturbed examples that are included during the model training phase. 


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, *bled* for your project, and then... you reveal it's glory in the next row of images.


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>


The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}
```html
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
```
{% endraw %}

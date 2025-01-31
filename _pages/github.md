---
layout: page
permalink: /repositories/
title: Github
description: Quick Summary of My Github Profile 
nav: true
nav_order: 3
---

## Key GitHub Stats

{% if site.data.repositories.github_users %}
<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for user in site.data.repositories.github_users %}
    {% include repository/repo_user.html username=user %}
  {% endfor %}
</div>
{% endif %}

---

## Open Source Contributions 


| Repository | Description | Contribution
|-------|--------|---------|
| [TextAttack](https://github.com/QData/TextAttack)  | A Python framework for adversarial attacks, data augmentation, and model training in NLP | [~20 Pull Requests](https://github.com/QData/TextAttack/pulls?q=is%3Apr+author%3AVijayKalmath+)
| [Transformers](https://github.com/HuggingFace/Transformers)  | State-of-the-art Machine Learning for Pytorch, TensorFlow, and JAX. |  [Good First Issues](https://github.com/huggingface/transformers/pulls?q=+is%3Apr+author%3AVijayKalmath+)
| [Datasets](https://github.com/HuggingFace/Datasets)  | The largest hub of ready-to-use datasets for ML models | [Good First Issues](https://github.com/huggingface/datasets/pulls?q=+is%3Apr+author%3AVijayKalmath+) 
| [AIModelshare](https://www.modelshare.org/)  | Platform for Deep Learning repository, model hosting and competition | Maintainer

---

## GitHub Repositories

{% if site.data.repositories.github_repos %}
<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.html repository=repo %}
  {% endfor %}
</div>
{% endif %}

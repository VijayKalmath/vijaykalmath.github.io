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

## Key Github Contributions 

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  <div class="p-2 text-left">
      <ol>
      <li>TextAttack - A Python framework for adversarial attacks, data augmentation, and model training in NLP - <a href='https://github.com/QData/TextAttack/pulls?q=is%3Apr+author%3AVijayKalmath+'> Almost 20 PRs opened and merged. </a></li>
      <li>HuggingFace/Transformers - <a href='https://github.com/huggingface/transformers/pulls?q=+is%3Apr+author%3AVijayKalmath+'> Working on Several Good First Issues</a></li>
      <li>HuggingFace/Datasets - <a href='https://github.com/huggingface/datasets/pulls?q=+is%3Apr+author%3AVijayKalmath+'> Working on Several Good First Issues</a></li>
      <li>AIModelshare - Maintainer for the python library.</li>
    </ol>  

  </div>
</div>

---

## GitHub Repositories

{% if site.data.repositories.github_repos %}
<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.html repository=repo %}
  {% endfor %}
</div>
{% endif %}

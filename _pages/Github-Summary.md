---
layout: page
permalink: /repositories/
title: Github
description: <a href='https://github.com/VijayKalmath'>My Github Profile</a>  
nav: true
nav_order: 2
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

## Github Contributions 

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  <div class="repo p-2 text-center">
      <ol>
      <li>TextAttack <a href='https://github.com/QData/TextAttack/pulls?q=is%3Apr+author%3AVijayKalmath+'> ~20 PRs </a> </li>
        <dd>A Python framework for adversarial attacks, data augmentation, and model training in NLP</dd>
      <li>Tea</li>
      <li>Milk</li>
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

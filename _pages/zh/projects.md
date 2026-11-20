---
layout: page
lang: zh-CN
title: 项目
permalink: /zh/projects/
description: 科研系统与工程部署。选择项目查看详情。
---

<div class="projects">
  <div class="row row-cols-1 row-cols-md-3">
    {% assign chinese_projects = site.pages | where: 'lang', 'zh-CN' | where: 'project_card', true | sort: 'importance' %}
    {% for project in chinese_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
</div>

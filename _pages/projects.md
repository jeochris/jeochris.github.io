---
layout: page
title: Projects
permalink: /projects/
description:
nav: true
nav_order: 3
horizontal: false
---

<div class="projects">
{% assign sorted_projects = site.projects | sort: 'importance' | sort: 'year' | reverse %}
{% assign current_year = '' %}
{% for project in sorted_projects %}
  {% assign project_year = project.year | toString %}
  {% if project_year != current_year %}
    {% if current_year != '' %}</div>{% endif %}
    {% assign current_year = project_year %}
    <h2 class="bibliography" style="color: var(--global-divider-color); border-top: 1px solid var(--global-divider-color); padding-top: 1rem; margin-top: 2rem; text-align: right;">{{ project_year }}</h2>
    <div class="row row-cols-1 row-cols-md-3">
  {% endif %}
  {% include projects.liquid %}
{% endfor %}
{% if current_year != '' %}</div>{% endif %}
</div>

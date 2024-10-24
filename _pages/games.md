---
layout: page
title: games
icon:
permalink: /games/
description:  Soon, you’ll be able to view the projects I’ve been working on.
nav: true
nav_order: 2
display_categories: [games, toys]
horizontal: false
---

<!-- pages/projects.md -->
<div class="projects">

<!-- Initialize an empty array for all matching projects -->
{% assign all_categorized_projects = "" | split: "" %}

<!-- Filter projects by categories in display_categories -->
{% for category in page.display_categories %}
  {% assign categorized_projects = site.projects | where: "category", category %}

  <!-- Append categorized projects to the all_categorized_projects array -->
  {% for project in categorized_projects %}
    {% assign all_categorized_projects = all_categorized_projects | push: project %}
  {% endfor %}
{% endfor %}

<!-- Sort the collected projects by importance -->
{% assign sorted_projects = all_categorized_projects | sort: "importance" %}

<!-- Generate cards for each project -->
{% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
{% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
{% endif %}
</div>

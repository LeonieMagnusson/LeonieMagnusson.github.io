---
layout: page
title: illustration/art
icon:
permalink: /illustrations-and-art/
description: Illustraition is a life long passion of mine and part of many of my projects. Here you can see some of them.
nav: true
nav_order: 3
display_categories: [illustrations, art]
horizontal: false
background_image: /assets/img/webBackground.jpg
---

<style>
/* Add this style block to apply the background to the entire page */
body {
    background-image: url('assets/img/webBackground.jpg'); /* Path to your image */
    background-size: cover; /* Ensures the image covers the entire screen */
    background-repeat: no-repeat; /* Prevents the image from tiling */
    background-attachment: fixed; /* Keeps the image fixed during scrolling */
    background-position: center; /* Centers the image */
    color: white; /* Optional: Adjust text colour for better readability */
}
</style>

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

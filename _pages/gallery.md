---
layout: page
title: Gallery
permalink: /gallery/
description:
nav: true
nav_order: 3
display_categories: []
horizontal: false
---

<!-- pages/gallery.md -->
<div class="Gallery">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized gallery -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_gallery = site.gallery | where: "category", category %}
  {% assign sorted_gallery = categorized_gallery | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for project in sorted_gallery %}
      {% include gallery_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for project in sorted_gallery %}
      {% include gallery.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display gallery without categories -->

{% assign sorted_gallery = site.gallery | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-2">
    {% for project in sorted_gallery %}
      {% include gallery_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for project in sorted_gallery %}
      {% include gallery.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>

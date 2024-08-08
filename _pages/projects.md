---
layout: page
title: Projects
permalink: /projects/
description: A growing collection of projects @ SLPS Lab.
nav: true
nav_order: 4
display_categories: [work, fun]
horizontal: false
---

<style>
  .projects .project-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  overflow: hidden;
  margin: 10px;
  padding: 15px;
  background-color: #fff;
}

.projects .project-card img {
  width: 100%;
  height: 200px; /* Ensure images are of equal height */
  object-fit: cover; /* Crop or fit image within this space */
  border-bottom: 1px solid #ddd;
}

.projects .project-card h3 {
  font-size: 1.25rem;
  margin-top: 15px;
}

.projects .project-card p {
  margin-top: 10px;
  color: #666;
}

</style>

<div class="projects">
  {% if site.enable_project_categories and page.display_categories %}
    <!-- Display categorized projects -->
    {% for category in page.display_categories %}
    <a id="{{ category }}" href=".#{{ category }}">
      <h2 class="category">{{ category }}</h2>
    </a>
    {% assign categorized_projects = site.projects | where: "category", category %}
    {% assign sorted_projects = categorized_projects | sort: "importance" %}
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
    {% endfor %}

  {% else %}

  <!-- Display projects without categories -->

  {% assign sorted_projects = site.projects | sort: "importance" %}

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
  {% endif %}
</div>

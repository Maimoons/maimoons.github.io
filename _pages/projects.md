---
layout: page
title: projects
permalink: /projects/
description: A growing collection of your cool projects.
nav: true
display_categories: [work, fun]
horizontal: false
---

<div class="projects">
  {% if site.projects.sort_by == 'stars' %}
    {% assign sort_order = 'stargazers_count', 'last' %}
  {% else %}
    {% assign sort_order = 'pushed_at' %}
  {% endif %}

  {% if site.projects.exclude.archived && site.projects.exclude.forks %}
    {% assign filtered_repos = site.github.public_repositories | where:'archived', false | where:'fork', false | sort: sort_order | reverse %}
  {% elsif site.projects.exclude.archived %}
    {% assign filtered_repos = site.github.public_repositories | where:'archived', false | sort: sort_order | reverse %}
  {% elsif site.projects.exclude.forks %}
    {% assign filtered_repos = site.github.public_repositories | where:'fork', false | sort: sort_order | reverse %}
  {% else %}
    {% assign filtered_repos = site.github.public_repositories | sort: sort_order | reverse %}
  {% endif %}

  {% for repository in filtered_repos | limit: site.projects.limit %}
    {% unless site.projects.exclude.projects contains repository.name %}
     <div class="container">
          <div class="row row-cols-2">
          {% include repo-card.html %}
          </div>
      </div>
    {% endunless %}
  {% endfor %}
</div>

<div class="projects">
  {% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
    {% for category in page.display_categories %}
      <h2 class="category">{{category}}</h2>
      {% assign categorized_projects = site.projects | where: "category", category %}
      {% assign sorted_projects = categorized_projects | sort: "importance" %}
      <!-- Generate cards for each project -->
      {% if page.horizontal %}
        <div class="container">
          <div class="row row-cols-2">
          {% for project in sorted_projects %}
            {% include projects_horizontal.html %}
          {% endfor %}
          </div>
        </div>
      {% else %}
        <div class="grid">
          {% for project in sorted_projects %}
            {% include projects.html %}
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
        <div class="row row-cols-2">
        {% for project in sorted_projects %}
          {% include projects_hrz.html %}
        {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="grid">
        {% for project in sorted_projects %}
          {% include projects.html %}
        {% endfor %}
      </div>
    {% endif %}

  {% endif %}

</div>

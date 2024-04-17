---
layout: team
title: Team
permalink: /team/
description:
nav: true
nav_order: 2
display_categories: [Researcher, Intern, Collaborator, Past Member, Research Scientist, Research Intern, Past Researcher, Past Intern]
horizontal: true
---

<!-- pages/team.md -->
<div class="projects">
{%- if site.enable_team_categories and page.display_categories %}
  <!-- Display categorized teams -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_team = site.team | where: "category", category -%}
  {%- assign sorted_team = categorized_team | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <!-- *** PS: Set the number of cols here *** -->
    <div class="row row-cols-4"> 
    {%- for member in sorted_team -%}
      {% include member_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for member in sorted_team -%}
      {% include member.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display projects without categories -->
  {%- assign sorted_team = site.team | sort: "importance" -%}
  <!-- Generate cards for each project -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for member in sorted_team -%}
      {% include member_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for member in sorted_team -%}
      {% include member.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>

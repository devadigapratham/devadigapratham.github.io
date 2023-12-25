---
layout: page
permalink: /talks/
title: talks
description: Blog and Resources related to talks given.
nav: true
nav_order: 5
---
<!-- pages/talks.md -->

<div class="talks">
  {%- if site.enable_talk_categories and page.display_categories %}
    <!-- Display categorized talks -->
    {%- for category in page.display_categories %}
      <h2 class="category">{{ category }}</h2>
      {%- assign categorized_talks = site.talks | where: "category", category -%}
      {%- if categorized_talks != null and categorized_talks.size > 0 -%}
        {%- assign sorted_talks = categorized_talks | sort: "importance" %}
        <!-- Generate cards for each talk -->
        {% if page.horizontal -%}
          <div class="container">
            <div class="row row-cols-2">
              {%- for talk in sorted_talks -%}
                {% include talks_horizontal.html %}
              {%- endfor %}
            </div>
          </div>
        {%- else -%}
          <div class="grid">
            {%- for talk in sorted_talks -%}
              {% include talks.html %}
            {%- endfor %}
          </div>
        {%- endif -%}
      {%- else -%}
        <!-- Handle case where there are no talks in this category -->
        No talks available for this category.
      {%- endif -%}
    {%- endfor %}
  {%- else -%}
    <!-- Display talks without categories -->
    {%- if site.talks != null and site.talks.size > 0 -%}
      {%- assign sorted_talks = site.talks | sort: "importance" %}
      <!-- Generate cards for each talk -->
      {% if page.horizontal -%}
        <div class="container">
          <div class="row row-cols-2">
            {%- for talk in sorted_talks -%}
              {% include talks_horizontal.html %}
            {%- endfor %}
          </div>
        </div>
      {%- else -%}
        <div class="grid">
          {%- for talk in sorted_talks -%}
            {% include talks.html %}
          {%- endfor %}
        </div>
      {%- endif -%}
    {%- else -%}
      <!-- Handle case where there are no talks at all -->
      Will be up soon! 
    {%- endif -%}
  {%- endif -%}
</div>

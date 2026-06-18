---
layout: page
meta_title: Categories
meta_description: Browse all categories
hide_from_sitemap: true
robots: noindex,follow
title: Categories
permalink: /categories/
---

<h2>Projects</h2>
<ul>
{% set projectTags = [] %}

{% for post in collections.projects %}
  {% for tag in post.data.tags %}
    {% if tag != 'projects' and tag != 'all' %}
      {% if projectTags.indexOf(tag) == -1 %}
        {% set projectTags = projectTags.concat([tag]) %}
      {% endif %}
    {% endif %}
  {% endfor %}
{% endfor %}

{% for tag in projectTags %}
  <li><a href="/categories/{{ tag | slug }}">{{ tag | capitalize }}</a></li>
{% endfor %}

</ul>

<a href="/projects/" style="margin-top: 10px; margin-bottom: 10px">All Projects</a>

<h2>Blog Posts</h2>
<ul>
{% set blogTags = [] %}

{% for post in collections.blog %}
  {% for tag in post.data.tags %}
    {% if tag != 'blog' and tag != 'all' %}
      {% if blogTags.indexOf(tag) == -1 %}
        {% set blogTags = blogTags.concat([tag]) %}
      {% endif %}
    {% endif %}
  {% endfor %}
{% endfor %}

{% for tag in blogTags %}
  <li><a href="/categories/{{ tag | slug }}">{{ tag | capitalize }}</a></li>
{% endfor %}

</ul>

<a href="/blog/" style="margin-top: 10px; margin-bottom: 10px">All Blog Posts</a>
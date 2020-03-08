---
layout: default
title: Blog
---

{% for blog in site.blog %}

  <h2><a href="{{ blog.url }}">{{ blog.title }}</a></h2>

<p class="post-excerpt">{{ blog.description | truncate: 160 }}</p>

{% endfor %}

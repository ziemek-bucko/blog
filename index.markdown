---
layout: default
title: Data
---

{% for content in site.content %}

  <h2><a href="{{ content.url }}">{{ content.title }}</a></h2>

<p class="post-excerpt">{{ content.description | truncate: 160 }}</p>

{% endfor %}

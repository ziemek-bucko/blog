---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: Home
---

{% for content in site.content %}

  <h2><a href="{{ content.url }}">{{ content.title }}</a></h2>

<p class="post-excerpt">{{ content.description | truncate: 160 }}</p>

{% endfor %}

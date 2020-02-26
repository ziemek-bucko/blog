---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

{% for content in site.content %}

<a href="{{ content.url | prepend: site.baseurl }}">
  <h2>{{ content.title }}</h2>
</a>

<p class="post-excerpt">{{ content.description | truncate: 160 }}</p>

{% endfor %}

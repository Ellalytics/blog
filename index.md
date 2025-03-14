---
layout: home
author_profile: true
---

This is my personal blog where I share my thoughts, experiences, and knowledge about programming and technology.

## Recent Posts

{% for post in paginator.posts %}
  {% include archive-single.html %}
{% endfor %}

{% include paginator.html %} 
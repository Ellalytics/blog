---
layout: home
author_profile: true
---

This is my personal blog where I share my thoughts, experiences, and knowledge about programming and technology.

{% for post in paginator.posts %}
  {% include archive-single.html %}
{% endfor %}

{% include paginator.html %} 


<div class="entries-list">
  {% for post in site.posts limit:6 %}
    <article class="entry">
      <h4><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h4>
      <p>{{ post.excerpt | strip_html | truncate: 100 }}</p>
    </article>
  {% endfor %}
</div>



---
layout: single
title: "Categories"
permalink: /categories/
author_profile: true
---

## ai
{% for post in site.categories.ai %}
- [{{ post.title }}]({{ post.url | relative_url }}) <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}

## electrical
{% for post in site.categories.electrical %}
- [{{ post.title }}]({{ post.url | relative_url }}) <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}

## ev
{% for post in site.categories.ev %}
- [{{ post.title }}]({{ post.url | relative_url }}) <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}

## e-commerce
{% for post in site.categories.e-commerce %}
- [{{ post.title }}]({{ post.url | relative_url }}) <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}

## game
{% for post in site.categories.game %}
- [{{ post.title }}]({{ post.url | relative_url }}) <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}
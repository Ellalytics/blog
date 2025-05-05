---
layout: single
title: "Categories"
permalink: /categories/
author_profile: true
---

## AI
{% for post in site.categories.AI %}
- [{{ post.title }}]({{ post.url | relative_url }}) <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}

## Electrical
{% for post in site.categories.Electrical %}
- [{{ post.title }}]({{ post.url | relative_url }}) <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}

## EV
{% for post in site.categories.EV %}
- [{{ post.title }}]({{ post.url | relative_url }}) <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}

## E-commerce
{% for post in site.categories.E-commerce %}
- [{{ post.title }}]({{ post.url | relative_url }}) <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}

## Game
{% for post in site.categories.Game %}
- [{{ post.title }}]({{ post.url | relative_url }}) <span class="post-meta">{{ post.date | date: "%Y-%m-%d" }}</span>
{% endfor %}
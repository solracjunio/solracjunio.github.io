---
layout: single
title: "Solrac Junio Blog"
toc: true
toc_sticky: true
permalink: /
author_profile: false
---

{% assign postsByYearMonth = site.posts | group_by_exp:"post", "post.date | date: '%Y %B'" %}
{% for yearMonth in postsByYearMonth %}
  {% assign dateParts = yearMonth.name | split: " " %}
  <h2 id="{{ dateParts[0] }}-{{ dateParts[1] | date: '%m' }}" class="archive__subtitle">{{ dateParts[1] }} {{ dateParts[0] }}</h2>
  {% for post in yearMonth.items %}
    {% include archive-single.html %}
  {% endfor %}
{% endfor %}
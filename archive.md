---
layout: page
title: Archive
permalink: /archive/
---

<ul>
{% for post in site.posts %}

  <li>
    <a href="{{ post.url }}">{{ post.title }}</a><p>{{ post.date | date: "%b %d, %Y"  }}</p>
  </li>
{% endfor %}
</ul>

---
layout: default
title: Blog
---

<ul class="post-list">
  {% for post in site.posts %}
    <li>
      <a class="post-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <div class="post-meta">{{ post.date | date: "%B %d, %Y" }}</div>
    </li>
  {% endfor %}
</ul>
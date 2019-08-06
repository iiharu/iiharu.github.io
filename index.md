---
title: Hello World
---
# Hello World

## Recent Post
<ul>
  {% for post in site.posts limit:2 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

---
title: プログラミング, ときどき...
---
# プログラミング, ときどき...

## Recent Post
<ul>
  {% for post in site.posts limit:2 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

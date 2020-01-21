---
permalink: /blog/
title: "Blog"
author_profile: true
---
I am fixing the errors in my last post.
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>


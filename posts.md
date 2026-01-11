---
title: "Posts"
---

<section>
  <ul>
    {% assign posts = site.posts | sort: "slug" %}
    {% for post in posts %}
      <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }} </a><br><small>{{ post.excerpt }}</small></li>
    {% endfor %}
  </ul>
</section>

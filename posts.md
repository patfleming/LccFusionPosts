---
title: "Posts"
---

<section>
  <ul>
    {% for post in site.posts %}
      <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }} </a><br><small>{{ post.excerpt }}</small></li>
    {% endfor %}
  </ul>
</section>

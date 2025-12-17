---
title: "Posts"
layout: posts
classes: wide
permalink: /posts/
author_profile: false
classes: wide
date: 2025-11-20
---

<section>
  <ul>
    {% assign posts = site.posts | sort: "slug" %}
    {% for post in posts %}
      <li>
        <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a><br>
        <small>{{ post.excerpt }}</small>
      </li>
    {% endfor %}
  </ul>
</section>

---
title: "Podcasts"
layout: posts
classes: wide
permalink: /podcasts/
author_profile: false
date: 2025-11-20
classes: wide
---

<section>
  <ul>
    {% assign all_posts = site.posts %}
    {% assign podcast_posts = all_posts | where_exp: "post", "post.categories contains 'Podcast'" %}
    {% for post in podcast_posts %}
      <li>
        <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a><br>
        <small>{{ post.excerpt }}</small>
      </li>
    {% endfor %}
  </ul>
</section>

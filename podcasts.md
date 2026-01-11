---
title: "Podcasts"
---

<section>
  <ul>
    {% assign all_posts = site.posts | sort: "slug" %}
    {% assign podcast_posts = all_posts | where_exp: "post", "post.categories contains 'Podcast'" %}
    {% for post in podcast_posts %}
      <li>
        <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a><br>
        <small>{{ post.excerpt }}</small>
      </li>
    {% endfor %}
  </ul>
</section>

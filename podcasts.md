---
title: "Podcasts"
---

<section>
  <p>Podcast posts collect the video, slides, notes, and related article context for LCC Fusion topics.</p>
  <ul>
    {% assign podcast_posts = site.posts | where_exp: "post", "post.categories contains 'Podcasts'" %}
    {% for post in podcast_posts %}
      <li>
        <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a><br>
        <small>{{ post.excerpt }}</small>
      </li>
    {% endfor %}
  </ul>
</section>

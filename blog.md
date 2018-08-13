---
layout: page
title: Blog
permalink: /about/
---

<section id="two" class="wrapper alt style2">
  <section class="spotlight">
    <ul>
      {% for post in site.posts %}
      <div class="content">
        <h2><a href="{{ post.url | relative_url }}" class="link">{{ post.title }}</a></h2>
        <p>{{ post.description }}</p>
      </div>
      {% endfor %}
    <ul>
</section>

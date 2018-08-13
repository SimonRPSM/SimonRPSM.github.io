---
layout: page
title: Blog
permalink: /blog/
description: ""
---


  <section class="major">
    <ul>
      {% for post in site.posts %}
        <h2><a href="{{ post.url | relative_url }}" class="link">{{ post.title }}</a></h2>
        <p>{{ post.description }}</p>
      {% endfor %}
    <ul>

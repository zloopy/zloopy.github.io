---
layout : page
title : "Physics Bytes !"
icon: fas fa-podcast
category : blog
order: 8
---
Welcome to Physics Bytes ! the english language podcast of the students of Notre-Dame de Sion here in Paris!

<div class="post-list">
  {% for post in site.categories.blog %}
    <article class="post-list-item">
      {% if post.featured_image %}
        <a class="post-list-item-image" href="{{ post.url | relative_url }}" style="background-image: url('{{ post.featured_image }}')"></a>
      {% endif %}
      <a class="post-list-item-title" href="{{ post.url | relative_url }}">{{ post.title }}</a>
      <div class="post-list-item-excerpt">{{ post.excerpt | strip_html | truncate: 400, '&hellip;' }}</div>
      <time class="post-list-item-date" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
    </article>
  {% endfor %}
</div>


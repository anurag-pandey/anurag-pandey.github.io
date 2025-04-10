---
layout: default
title: Blog
permalink: /blog/
---

<div class="blog-container">
  <h1 class="page-heading">Blog</h1>
  
  {% for post in site.posts %}
  <div class="post-card">
    {% if post.content.size > 50 %}
    <a href="{{ post.url | relative_url }}" class="post-card-link">
    {% endif %}
      <div class="post-card-content">
        <h2 class="post-card-title">{{ post.title }}</h2>
        {% if post.content.size > 50 %}
          <div class="post-card-excerpt">
            {{ post.content | strip_html | truncatewords: 15 }}
          </div>
        {% endif %}
        <span class="post-card-date">{{ post.date | date: "%b %-d, %Y" }}</span>
      </div>
    {% if post.content.size > 50 %}
    </a>
    {% endif %}
  </div>
  {% endfor %}
</div>
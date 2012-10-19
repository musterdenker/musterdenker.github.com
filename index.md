---
layout: page
title: Musterdenker
tagline:  blog posts and projects
---
{% include JB/setup %}

The Musterdenker is a german group of developers and designers.

***

## {{ site.posts.first.title }} 
({{ site.posts.first.description }})

{{ site.posts.first.content }}

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

---
layout: default
title: Blog
---
<h2>Blogposts</h2>

<ul>
  {% for post in site.posts %}
      <i>{{post.date | date_to_string }} <a href="{{ post.url }}">{{ post.title }}</a></i><br>
  {% endfor %}
</ul>

<h2>Categories</h2>
<ul>
{% assign categories = site.categories | sort: "title" %}
{% for post in categories %}
    <li> <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
{% endfor %}
</ul>
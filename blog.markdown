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
{% for category in site.categories %}
<i><a href="{{ site.url }}/category/{{ category | first | slugify }}/index.html">#{{ category | first }}</a></i>
{% endfor %}
</ul>
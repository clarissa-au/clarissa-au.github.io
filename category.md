---
layout: default
---
<h2>List of categories in this blog</h2>
<ul>
{% assign categories = site.categories | sort: "title" %}
{% for post in categories %}
    <li> <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
{% endfor %}
</ul>


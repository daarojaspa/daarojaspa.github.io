---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---
---
layout: default
title: Home
---

# All Posts by Category

{% assign posts_by_category = site.posts | group_by: "category" %}

{% for category in posts_by_category %}
## {{ category.name | capitalize }}

<ul>
  {% for post in category.items %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <small>({{ post.date | date: "%Y-%m-%d" }})</small>
    </li>
  {% endfor %}
</ul>
{% endfor %}

---
layout: page
title: Hello My Engineering Blog!
tagline: Supporting tagline
---
{% include JB/setup %}

## Doing
* Crossfit Wod Diary : [http://crossfitwod.herokuapp.com](http://crossfitwod.herokuapp.com)
* Engineering Blog : [http://leejoon0.github.io/](http://leejoon0.github.io/)

## Posts

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

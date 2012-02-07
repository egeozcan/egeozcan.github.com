---
layout: page
title: The Guy Who Keeps Coding While True
---
{% include JB/setup %}

## About

I think I need to stop coding and do some literature here... I am a web developer. I'm good at all things JavaScript, C#, Python, Ruby and of course HTML/CSS.
    
## Stuff I've Talked About

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>



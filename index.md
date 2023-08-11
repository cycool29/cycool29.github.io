---
title: Home
layout: default
author: cycool29
---

{% for post in site.posts limit:1 %}
<h2><a href="{{ post.url }}" style="text-decoration: none; color: #00ff00">{{  post.title  }}</a></h2>

{{ post.description }}

<p class="btn" style="color: #0f0; font-size: 90%; border-color: #00ff00"><a style="text-decoration: none; color: #0f0;"
                        href="{{ post.url }}">Continue Reading </a></p>

{% endfor %}
<br/>

### **Latest posts**

{% for post in site.posts limit:5 %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}



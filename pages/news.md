---
title: posts
permalink: /posts/
---

# Posts

<p>저희가 개발을 하며 공부한 내용들이에요(❁´◡`❁)</p>

<br>

{% for post in site.posts limit:10 %}
   <div class="post-preview">
   <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>
   <span class="post-date">{{ post.date | date: "%B %d, %Y" }}</span><br>
   {% if post.badges %}{% for badge in post.badges %}<span class="badge badge-{{ badge.type }}">{{ badge.tag }}</span>{% endfor %}{% endif %}
   {{ post.content | split:'<!--more-->' | first }}
   {% if post.content contains '<!--more-->' %}
      <a href="{{ site.baseurl }}{{ post.url }}">read more</a>
   {% endif %}
   </div>
   <hr>
{% endfor %}

Want to see more? See the <a href="{{ site.baseurl }}/archive/">News Archive</a>.

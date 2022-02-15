---
layout: page
title: Documentation
permalink: /docs/
---

# Documentation

🎈이곳에선 특정 페이지를 바로 갈 수 있는 링크를 제공하고 있어요.

<div class="section-index">
    <hr class="panel-line">
    {% for post in site.docs  %}        
		<div class="entry">
			<h5><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h5>
			<p>{{ post.description }}</p>
		</div>
	{% endfor %}
</div>

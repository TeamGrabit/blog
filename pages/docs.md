---
layout: page
title: Documentation
permalink: /docs/
---

# Documentation

πμ΄κ³³μμ  νΉμ  νμ΄μ§λ₯Ό λ°λ‘ κ° μ μλ λ§ν¬λ₯Ό μ κ³΅νκ³  μμ΄μ.

<div class="section-index">
    <hr class="panel-line">
    {% for post in site.docs  %}        
		<div class="entry">
			<h5><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h5>
			<p>{{ post.description }}</p>
		</div>
	{% endfor %}
</div>

---
layout: page
title: Archives
keywords: 存档
comments: true
permalink: /archives/
---

<ul>
  {% for post in site.posts %}
	{% unless post.next %}
	  <h2 id="y{{ post.date | date: '%Y' }}">{{ post.date | date: '%Y' }}</h2>
	{% else %}
	  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
	  {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
	  {% if year != nyear %}
		<h2 id="y{{ post.date | date: '%Y' }}">{{ post.date | date: '%Y' }}</h2>
	  {% endif %}
	{% endunless %}

	<li>
		<time style="display:inline-block; width: 135px;">
		{{ post.date | date:"%F" }} {{ post.date | date: "%a" }}.
		</time>
		
		<a class="title" href="{{ post.url }}">{{ post.title }}</a>
		
		<span style="padding-left: 15px"> </span>
		
		{% for cat in post.categories %}
		<span class="meta-info">
		  <span class="octicon octicon-file-directory"></span>
		  <a href="/categories/#{{ cat }}" title="{{ cat }}">{{ cat }}</a>
		</span>
		{% endfor %}
	</li>

  {% endfor %}
</ul>
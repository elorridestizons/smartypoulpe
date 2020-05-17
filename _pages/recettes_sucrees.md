---
layout: page
title: Recettes sucrées
#image: Author/Elorri.jpg
permalink: /recettes_sucrees/
---


<div class="container">
	<div class="row">
		{% assign first_post = true %}
		{%- for post in site.posts offset: 1 -%}
			{% for tag in post.tags %}
				{% if tag == "Recettes sucrées"%}
					{% if first_post == true %}
					{% assign first_post = false %}
					<div class="col col-12">
						<article class="article-first">
							<div class="article-image-first"
								style="background-image: url({{"/img/" | prepend: site.baseurl | append : post.image}})">
								<div class="article-content-first">
									<div class="article-tag">
										{% if post.tags.size >= 1 %}
											{% for tag in post.tags %}
												<a href="{{ site.baseurl }}/tags#{{tag}}" class="tag">{{ tag }}</a>
											{% endfor %}
										{% else %} {% endif %}
									</div>
									<h2 class="article-title"><a href="{{ post.url | prepend: site.baseurl }}">{{post.title}}</a>
									</h2>
									<p class="article-excerpt">
										{% if post.description %}{{ post.description | strip_html | truncate: 163 }}{% else %}{{ post.content | strip_html | truncate: 163 }}{% endif %}
									</p>
									<a href="{{ post.url | prepend: site.baseurl }}" class="button read-more">Read More</a>
								</div>
							</div>
						</article> <!-- /.article-first -->
					</div>
					{% else %}
					<div class="col col-12 col-t-8">
						<div class="row">
							<article class="article col col-12 col-t-6">
								<div class="article-box">
									<div class="article-head">
										<a href="{{ post.url | prepend: site.baseurl }}" class="article-image"
											style="background-image: url({{"/img/" | prepend: site.baseurl | append : post.image}})">
											<div class="image-overlay">
												<span class="image-overlay-text">{{post.title | slice: 0}}</span>
											</div>
										</a>
									</div>
									<div class="article-content">
										<div class="article-info">
											<div class="article-date">
												<span class="date"><time
														datetime="{{ post.date | date_to_xmlschema }}">{% assign date_format = site.minima.date_format | default: "%b %-d, %Y" %}{{ post.date | date: date_format }}</time></span>
											</div>
											<div class="article-tag">
												{% if post.tags.size >= 1 %}
													{% for tag in post.tags %}
														<a href="{{ site.baseurl }}/tags#{{tag}}" class="tag">{{ tag }}</a>
													{% endfor %}
												{% else %} {% endif %}
											</div>
										</div>
										<h2 class="article-title">
											<a href="{{ post.url | prepend: site.baseurl }}">{{post.title}}</a>
										</h2>
										<p class="article-excerpt">
											{% if post.description %}{{ post.description | strip_html | truncate: 135 }}{% else %}{{ post.content | strip_html | truncate: 135 }}{% endif %}
										</p>
									</div>
								</div>
							</article> <!-- /.article -->
						</div>
						{% include pagination.html %}
					</div> 
					{% endif %}
				{% else %} {% endif %}
			{% endfor %}
		{% endfor %}
		<div class="col col-12 col-t-4">
				{% include sidebar.html %}
		</div>
	</div>
</div>
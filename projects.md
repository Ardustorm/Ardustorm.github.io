---
layout: page
title: Completed Projects
---

Here is a collection of some of my completed projects.
As projects become complete, I will add them here.



{% for tag in site.tags %}
  {% assign t = tag | first %}
  {% assign posts = tag | last %}

<ul>
{% for post in posts %}
  {% if post.tags contains "done" %}

  
     <article class="post-preview">
    <a href="{{ post.url | prepend: site.baseurl }}">
	  <h2 class="post-title">{{ post.title }}</h2>

	  {% if post.subtitle %}
	  <h3 class="post-subtitle">
	    {{ post.subtitle }}
	  </h3>
	  {% endif %}
    </a>

    <p class="post-meta">
      Posted on {{ post.date | date: "%B %-d, %Y" }}
    </p>

    <div class="post-entry">
      {{ post.excerpt | strip_html | xml_escape | truncatewords: site.excerpt_length }}
      {% assign excerpt_word_count = post.excerpt | number_of_words %}
      {% if post.content != post.excerpt or excerpt_word_count > site.excerpt_length %}
        <a href="{{ post.url | prepend: site.baseurl }}" class="post-read-more">[Read&nbsp;More]</a>
      {% endif %}
    </div>

    {% if post.tags.size > 0 %}
    <div class="blog-tags">
      Tags:
      {% if site.link-tags %}
      {% for tag in post.tags %}
      <a href="{{ site.baseurl }}/tag/{{ tag }}">{{ tag }}</a>
      {% endfor %}
      {% else %}
        {{ post.tags | join: ", " }}
      {% endif %}
    </div>
    {% endif %}

   </article>
    
  </li>
  {% endif %}
{% endfor %}
</ul>
{% endfor %}

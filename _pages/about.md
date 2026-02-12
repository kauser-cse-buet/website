---
permalink: /about/
title: "About"
---

Computer science researcher with a strong background in machine learning, data analysis, and large-scale software systems. Author of peer-reviewed publications in emotion modeling, protein structure prediction, and autonomous systems. Experienced software engineer with industry exposure to building scalable, secure, and data-intensive systems, with research interests spanning human-centric modeling, networked systems, and data-driven security.  
Outside of work, I enjoy playing soccer and reading books, especially science fiction.
{: .notice--info}

## Recent Posts

{% for post in site.posts limit:5 %}
<div class="notice--primary">
  {% if post.image %}
    <img src="{{ post.image | relative_url }}" alt="{{ post.title }}">
  {% endif %}
  <h4><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h4>
  <p>{{ post.excerpt }}</p>
</div>
{% endfor %}

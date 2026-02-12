Computer science researcher and passionate software engineer with a strong background in machine learning, data analysis, and large-scale software systems. My research interests lie at the intersection of human-centric AI, networked systems, and data-driven security. I have authored peer-reviewed publications in emotion modeling, protein structure prediction, and autonomous systems, and I bring industry experience building scalable, secure, and data-intensive software platforms.  
Outside of research and engineering, I enjoy traveling, hiking, playing soccer, and reading books, especially science fiction.
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

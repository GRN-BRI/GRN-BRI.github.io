---
layout: default
title: News
permalink: /news/
---

<style>
.image-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: 16px;
  margin-top: 1rem;
}

.image-grid img {
  width: 100%;
  border-radius: 8px;
  object-fit: cover;
  box-shadow: 0 2px 6px rgba(0,0,0,0.15);
  transition: transform 0.3s;
}

.image-grid img:hover {
  transform: scale(1.03);
}

.conference-entry {
  border-bottom: 1px solid #ddd;
  padding: 1rem 0;
  margin-bottom: 1rem;
}
.conference-entry img {
  max-width: 300px;
  border-radius: 6px;
  margin-top: 0.5rem;
}
</style>

# 🗂 Past Conferences

---

{% assign posts = site.posts | where_exp: "post", "post.categories contains 'past-conferences'" | sort: "date" | reverse %}

{% for post in posts %}
<div class="conference-entry">
  <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
  <p><strong>{{ post.date | date: "%B %d, %Y" }}</strong></p>

  {% if post.excerpt %}
    <p>{{ post.excerpt }}</p>
  {% endif %}

  {% if post.image %}
    <img src="{{ post.image | relative_url }}" alt="{{ post.title }}">
  {% endif %}

  <p><a href="{{ post.url | relative_url }}">📄 View Full Details →</a></p>
</div>
{% endfor %}

---

# 🖼 Photo Highlights from Past Conferences

<div class="image-grid">
  {% for post in posts %}
    {% if post.image %}
      <img src="{{ post.image | relative_url }}" alt="Image from {{ post.title }}">
    {% endif %}
  {% endfor %}
</div>

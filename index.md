---
layout: default
title: Thrilling Times
---

# 🌍 Stories that make us who we are

🌌 **Stories, hikes, road trips, and unforgettable moments**  
I have the feeling that many of us have stories worth telling and worth writting to perdure. This blog is an effort for normal people to share their stories and make them eternal and public

---

> “If I find in myself a desire which no experience in this world can satisfy,  
> the most probable explanation is that I was made for another world.”  
> — *C.S. Lewis*

---

## 🧭 Latest Adventures

{% for post in site.posts %}
{% assign image = post.path | split:'/' | last | replace:'.md','.jpg' %}

<div class="card fade-in">

<a href="{{ site.baseurl }}{{ post.url }}">
  <div class="card-image">
    <img
      src="{{ site.baseurl }}/assets/img/{{ image }}"
      alt="{{ post.title }}"
      loading="lazy"
      onerror="this.parentElement.style.display='none'"
    />
  </div>
</a>

  <h3>
    <a href="{{ site.baseurl }}{{ post.url }}">
      {{ post.title }}
    </a>
  </h3>

  <p class="muted">
    {{ post.date | date: "%B %d, %Y" }}
  </p>

  <p>{{ post.excerpt }}</p>

  <p>
    <strong>
      <a href="{{ site.baseurl }}{{ post.url }}">Read more →</a>
    </strong>
  </p>

</div>

{% endfor %}


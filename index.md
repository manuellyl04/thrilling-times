---
layout: default
title: Thrilling Times
---

<style>
body {
  background-color: #0f172a;
  color: #e5e7eb;
}

a { color: #93c5fd; }

.card {
  background: #020617;
  border-radius: 14px;
  padding: 1.5rem;
  margin-bottom: 2.5rem;
  box-shadow: 0 10px 25px rgba(0,0,0,.4);
}

.card img {
  width: 100%;
  border-radius: 12px;
  margin-bottom: 1rem;
}

.hero img {
  width: 100%;
  max-width: 900px;
  border-radius: 16px;
}

blockquote {
  border-left: 4px solid #38bdf8;
  padding-left: 1rem;
  color: #cbd5f5;
}
</style>


# 🌍 Stories that make us who we are

🌌 **Stories, hikes, road trips, and unforgettable moments**  
Built around curiosity, solitude, and wonder.

---

## ✒️ Words That Inspire the Journey

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


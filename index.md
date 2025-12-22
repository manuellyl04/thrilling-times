---
layout: default
title: Thrilling Times
---

<!-- HERO IMAGE -->
<div style="text-align:center; margin-bottom:2rem;">
  <img
    src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?auto=format&fit=crop&w=1200&q=80"
    alt="Adventure landscape"
    style="width:100%; max-width:900px; border-radius:12px;"
  />
</div>

# 🌍 Thrilling Times

🌄 **Stories, hikes, road trips, and unforgettable moments**  
✨ Built around curiosity, wanderlust, and good company.

---

## ✒️ Words That Inspire the Journey

> “"If I find in myself a desire which no experience in this world can satisfy, the most probable explanation is that I was made for another world.”  
> — *C.S. Lewis*
---

## 🧭 Latest Adventures

{% for post in site.posts %}
<div style="margin-bottom:3rem;">

<h3>🗺️ <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h3>

<p>📅 <em>{{ post.date | date: "%B %d, %Y" }}</em></p>

<p>{{ post.excerpt }}</p>

<p>
  👉 <strong>
    <a href="{{ site.baseurl }}{{ post.url }}">Read more →</a>
  </strong>
</p>

</div>

<hr />
{% endfor %}


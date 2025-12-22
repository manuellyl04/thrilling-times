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

> “Not all those who wander are lost.”  
> — *J.R.R. Tolkien*

> “Once a year, go someplace you’ve never been before.”  
> — *Dalai Lama*

> “The world is a book, and those who do not travel read only one page.”  
> — *Saint Augustine*

---

## 🧭 Latest Adventures

{% for post in site.posts %}
<div style="margin-bottom:3rem;">

### 🗺️ [{{ post.title }}]({{ site.baseurl }}{{ post.url }})

📅 *{{ post.date | date: "%B %d, %Y" }}*

{{ post.excerpt }}

👉 **[Read more →]({{ site.baseurl }}{{ post.url }})**

</div>

<hr />
{% endfor %}

---
layout: default
title: Thrilling Times
---

<!-- HERO IMAGE -->
<div style="text-align:center;">
  <img
    src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?auto=format&fit=crop&w=1400&q=80"
    alt="Adventure landscape"
    style="max-width:100%; border-radius:12px;"
  />
</div>

# 🌍 Thrilling Times

🌄 **Stories, hikes, road trips, and unforgettable moments**  
✨ Built around curiosity, wonderlust, and good company.

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

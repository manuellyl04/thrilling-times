---
layout: default
title: Thrilling Times
---

# 🌍 Thrilling Times

Stories, hikes, and adventures with friends.

---

{% for post in site.posts %}
## 🗺️ [{{ post.title }}]({{ site.baseurl }}{{ post.url }})

📅 *{{ post.date | date: "%B %d, %Y" }}*

{{ post.excerpt }}

[Read more →]({{ site.baseurl }}{{ post.url }})

---
{% endfor %}

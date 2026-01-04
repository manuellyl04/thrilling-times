---
layout: default
title: Thrilling Times
---

# 🌍 Just doing it for the plot

🌌 **Share your most interesting sidequests and make them immortal**  
---

> “If I find in myself a desire which no experience in this world can satisfy,  
> the most probable explanation is that I was made for another world.”  
> — *C.S. Lewis*

---

{% comment %}
========================================
 Adventurer metadata
 Add new travellers here once
========================================
{% endcomment %}

{% assign adventurers = 
  {
    "manuellorenzo": "Manuel Lorenzo"
  }
%}

<section class="adventurers">
  <h2>Adventurers</h2>

  <div class="adventurers-grid">

    {% assign all_travellers = site.posts | map: "travellers" | compact | uniq | sort %}

    {% for traveller in all_travellers %}
      {% assign count = 0 %}
      {% for post in site.posts %}
        {% if post.travellers contains traveller %}
          {% assign count = count | plus: 1 %}
        {% endif %}
      {% endfor %}

      <a
        href="?traveller={{ traveller }}"
        class="adventurer"
        data-traveller="{{ traveller }}"
      >
        <img
          src="{{ site.baseurl }}/assets/img/adventurers/{{ traveller }}.jpg"
          alt="{{ traveller }}"
          loading="lazy"
        >
        <span class="name">
          {{ adventurers[traveller] | default: traveller }}
        </span>
        <span class="count">
          {{ count }} adventure{% if count != 1 %}s{% endif %}
        </span>
      </a>
    {% endfor %}

  </div>

  <button id="clear-filter" hidden>
    ✖ Clear filter
  </button>
</section>

---

## 🧭 Latest Adventures

<div id="posts">

{% for post in site.posts %}
{% assign image = post.path | split:'/' | last | replace:'.md','.jpg' %}

<div
  class="card fade-in"
  data-travellers="{{ post.travellers | join: ',' }}"
>

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

  {% if post.travellers %}
  <div class="post-travellers">
    {% for traveller in post.travellers %}
      <a
        href="?traveller={{ traveller }}"
        class="inline-adventurer"
        title="{{ adventurers[traveller] | default: traveller }}"
      >
        <img
          src="{{ site.baseurl }}/assets/img/adventurers/{{ traveller }}.jpg"
          alt="{{ traveller }}"
        >
      </a>
    {% endfor %}
  </div>
  {% endif %}

  <p>
    <strong>
      <a href="{{ site.baseurl }}{{ post.url }}">Read more →</a>
    </strong>
  </p>

</div>

{% endfor %}

</div>

<script>
(function () {
  const params = new URLSearchParams(window.location.search);
  const selectedTraveller = params.get("traveller");

  if (!selectedTraveller) return;

  document.getElementById("clear-filter").hidden = false;

  document.querySelectorAll(".adventurer").forEach(el => {
    if (el.dataset.traveller === selectedTraveller) {
      el.classList.add("active");
    }
  });

  document.querySelectorAll(".card").forEach(card => {
    const travellers = card.dataset.travellers || "";
    if (!travellers.split(",").includes(selectedTraveller)) {
      card.style.display = "none";
    }
  });

  document.getElementById("clear-filter").addEventListener("click", () => {
    window.location.href = window.location.pathname;
  });
})();
</script>

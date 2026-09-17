---
layout: default
title: Thrilling Times
---

# 🌍 Just doing it for the plot

🌌 **Share your most interesting sidequests and make them immortal here**  
---

> “If I find in myself a desire which no experience in this world can satisfy,  
> the most probable explanation is that I was made for another world.”  
> — *C.S. Lewis*

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

  <p>{{ post.excerpt | strip_html | truncatewords: 32 }}</p>

  {% if post.travellers %}
  <div class="post-travellers">
    {% for traveller in post.travellers %}
      {% assign adventurer = site.data.adventurers[traveller] %}
      <a
        href="?traveller={{ traveller }}"
        class="inline-adventurer"
        title="{{ adventurer.name | default: traveller }}"
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

<a
  class="card share-card fade-in"
  href="https://github.com/manuellyl04/thrilling-times#share-your-own-story"
>
  <span class="share-plus">+</span>
  <h3>Share your story</h3>
  <p class="muted">
    Got a sidequest worth telling? Add it to the collection and make it immortal.
  </p>
</a>

</div>

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

      {% assign adventurer = site.data.adventurers[traveller] %}
      <a
        href="?traveller={{ traveller }}"
        class="adventurer"
        data-traveller="{{ traveller }}"
        aria-label="{{ adventurer.name | default: traveller }}"
      >
        <img
          src="{{ site.baseurl }}/assets/img/adventurers/{{ traveller }}.jpg"
          alt="{{ adventurer.name | default: traveller }}"
          loading="lazy"
        >

        <span class="tooltip">
          {{ adventurer.name | default: traveller }}  
          · {{ count }} adventure{% if count != 1 %}s{% endif %}
        </span>
      </a>
    {% endfor %}

    <a
      class="adventurer add-adventurer"
      href="https://github.com/manuellyl04/thrilling-times#share-your-own-story"
      aria-label="Join the adventurers"
    >
      <span class="add-circle">+</span>
      <span class="tooltip">Join the adventurers</span>
    </a>
  </div>

  <div id="filter-info" hidden>
    <span>
      Filtering by <strong id="active-traveller"></strong>
    </span>
    <button id="clear-filter">
      Show all adventures
    </button>
  </div>
</section>

<script>
(function () {
  const params = new URLSearchParams(window.location.search);
  const selectedTraveller = params.get("traveller");

  if (!selectedTraveller) return;

  document.getElementById("filter-info").hidden = false;

  let displayName = selectedTraveller.replace(/(^\w)/, m => m.toUpperCase());
  document.querySelectorAll(".adventurer").forEach(el => {
    if (el.dataset.traveller === selectedTraveller) {
      el.classList.add("active");
      displayName = el.getAttribute("aria-label") || displayName;
    }
  });
  document.getElementById("active-traveller").textContent = displayName;

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

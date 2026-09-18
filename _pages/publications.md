---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

<div class="hk-pub-filters" role="group" aria-label="Filter publications">
  <button class="active" data-filter="all">All</button>
  <button data-filter="conference">Conference</button>
  <button data-filter="journal">Journal</button>
  <button data-filter="preprint">Preprint</button>
</div>

{% assign preprints = site.data.publications | where: "type", "preprint" %}
{% if preprints.size > 0 %}
<section class="hk-pub-section" data-section="preprints">
  <h2 class="hk-pub-year">Preprints</h2>
  {% for pub in preprints %}
    {% include publication-item.html pub=pub %}
  {% endfor %}
</section>
{% endif %}

{% assign years = "2026,2025,2024,2023,2022,2021,2020" | split: "," %}
{% for year in years %}
  {% assign year_num = year | plus: 0 %}
  {% assign year_pubs = site.data.publications | where: "year", year_num %}
  {% assign regular_pubs = year_pubs | where_exp: "p", "p.type != 'preprint'" %}
  {% if regular_pubs.size > 0 %}
  <section class="hk-pub-section" data-section="{{ year }}">
    <h2 class="hk-pub-year">{{ year }}</h2>
    {% for pub in regular_pubs %}
      {% include publication-item.html pub=pub %}
    {% endfor %}
  </section>
  {% endif %}
{% endfor %}

<a class="hk-next-section" href="/cv/">
  <span class="hk-next-label">Next</span>
  <span class="hk-next-main"><strong>CV</strong><span aria-hidden="true">→</span></span>
  <span class="hk-next-desc">Education, honors, and competitions</span>
</a>

---
layout: default
title: Case Studies
permalink: /case-studies/
---

# Case Studies

A collection of practical experiences from working in software development, exploring user research, product discovery, agile delivery, developer experience and data-informed decisions.

Each case study describes the challenges, my contributions and what I learned along the way.

<div class="cards">
{% assign cases = site.case_studies | sort: "order" %}
{% for case in cases %}
  <article class="card">
    <h2>
        <a href="{{ case.url | relative_url }}">{{ case.title | escape }}</a>
    </h2>
    <p>{{ case.summary | escape }}</p>
  </article>
{% endfor %}
</div>

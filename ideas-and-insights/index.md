---
layout: default
title: Ideas & Insights
permalink: /ideas-and-insights/
---

# Ideas & Insights

A space to share reflections, lessons learned and things I'm curious about — from product thinking and developer experience to sailing and whatever I explore next.

<div class="cards">
{% assign articles = site.insights | sort: "date" | reverse %}
{% for article in articles %}
  <article class="card">
    <h2>
        <a href="{{ article.url | relative_url }}">{{ article.title | escape }}</a>
    </h2>
    <p>{{ article.summary | escape }}</p>
  </article>
{% endfor %}
</div>

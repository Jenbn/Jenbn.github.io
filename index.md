---
layout: default
title: Home
---

<p class="eyebrow">Technical Business Analyst · Product Thinking · Curious Mind</p>

# From Complexity to Clarity

<p class="lead">I'm a Technical Business Analyst with a background in Quality Analysis, a curious mind and a passion for understanding problems, connecting people and making complicated things simpler.</p>

Here, I share professional experiences, lessons learned, practical experiments and whatever sparks my curiosity along the way.

[Get to know me →]({{ '/about/' | relative_url }}){: .button-link }

## Featured Case Studies

A selection of my work in internal platform teams, exploring user research, agile delivery, developer experience and data-informed decisions.

<div class="cards">
{% assign featured_cases = site.case_studies | sort: "order" %}
{% for case in featured_cases limit:3 %}
  <article class="card">
    <h3>
      <a href="{{ case.url | relative_url }}">{{ case.title | escape }}</a>
    </h3>
    <p>{{ case.summary | escape }}</p>
  </article>
{% endfor %}
</div>

[Explore all case studies →]({{ '/case-studies/' | relative_url }})

## Ideas & Insights

A space for reflections, things I'm learning and ideas I'd like to share — from product thinking and developer experience to sailing and whatever comes next.

<div class="cards">
{% assign recent_articles = site.insights | sort: "date" | reverse %}
{% for article in recent_articles limit:3 %}
  <article class="card">
    <h3>
      <a href="{{ article.url | relative_url }}">{{ article.title | escape }}</a>
    </h3>
    <p>{{ article.summary | escape }}</p>
  </article>
{% endfor %}
</div>

[Explore all articles →]({{ '/ideas-and-insights/' | relative_url }})

## A Little More About Me

My journey into technology started in tourism and customer-facing roles before moving into Quality Analysis and Business Analysis.

Outside work, I enjoy cooking, travelling, discovering different cultures and learning new things. My latest adventure is working towards my RYA Day Skipper certification and developing my sailing skills.

This website is a space for both my professional work and the things I'm curious about beyond it.

[More about me →]({{ '/about/' | relative_url }})

---

**A note on AI and confidentiality:** I used AI as a supporting tool to develop parts of this portfolio, including synthetic datasets, analytical exercises, writing and website development. The professional experiences and contributions described are my own. Examples are anonymised or reconstructed where necessary to protect confidentiality, and retrospective exercises are identified accordingly.

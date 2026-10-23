---
title: "Reports & Data Products"
permalink: /reports/
layout: single
---

<style>
  .report-grid{
    display:grid;
    grid-template-columns:repeat(auto-fill,minmax(280px,1fr));
    gap:22px;
    margin-top: 1rem;
  }
  .report-card{
    display:block;
    border:1px solid #e5e7eb;
    border-radius:16px;
    overflow:hidden;
    background:#fff;
    text-decoration:none !important;
    transition:transform .12s ease, box-shadow .12s ease, border-color .12s ease;
  }
  .report-card:hover{
    transform:translateY(-2px);
    border-color:#d1d5db;
    box-shadow:0 14px 32px rgba(0,0,0,.10);
  }
  .report-thumb{
    aspect-ratio: 16 / 10;
    background:#f3f4f6;
    overflow:hidden;
  }
  .report-thumb img{
    width:100%;
    height:100%;
    object-fit:cover;
    display:block;
  }
  .report-meta{
    padding:16px 16px 18px 16px;
  }
  .report-title{
    margin:0 0 6px 0;
    font-size: 1.05rem;
    line-height: 1.25;
    color:#111827;
    font-weight: 800;
  }
  .report-sub{
    margin:0 0 10px 0;
    color:#6b7280;
    font-size:.95rem;
    font-weight: 600;
  }
  .report-desc{
    margin:0;
    color:#374151;
    font-size:.95rem;
    line-height:1.35;
  }
  .report-type{
    display:inline-block;
    margin:0 0 8px 0;
    padding:2px 8px;
    border-radius:999px;
    background:#eef2ff;
    color:#3730a3;
    font-size:.75rem;
    font-weight:700;
    letter-spacing:.02em;
    text-transform:uppercase;
  }
  .report-card a.report-main{
    display:block;
    text-decoration:none !important;
  }
  .report-links{
    display:flex;
    flex-wrap:wrap;
    gap:8px 14px;
    margin-top:12px;
    font-size:.9rem;
    font-weight:600;
  }
  .report-links a{ text-decoration:none; }
  .report-links a:hover{ text-decoration:underline; }
  .section-heading{ margin-top:2rem; }
</style>

## Data Products {#data-products .section-heading}

<div class="report-grid">
{% for d in site.data.data_products %}
  <div class="report-card">
    <a class="report-main" href="{{ d.link }}" target="_blank" rel="noopener">
      <div class="report-thumb">
        <img src="{{ d.image | relative_url }}" alt="{{ d.title }} preview image">
      </div>
    </a>
    <div class="report-meta">
      {% if d.type %}<span class="report-type">{{ d.type }}</span>{% endif %}
      <a class="report-main" href="{{ d.link }}" target="_blank" rel="noopener">
        <div class="report-title">{{ d.title }}</div>
      </a>
      <div class="report-sub">{{ d.org }}{% if d.date %} • {{ d.date }}{% endif %}</div>
      {% if d.contribution %}
        <p class="report-desc">{{ d.contribution }}</p>
      {% endif %}
      {% if d.links %}
        <div class="report-links">
        {% for l in d.links %}
          <a href="{{ l.url }}" target="_blank" rel="noopener">{{ l.label }} ↗</a>
        {% endfor %}
        </div>
      {% endif %}
    </div>
  </div>
{% endfor %}
</div>



## Reports {#reports .section-heading}

<div class="report-grid">
{% for r in site.data.reports %}
  {% assign href = r.link %}
  {% if r.link contains 'http' %}
    {% assign href = r.link %}
  {% else %}
    {% assign href = r.link | relative_url %}
  {% endif %}

  <a class="report-card" href="{{ href }}" target="_blank" rel="noopener">
    <div class="report-thumb">
      <img src="{{ r.image | relative_url }}" alt="{{ r.title }} cover image">
    </div>
    <div class="report-meta">
      {% if r.type %}<span class="report-type">{{ r.type }}</span>{% endif %}
      <div class="report-title">{{ r.title }}</div>
      <div class="report-sub">{{ r.org }}{% if r.date %} • {{ r.date }}{% endif %}</div>
      {% if r.contribution %}
        <p class="report-desc">{{ r.contribution }}</p>
      {% endif %}
    </div>
  </a>
{% endfor %}
</div>

---
layout: splash
title: "Solrac Junio Blog"
permalink: /
author_profile: false
---

{% assign latest = site.posts | first %}

<section class="eg-hero">
  {% if latest %}
  <a class="eg-pill eg-spotlight" href="{{ latest.url | relative_url }}">
    <span class="eg-pill__tag">Novo</span>
    <span class="eg-pill__text">{{ latest.title }}</span>
    <span aria-hidden="true">→</span>
  </a>
  {% endif %}

  <h1 class="eg-hero__title">{{ site.description | strip }}</h1>

  <div class="eg-hero__actions">
    {% for link in site.footer.links %}
      <a class="eg-btn eg-btn--ghost eg-spotlight" href="{{ link.url }}" target="_blank" rel="noopener">
        <i class="{{ link.icon }}" aria-hidden="true"></i> {{ link.label }}
      </a>
    {% endfor %}
  </div>
</section>

<section class="eg-posts" id="posts">
  <div class="eg-section-head">
    <h2 class="eg-section-title">Artigos recentes</h2>
    <div class="eg-view-toggle" role="group" aria-label="Modo de exibição">
      <button type="button" class="eg-view-btn" data-view="grid" aria-pressed="true" title="Ver em grade">
        <svg viewBox="0 0 16 16" width="16" height="16" aria-hidden="true"><rect x="1" y="1" width="6" height="6" rx="1.5"/><rect x="9" y="1" width="6" height="6" rx="1.5"/><rect x="1" y="9" width="6" height="6" rx="1.5"/><rect x="9" y="9" width="6" height="6" rx="1.5"/></svg>
        <span>Grade</span>
      </button>
      <button type="button" class="eg-view-btn" data-view="list" aria-pressed="false" title="Ver em lista">
        <svg viewBox="0 0 16 16" width="16" height="16" aria-hidden="true"><rect x="1" y="1.5" width="4" height="4" rx="1"/><rect x="7" y="2.5" width="8" height="2" rx="1"/><rect x="1" y="6" width="4" height="4" rx="1"/><rect x="7" y="7" width="8" height="2" rx="1"/><rect x="1" y="10.5" width="4" height="4" rx="1"/><rect x="7" y="11.5" width="8" height="2" rx="1"/></svg>
        <span>Lista</span>
      </button>
    </div>
  </div>

  <div class="eg-grid">
  {% for post in site.posts %}
    {% comment %} Capa: header.teaser > header.image > primeira imagem do post {% endcomment %}
    {% assign cover = post.header.teaser | default: post.header.image %}
    {% unless cover %}
      {% if post.content contains '<img' %}
        {% assign cover = post.content | split: '<img' | slice: 1 | first | split: 'src="' | slice: 1 | first | split: '"' | first %}
      {% endif %}
    {% endunless %}
    {% assign words = post.content | strip_html | number_of_words %}
    {% assign minutes = words | divided_by: 200 | at_least: 1 %}

    <div class="eg-card-wrap eg-reveal">
    {% comment %} Glow ambiente: cópia desfocada da capa que "vaza" cor no fundo {% endcomment %}
    <div class="eg-ambient{% unless cover %} eg-ambient--gradient{% endunless %}" aria-hidden="true">
      {% if cover %}<img src="{{ cover | relative_url }}" alt="" loading="lazy">{% endif %}
    </div>
    <a class="eg-card eg-spotlight" href="{{ post.url | relative_url }}">
      <div class="eg-card__media">
        {% if cover %}
          <img src="{{ cover | relative_url }}" alt="" loading="lazy">
        {% else %}
          <span class="eg-card__placeholder" aria-hidden="true">{{ post.title | slice: 0 }}</span>
        {% endif %}
      </div>
      <div class="eg-card__body">
        <p class="eg-card__meta">
          <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%d/%m/%Y" }}</time>
          · {{ minutes }} min de leitura
        </p>
        <h3 class="eg-card__title">{{ post.title }}</h3>
        <p class="eg-card__excerpt">{{ post.excerpt | strip_html | truncatewords: 24 }}</p>
      </div>
    </a>
    </div>
  {% endfor %}
  </div>
</section>

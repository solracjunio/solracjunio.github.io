---
layout: splash
title: "Solrac Junio Blog"
permalink: /
author_profile: false
---

{% assign latest = site.posts | first %}

<section class="eg-hero">
  {% if latest %}
  <a class="eg-pill" href="{{ latest.url | relative_url }}">
    <span class="eg-pill__tag">Novo</span>
    <span class="eg-pill__text">{{ latest.title }}</span>
    <span aria-hidden="true">→</span>
  </a>
  {% endif %}

  <h1 class="eg-hero__title">{{ site.title }}</h1>
  <p class="eg-hero__subtitle">{{ site.description }}</p>

  <div class="eg-hero__actions">
    <a class="eg-btn eg-btn--primary" href="#posts">Ler os posts</a>
    {% for link in site.footer.links %}
      <a class="eg-btn eg-btn--ghost" href="{{ link.url }}" target="_blank" rel="noopener">
        <i class="{{ link.icon }}" aria-hidden="true"></i> {{ link.label }}
      </a>
    {% endfor %}
  </div>
</section>

<section class="eg-posts" id="posts">
  <h2 class="eg-section-title">Últimos posts</h2>

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

    <a class="eg-card eg-reveal" href="{{ post.url | relative_url }}">
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
  {% endfor %}
  </div>
</section>

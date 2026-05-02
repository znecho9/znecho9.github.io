---
layout: single
title: "Home"
permalink: /
classes:
  - wide
  - kf-home-page
author_profile: false
---

{% assign recent_publications = site.publications | sort: "date" | reverse %}
{% assign recent_posts = site.posts | sort: "date" | reverse %}

<div class="kf-home">
  <section class="kf-hero">
    <div class="kf-hero__copy">
      <h1 class="serif-font">Echo Valley</h1>
      <p class="kf-lead">Hi, I am Zinan, an independent engineer and researcher working across civil engineering, wind engineering, and long-form technical writing.</p>
      <p>This site collects my research notes, publications in progress, project writeups, and essays on building durable personal knowledge systems.</p>
      <div class="kf-actions">
        <a class="kf-button" href="{{ '/cv/' | relative_url }}">About me</a>
        <a class="kf-link" href="{{ '/publications/' | relative_url }}">View publications</a>
      </div>
    </div>
    <div class="kf-hero__media">
      <img src="{{ '/assets/images/bio-photo.jpg' | relative_url }}" alt="Abstract profile artwork for Zinan Lin">
    </div>
  </section>

  <div class="kf-main-grid">
    <section class="kf-publications">
      <h2 class="kf-section-title serif-font"><a href="{{ '/publications/' | relative_url }}">Recent Publications:</a></h2>
      <div class="kf-publication-grid">
        {% for item in recent_publications limit: 4 %}
        <article class="kf-card">
          <a class="kf-card__media" href="{{ item.url | relative_url }}">
            <img src="{{ item.image | default: site.teaser | relative_url }}" alt="">
          </a>
          <div class="kf-card__body">
            <h3 class="kf-card__title"><a href="{{ item.url | relative_url }}">{{ item.title }}</a></h3>
            <p class="kf-card__meta"><em>{{ item.authors | default: site.author.name }}</em>{% if item.venue %}, {{ item.venue }}{% endif %}{% if item.date %}, {{ item.date | date: "%Y" }}{% endif %}</p>
            {% if item.tags %}
            <ul class="kf-tags">
              {% for tag in item.tags limit: 3 %}
              <li>{{ tag }}</li>
              {% endfor %}
            </ul>
            {% endif %}
            <p class="kf-card__excerpt">{{ item.excerpt | markdownify | strip_html | truncate: 145 }}</p>
          </div>
        </article>
        {% endfor %}
      </div>
    </section>

    <aside class="kf-news">
      <h3 class="serif-font">Recent News</h3>
      <div class="kf-news__item">
        <time datetime="2026-05">May 2026</time>
        <p>Rebuilt this site into a cleaner academic homepage with a publication-first layout.</p>
      </div>
      <div class="kf-news__item">
        <time datetime="2026-05">May 2026</time>
        <p>Drafting notes on independent engineering as a repeatable research practice.</p>
      </div>
      <div class="kf-news__item">
        <time datetime="2026-04">April 2026</time>
        <p>Started organizing technical notes around AI-assisted research workflows.</p>
      </div>
    </aside>
  </div>

  <section class="kf-blog-section">
    <h2 class="kf-section-title serif-font"><a href="{{ '/year-archive/' | relative_url }}">Recent Blog Posts:</a></h2>
    <div class="kf-blog-grid">
      {% for post in recent_posts limit: 3 %}
      <article class="kf-card">
        <a class="kf-card__media" href="{{ post.url | relative_url }}">
          <img src="{{ post.header.image | default: site.teaser | relative_url }}" alt="">
        </a>
        <div class="kf-card__body">
          <h3 class="kf-card__title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
          <p class="kf-card__meta">{{ post.date | date: "%B %-d, %Y" }}</p>
          <p class="kf-card__excerpt">{{ post.excerpt | markdownify | strip_html | truncate: 145 }}</p>
        </div>
      </article>
      {% endfor %}
    </div>
  </section>
</div>

---
layout: single
title: "About"
author_profile: true
permalink: /
---

I am **Zinan Lin**, an independent engineer and researcher interested in software
systems, applied intelligence, and the craft of building durable personal
knowledge. My current work is organized around a simple question: how can
engineering practice become a better instrument for understanding the world?

My background combines production engineering, self-directed research, and
long-form writing. I use this site as an academic-style notebook for work in
progress: publications and essays in preparation, talks I may give, teaching
materials, project notes, and reflections on work and life.

## Research Interests

- Human-centered software systems and developer tools
- Applied AI, knowledge workflows, and research infrastructure
- Reliable interfaces for long-running personal and collaborative work
- Writing as a method for technical thinking and self-education

## News

- **2026.05**: Rebuilt this website into an Academic Pages style research homepage.
- **2026.05**: Preparing draft notes on independent engineering and personal research systems.
- **2025.08**: Began writing publicly about work transitions, agency, and long-term capability.

## Selected Publications

{% assign selected_publications = site.publications | sort: "date" | reverse | slice: 0, 3 %}
{% if selected_publications.size > 0 %}
{% for item in selected_publications %}
- **[{{ item.title }}]({{ item.url | relative_url }})**<br>
  {{ item.venue }}{% if item.date %}, {{ item.date | date: "%Y" }}{% endif %}. {{ item.excerpt | markdownify | strip_html }}
{% endfor %}
{% else %}
Publication drafts will be listed here as they become ready.
{% endif %}

## Recent Writing

{% assign recent_posts = site.posts | slice: 0, 3 %}
{% for post in recent_posts %}
- **[{{ post.title }}]({{ post.url | relative_url }})**<br>
  {{ post.date | date: "%B %-d, %Y" }}. {{ post.excerpt | markdownify | strip_html | truncate: 160 }}
{% endfor %}

## Current Work

I am currently building a small research agenda around independent engineering:
how to keep technical work creative, how to make research notes compound, and how
to design tools that make careful thinking easier to sustain.

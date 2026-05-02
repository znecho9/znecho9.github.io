---
title: Home
layout: default
---

{% assign recent_publications = site.publications | sort: "date" | reverse %}
{% assign recent_posts = site.posts | sort: "date" | reverse %}

{% if page.url == "/" %}
<div class="rounded mb-5 hero">
  <div class="row align-items-center justify-content-between">
    <div class="col-md-6">
      <h1 class="font-weight-bold mb-4 serif-font">Zinan Lin</h1>
      <p>Hi, I am Zinan, an independent engineer and researcher working across civil engineering, wind engineering, and long-form technical writing.</p>
      <p>I use this site to collect research notes, publications in progress, project writeups, and essays on building durable personal knowledge systems.</p>
      <p><br></p>
      <a href="{{ '/about/' | relative_url }}" class="btn btn-dark text-white px-5 btn-lg">About me</a>
    </div>
    <div class="col-md-6 text-right pl-0 pl-lg-4">
      <img class="intro" width="380" height="380" src="{{ '/assets/images/bio-photo.jpg' | relative_url }}" alt="Zinan Lin profile artwork">
    </div>
  </div>
</div>
{% endif %}

<h3 class="font-weight-bold mb-4 serif-font"><a href="{{ '/publications/' | relative_url }}">Recent Publications:</a></h3>
<br>
<section class="row">
  <div class="col-sm-8">
    <div class="row">
      {% for item in recent_publications limit: 4 %}
      <div class="col-md-6 mb-5">
        {% include postbox.html entry=item %}
      </div>
      {% endfor %}
    </div>
  </div>
  <div class="col-sm-4">
    {% include sidebar.html %}
  </div>
</section>

<h3 class="font-weight-bold mb-4 serif-font">Recent Blog Posts:</h3>
<br>
<section class="row">
  {% for post in recent_posts limit: 3 %}
  <div class="col-md-4 mb-5">
    {% include postbox.html entry=post %}
  </div>
  {% endfor %}
</section>

---
title: Legal Documents
permalink: /
---

# Legal Documents

Privacy policies and terms of service for our apps.

<ul class="home-list">
{% for app in site.data.apps %}
  <li class="app-card">
    <h2 id="{{ app.slug }}">{{ app.name }}</h2>
    {% if app.tagline %}<p class="tagline">{{ app.tagline }}</p>{% endif %}
    <div class="doc-links">
      {% for doc in app.docs %}
        <a href="{{ doc.url | relative_url }}">{{ doc.title }}</a>
      {% endfor %}
    </div>
  </li>
{% endfor %}
</ul>

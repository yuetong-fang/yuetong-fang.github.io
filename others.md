---
layout: default
title: Others
---
<div class="page-title">
    <h1>Others</h1>
</div>

<section class="section">
    <h3 class="section-title">Links</h3>
{% assign links = site.data.links %}
{% if links.size > 0 %}
<div class="link-list">
    {% for link in links %}
    <div class="link-item">
        <a href="{{ link.url }}" target="_blank" class="link-name">{{ link.name }}</a>
        {% if link.description %}
        <span class="link-description">— {{ link.description }}</span>
        {% endif %}
    </div>
    {% endfor %}
</div>
{% else %}
<div class="no-links">No links available at the moment.</div>
{% endif %}
</section>
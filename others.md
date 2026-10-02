---
layout: default
title: Others
last_modified: 2026-10-02

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


<section class="section">
    <h3 class="section-title">Outreach</h3>
   <p >I participated in the <a href="https://www.bretagne-pays-de-la-loire.cnrs.fr/fr/cnrsinfo/la-science-taille-xx-elles-une-nouvelle-edition-de-lexposition-celebre-les-femmes" target="_blank" class="text-link">La Science taille XX elles</a> program of Pays de la Loire in 2026.
  <p>
  I was volunteer for
  <a href="https://www.mathenjeans.fr/" target="_blank" class="text-link">MATh.en.JEANS</a>
  for
  <a href="https://mathenjeans.fr/content/Lycee-Joachim-Du-Bellay-Angers-2025-2026" target="_blank" class="text-link">lycée Joachim Du Bellay</a>
  in 2025.
</p>
</section>
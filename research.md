---
layout: default
title: Research
---

<section class="section">
<h2 class="section-title">Preprints                                                                   </h2>

{% assign preprints = site.data.publications | where: "type", "preprint" | sort: "year" | reverse %}
{% if preprints.size > 0 %}
{% for paper in preprints %}
<div class="publication-item">
    <div class="publication-content">
        <span class="publication-number">{{ forloop.length | minus: forloop.index0 }}.</span>
        <span class="publication-title">{{ paper.title }}</span>
        {% if paper.authors != "Y. Fang" and paper.authors != "Fang, Y." %}
        <span class="publication-authors"> with {{ paper.authors | remove: "Fang, Y., " | remove: ", Fang, Y." | remove: "Y. Fang, " | remove: ", Y. Fang" }}</span>
        {% endif %}
        <span class="publication-meta">, {{ paper.archive }}, {{ paper.year }}</span>
        {% if paper.arxiv %}
        <span class="publication-links"> [<a href="https://arxiv.org/abs/{{ paper.arxiv }}" target="_blank">arXiv</a>]</span>
        {% endif %}
        {% if paper.abstract %}
        <span class="publication-links"> [<button class="abstract-toggle" data-target="abstract-preprint-{{ forloop.index }}">Abstract</button>]</span>
        {% endif %}
    </div>
    {% if paper.abstract %}
    <div class="publication-abstract" id="abstract-preprint-{{ forloop.index }}">{{ paper.abstract }}</div>
    {% endif %}
</div>
{% endfor %}
{% else %}
<div class="no-publications">No preprints available at the moment.</div>
{% endif %}
</section>

<section class="section">
<h2 class="section-title">Publications</h2>

{% assign journal_papers = site.data.publications | where: "type", "journal" | sort: "year" | reverse %}
{% if journal_papers.size > 0 %}
{% for paper in journal_papers %}
<div class="publication-item">
    <div class="publication-content">
        <span class="publication-number">{{ forloop.length | minus: forloop.index0 }}.</span>
        <span class="publication-title">{{ paper.title }}</span>
        {% if paper.authors != "Y. Fang" and paper.authors != "Fang, Y." %}
        <span class="publication-authors"> with {{ paper.authors | remove: "Fang, Y., " | remove: ", Fang, Y." | remove: "Y. Fang, " | remove: ", Y. Fang" }}</span>
        {% endif %}
        <span class="publication-meta">, {{ paper.journal }}, {{ paper.year }}{% if paper.volume %}, Vol. {{ paper.volume }}{% endif %}{% if paper.issue %}, No. {{ paper.issue }}{% endif %}{% if paper.pages %}, pp. {{ paper.pages }}{% endif %}</span>
        {% if paper.doi %}
        <span class="publication-links"> [<a href="https://doi.org/{{ paper.doi }}" target="_blank">DOI</a>]</span>
        {% endif %}
        {% if paper.code %}
        <span class="publication-links"> [<a href="{{ paper.code }}" target="_blank">Code</a>]</span>
        {% endif %}
        {% if paper.abstract %}
        <span class="publication-links"> [<button class="abstract-toggle" data-target="abstract-{{ forloop.index }}">Abstract</button>]</span>
        {% endif %}
    </div>
    {% if paper.abstract %}
    <div class="publication-abstract" id="abstract-{{ forloop.index }}">{{ paper.abstract }}</div>
    {% endif %}
</div>
{% endfor %}
{% else %}
<div class="no-publications">No publications available at the moment.</div>
{% endif %}
</section>

<script>
document.addEventListener('DOMContentLoaded', function() {
    const abstractButtons = document.querySelectorAll('.abstract-toggle');
    
    // 初始隐藏所有摘要
    document.querySelectorAll('.publication-abstract').forEach(abstract => {
        abstract.style.display = 'none';
    });
    
    abstractButtons.forEach(button => {
        button.addEventListener('click', function() {
            const targetId = this.getAttribute('data-target');
            const abstractDiv = document.getElementById(targetId);
            
            if (abstractDiv) {
                const isVisible = abstractDiv.style.display !== 'none';
                
                if (isVisible) {
                    abstractDiv.style.display = 'none';
                    this.textContent = 'Abstract';
                } else {
                    abstractDiv.style.display = 'block';
                    this.textContent = 'Hide Abstract';
                }
            }
        });
    });
});
</script>
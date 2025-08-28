---
layout: default
title: Research
---

<section class="section">
## Preprints

{% assign preprints = site.data.publications | where: "type", "preprint" | sort: "year" | reverse %}
{% if preprints.size > 0 %}
{% for paper in preprints %}
<div class="publication-item">
    <div class="publication-header">
        <span class="publication-number">{{ forloop.length | minus: forloop.index0 }}.</span>
        <span class="publication-title">{{ paper.title }}</span>
        {% if paper.authors != "Y. Fang" and paper.authors != "Fang, Y." %}
        <span class="publication-authors"> with {{ paper.authors | remove: "Fang, Y., " | remove: ", Fang, Y." | remove: "Y. Fang, " | remove: ", Y. Fang" }}</span>
        {% endif %}
    </div>
    <div class="publication-meta">
        <span class="publication-info">{{ paper.archive }}, {{ paper.year }}</span>
        {% if paper.arxiv %}
        <span class="publication-links">[<a href="https://arxiv.org/abs/{{ paper.arxiv }}" target="_blank">arXiv</a>]</span>
        {% endif %}
        {% if paper.abstract %}
        <span class="publication-links">[<button class="abstract-toggle" data-target="abstract-preprint-{{ forloop.index }}">Abstract</button>]</span>
        {% endif %}
    </div>
    {% if paper.abstract %}
    <div class="publication-abstract-container">
        <div class="publication-abstract" id="abstract-preprint-{{ forloop.index }}">{{ paper.abstract }}</div>
    </div>
    {% endif %}
</div>
{% endfor %}
{% else %}
<div class="no-publications">No preprints available at the moment.</div>
{% endif %}
</section>

<section class="section">
## Publications

{% assign journal_papers = site.data.publications | where: "type", "journal" | sort: "year" | reverse %}
{% if journal_papers.size > 0 %}
{% for paper in journal_papers %}
<div class="publication-item">
    <div class="publication-header">
        <span class="publication-number">{{ forloop.length | minus: forloop.index0 }}.</span>
        <span class="publication-title">{{ paper.title }}</span>
        {% if paper.authors != "Y. Fang" and paper.authors != "Fang, Y." %}
        <span class="publication-authors"> with {{ paper.authors | remove: "Fang, Y., " | remove: ", Fang, Y." | remove: "Y. Fang, " | remove: ", Y. Fang" }}</span>
        {% endif %}
    </div>
    <div class="publication-meta">
        <span class="publication-info">{{ paper.journal }}, {{ paper.year }}{% if paper.volume %}, Vol. {{ paper.volume }}{% endif %}{% if paper.issue %}, No. {{ paper.issue }}{% endif %}{% if paper.pages %}, pp. {{ paper.pages }}{% endif %}</span>
        {% if paper.doi %}
        <span class="publication-links">[<a href="https://doi.org/{{ paper.doi }}" target="_blank">DOI</a>]</span>
        {% endif %}
        {% if paper.code %}
        <span class="publication-links">[<a href="{{ paper.code }}" target="_blank">Code</a>]</span>
        {% endif %}
        {% if paper.abstract %}
        <span class="publication-links">[<button class="abstract-toggle" data-target="abstract-{{ forloop.index }}">Abstract</button>]</span>
        {% endif %}
    </div>
    {% if paper.abstract %}
    <div class="publication-abstract-container">
        <div class="publication-abstract" id="abstract-{{ forloop.index }}">{{ paper.abstract }}</div>
    </div>
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
    
    abstractButtons.forEach(button => {
        button.addEventListener('click', function() {
            const targetId = this.getAttribute('data-target');
            const abstractDiv = document.getElementById(targetId);
            
            if (abstractDiv) {
                const isVisible = abstractDiv.classList.contains('open');
                
                if (isVisible) {
                    // 隐藏动画
                    abstractDiv.classList.remove('open');
                    this.textContent = 'Abstract';
                } else {
                    // 显示动画
                    abstractDiv.classList.add('open');
                    this.textContent = 'Hide Abstract';
                }
            }
        });
    });
});
</script>
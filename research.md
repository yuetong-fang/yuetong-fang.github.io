---
layout: page
title: Research
---

## Preprints

{% assign preprints = site.data.publications | where: "type", "preprint" | sort: "year" | reverse %}
{% if preprints.size > 0 %}
<div class="publication-list">
    {% for paper in preprints %}
    <div class="publication-item">
        <span class="publication-number">{{ forloop.length | minus: forloop.index0 }}.</span>
        <div class="publication-details">
            <div class="publication-title">{{ paper.title }}</div>
            {% if paper.authors != "Fang, Y." %}
            <div class="publication-authors">with {{ paper.authors | remove: "Fang, Y., " | remove: ", Fang, Y." }}</div>
            {% endif %}
            <div class="publication-meta">
                <span class="publication-archive">{{ paper.archive }}</span>, 
                <span class="publication-year">{{ paper.year }}</span>
            </div>
            <div class="publication-links">
                {% if paper.pdf %}
                <a href="{{ paper.pdf }}" target="_blank">PDF</a>
                {% endif %}
                {% if paper.arxiv %}
                <a href="https://arxiv.org/abs/{{ paper.arxiv }}" target="_blank">arXiv</a>
                {% endif %}
                {% if paper.abstract %}
                <button class="abstract-toggle" data-target="abstract-preprint-{{ forloop.index }}">Abstract</button>
                {% endif %}
            </div>
            {% if paper.abstract %}
            <div class="publication-abstract" id="abstract-preprint-{{ forloop.index }}" style="display: none;">
                {{ paper.abstract }}
            </div>
            {% endif %}
        </div>
    </div>
    {% endfor %}
</div>
{% else %}
<div class="no-publications">
    No preprints available at the moment.
</div>
{% endif %}

## Publications

{% assign journal_papers = site.data.publications | where: "type", "journal" | sort: "year" | reverse %}
{% if journal_papers.size > 0 %}
<div class="publication-list">
    {% for paper in journal_papers %}
    <div class="publication-item">
        <span class="publication-number">{{ forloop.length | minus: forloop.index0 }}.</span>
        <div class="publication-details">
            <div class="publication-title">{{ paper.title }}</div>
            {% if paper.authors != "Fang, Y." %}
            <div class="publication-authors">with {{ paper.authors | remove: "Fang, Y., " | remove: ", Fang, Y." }}</div>
            {% endif %}
            <div class="publication-meta">
                <span class="publication-journal">{{ paper.journal }}</span>, 
                <span class="publication-year">{{ paper.year }}</span>
                {% if paper.volume %}, Vol. {{ paper.volume }}{% endif %}
                {% if paper.issue %}, No. {{ paper.issue }}{% endif %}
                {% if paper.pages %}, pp. {{ paper.pages }}{% endif %}
            </div>
            <div class="publication-links">
                {% if paper.pdf %}
                <a href="{{ paper.pdf }}" target="_blank">PDF</a>
                {% endif %}
                {% if paper.code %}
                <a href="{{ paper.code }}" target="_blank">Code</a>
                {% endif %}
                {% if paper.doi %}
                <a href="https://doi.org/{{ paper.doi }}" target="_blank">DOI</a>
                {% endif %}
                {% if paper.abstract %}
                <button class="abstract-toggle" data-target="abstract-{{ forloop.index }}">Abstract</button>
                {% endif %}
            </div>
            {% if paper.abstract %}
            <div class="publication-abstract" id="abstract-{{ forloop.index }}" style="display: none;">
                {{ paper.abstract }}
            </div>
            {% endif %}
        </div>
    </div>
    {% endfor %}
</div>
{% else %}
<div class="no-publications">
    No publications available at the moment.
</div>
{% endif %}

<script>
document.addEventListener('DOMContentLoaded', function() {
    const abstractButtons = document.querySelectorAll('.abstract-toggle');
    
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
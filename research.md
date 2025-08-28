---
layout: page
title: "Research"

---
<section class="publications-section">
        <h2 class="section-title">Preprints</h2>
<!-- 预印本 -->
        {% assign preprints = site.data.publications | where: "type", "preprint" | sort: "year" | reverse %}
        {% if preprints.size > 0 %}
        <div class="publication-list">
            {% for paper in preprints %}
            <div class="publication-item" id="preprint-{{ forloop.index }}">
                <span class="publication-number">{{ forloop.length | minus: forloop.index0 }}.</span>
                <div class="publication-details">
                    <h3 class="publication-title">{{ paper.title }}</h3>
                    <p class="publication-authors">{{ paper.authors }}</p>
                    <p class="publication-meta">
                        <span class="publication-archive">{{ paper.archive }}</span>, 
                        <span class="publication-year">{{ paper.year }}</span>
                    </p>
                    <div class="publication-links">
                        {% if paper.pdf %}
                        <a href="{{ paper.pdf }}" class="pub-link" target="_blank">
                            <i class="fas fa-file-pdf"></i> PDF
                        </a>
                        {% endif %}
                        {% if paper.arxiv %}
                        <a href="https://arxiv.org/abs/{{ paper.arxiv }}" class="pub-link" target="_blank">
                            <i class="fas fa-external-link-alt"></i> arXiv
                        </a>
                        {% endif %}
                        {% if paper.abstract %}
                        <button class="pub-link abstract-toggle" data-target="abstract-preprint-{{ forloop.index }}">
                            <i class="fas fa-quote-left"></i> Abstract
                        </button>
                        {% endif %}
                    </div>
                    {% if paper.abstract %}
                    <div class="publication-abstract" id="abstract-preprint-{{ forloop.index }}" style="display: none;">
                        <p>{{ paper.abstract }}</p>
                    </div>
                    {% endif %}
                </div>
            </div>
            {% endfor %}
        </div>
        {% else %}
        <p class="no-preprints">No preprints available at the moment.</p>
        {% endif %}
    </section>



    <section class="publications-section">
        <h2 class="section-title">Publications</h2>
        
        <!-- 期刊文章 -->
        {% assign journal_papers = site.data.publications | where: "type", "journal" | sort: "year" | reverse %}
        {% if journal_papers.size > 0 %}
        <div class="publication-list">
            {% for paper in journal_papers %}
            <div class="publication-item" id="pub-{{ forloop.index }}">
                <span class="publication-number">{{ forloop.length | minus: forloop.index0 }}.</span>
                <div class="publication-details">
                    <h3 class="publication-title">{{ paper.title }}</h3>
                    <p class="publication-authors">{{ paper.authors }}</p>
                    <p class="publication-meta">
                        <span class="publication-journal">{{ paper.journal }}</span>, 
                        <span class="publication-year">{{ paper.year }}</span>
                        {% if paper.volume %}
                        , <span class="publication-volume">Vol. {{ paper.volume }}</span>
                        {% endif %}
                        {% if paper.issue %}
                        , No. {{ paper.issue }}
                        {% endif %}
                        {% if paper.pages %}
                        , pp. {{ paper.pages }}
                        {% endif %}
                    </p>
                    <div class="publication-links">
                        {% if paper.pdf %}
                        <a href="{{ paper.pdf }}" class="pub-link" target="_blank">
                            <i class="fas fa-file-pdf"></i> PDF
                        </a>
                        {% endif %}
                        {% if paper.code %}
                        <a href="{{ paper.code }}" class="pub-link" target="_blank">
                            <i class="fas fa-code"></i> Code
                        </a>
                        {% endif %}
                        {% if paper.doi %}
                        <a href="https://doi.org/{{ paper.doi }}" class="pub-link" target="_blank">
                            <i class="fas fa-external-link-alt"></i> DOI
                        </a>
                        {% endif %}
                        {% if paper.abstract %}
                        <button class="pub-link abstract-toggle" data-target="abstract-{{ forloop.index }}">
                            <i class="fas fa-quote-left"></i> Abstract
                        </button>
                        {% endif %}
                    </div>
                    {% if paper.abstract %}
                    <div class="publication-abstract" id="abstract-{{ forloop.index }}" style="display: none;">
                        <p>{{ paper.abstract }}</p>
                    </div>
                    {% endif %}
                </div>
            </div>
            {% endfor %}
        </div>
        {% endif %}
    </section>


<script>
// Abstract显示/隐藏功能
document.addEventListener('DOMContentLoaded', function() {
    const abstractToggles = document.querySelectorAll('.abstract-toggle');
    
    abstractToggles.forEach(toggle => {
        toggle.addEventListener('click', function() {
            const targetId = this.getAttribute('data-target');
            const abstract = document.getElementById(targetId);
            
            if (abstract) {
                const isVisible = abstract.style.display === 'block';
                abstract.style.display = isVisible ? 'none' : 'block';
                
                // 更新按钮文本
                const icon = this.querySelector('i');
                if (isVisible) {
                    this.innerHTML = '<i class="fas fa-quote-left"></i> Abstract';
                } else {
                    this.innerHTML = '<i class="fas fa-eye-slash"></i> Hide Abstract';
                }
                
                // 平滑滚动到摘要
                if (!isVisible) {
                    abstract.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
                }
            }
        });
    });
});
</script>

<script>
// Abstract
document.addEventListener('DOMContentLoaded', function() {
    const abstractToggles = document.querySelectorAll('.abstract-toggle');
    
    abstractToggles.forEach(toggle => {
        toggle.addEventListener('click', function() {
            const targetId = this.getAttribute('data-target');
            const abstract = document.getElementById(targetId);
            
            if (abstract) {
                const isVisible = abstract.style.display === 'block';
                abstract.style.display = isVisible ? 'none' : 'block';
                
                // 更新按钮文本
                const icon = this.querySelector('i');
                if (isVisible) {
                    this.innerHTML = '<i class="fas fa-quote-left"></i> Abstract';
                } else {
                    this.innerHTML = '<i class="fas fa-eye-slash"></i> Hide Abstract';
                }
                
                // 平滑滚动到摘要
                if (!isVisible) {
                    abstract.scrollIntoView({ behavior: 'smooth', block: 'nearest' });
                }
            }
        });
    });
});
</script>
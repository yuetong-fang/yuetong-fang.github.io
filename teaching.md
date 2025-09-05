---
layout: default
title: "Teaching"
---
<div class="page-title">
    <h1>Teachings</h1>
</div>

<section class="section">
    <h3 class="section-title">Current Teachings</h3>
{% assign courses = site.data.teaching | sort: "term" | reverse %}
{% if courses.size > 0 %}
{% for course in courses %}
<div class="course-item">
    <div class="course-header">
        <span class="course-title">{{ course.name }}</span>
    </div>
    <div class="course-meta">
        <span class="course-info">
            {% if course.term %}{{ course.term }}{% if course.type or course.code %}, {% endif %}{% endif %}
            {% if course.type %}{{ course.type }}{% if course.code %} ({{ course.code }}){% endif %}{% endif %}
            {% if course.code and course.term == nil and course.type == nil %}({{ course.code }}){% endif %}
        </span>
    </div>
</div>
{% endfor %}
{% else %}
<div class="no-courses">No courses available at the moment.</div>
{% endif %}
</section>


<section>



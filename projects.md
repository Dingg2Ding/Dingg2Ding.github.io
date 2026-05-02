---
layout: page
title: Projects
permalink: /projects/
comments: false
---

<div class="project-section">
  <div class="project-category">Graduate School</div>
  <div class="project-list">
    {% assign sorted_projects = site.projects | sort: 'date' | reverse %}
    {% for project in sorted_projects %}
    <article class="project-entry">
      <a href="{{ project.url }}" class="project-thumb project-thumb-{{ project.title | slugify }}" aria-label="{{ project.title }}">
        {% if project.thumbnail %}
        <img src="{{ project.thumbnail }}" alt="{{ project.title }} preview">
        {% else %}
        <span>{{ project.title | slice: 0, 2 }}</span>
        {% endif %}
      </a>
      <div class="project-copy">
        {% if project.badge %}
        <div class="project-award">{{ project.badge }}</div>
        {% endif %}
        <h2 class="project-title">
          <a href="{{ project.url }}">{{ project.title }}</a>
        </h2>
        <p class="project-desc">{{ project.description }}</p>
        <p class="project-role">{{ project.role }}</p>
        <div class="project-meta">
          {% if project.period %}<span>{{ project.period }}</span>{% endif %}
          {% if project.venue %}<span>{{ project.venue }}</span>{% endif %}
          {% if project.publication_summary %}<span>{{ project.publication_summary }}</span>{% endif %}
        </div>
        <div class="project-links">
          {% if project.project_tags %}
            {% for tag in project.project_tags.platform %}<span>{{ tag }}</span>{% endfor %}
            {% for tag in project.project_tags.domain %}<span>{{ tag }}</span>{% endfor %}
            {% for tag in project.project_tags.technical %}<span>{{ tag }}</span>{% endfor %}
            {% for tag in project.project_tags.output %}<span>{{ tag }}</span>{% endfor %}
          {% else %}
            {% for tag in project.tags %}<span>{{ tag }}</span>{% endfor %}
          {% endif %}
        </div>
      </div>
    </article>
    {% endfor %}
  </div>
</div>

<div class="project-section">
  <div class="project-category">Undergraduate</div>
  
  <a href="https://dinggiding.github.io" target="_blank" class="university-link">
    <span class="project-title" style="margin:0">Undergraduate Portfolio / Projects</span>
    <svg class="arrow-icon" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path></svg>
  </a>
</div>

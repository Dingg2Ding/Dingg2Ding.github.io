---
layout: page
title: Projects
permalink: /projects/
comments: false
body_class: projects-page
---

<div class="project-section">
  <div class="project-category">
    <span>M.S. · Yonsei University</span>
    <span>{{ site.projects | size }} projects</span>
  </div>
  <div class="project-list">
    {% assign sorted_projects = site.projects | sort: 'date' | reverse %}
    {% for project in sorted_projects %}
    <article class="project-entry{% if project.thumbnail %} project-entry-has-media{% endif %}">
      {% if project.thumbnail %}
      <a href="{{ project.url }}" class="project-media" aria-label="View {{ project.title }}">
        <img src="{{ project.thumbnail }}" alt="{{ project.title }} preview" loading="lazy">
      </a>
      {% endif %}
      <div class="project-copy">
        {% if project.badge %}
        <div class="project-award">{{ project.badge }}</div>
        {% endif %}
        <h2 class="project-title">
          <a href="{{ project.url }}">{{ project.title }}</a>
        </h2>
        <p class="project-desc">{{ project.description }}</p>
        <div class="project-meta">
          {% if project.period %}<span>{{ project.period }}</span>{% endif %}
          {% if project.venue %}<span>{{ project.venue }}</span>{% endif %}
        </div>
        {% assign linked_publication_count = 0 %}
        {% for publication in site.data.publications %}
          {% if publication.projects contains project.project_id %}
            {% assign linked_publication_count = linked_publication_count | plus: 1 %}
          {% endif %}
        {% endfor %}
        {% if linked_publication_count > 0 %}
        <div class="project-output-preview">
          <div class="project-output-heading">
            <span>{% if linked_publication_count == 1 %}Publication{% else %}Publications{% endif %}</span>
            <a href="{{ project.url }}#research-outputs">
              {{ linked_publication_count }} {% if linked_publication_count == 1 %}output{% else %}outputs{% endif %}
              <span aria-hidden="true">&rarr;</span>
            </a>
          </div>
          <div class="project-output-list">
            {% for publication in site.data.publications %}
              {% if publication.projects contains project.project_id %}
              <a class="project-output-item" href="{{ project.url }}#publication-{{ publication.id }}">
                <span class="project-output-copy">
                  <span class="project-output-title">{{ publication.title }}</span>
                  {% if publication.venue %}<span class="project-output-venue">{{ publication.venue }}</span>{% endif %}
                </span>
                <span class="publication-status publication-status-{{ publication.status | slugify }}">{{ publication.status }}</span>
              </a>
              {% endif %}
            {% endfor %}
          </div>
        </div>
        {% endif %}
        <div class="project-links">
          {% for tag in project.tags %}<span>{{ tag }}</span>{% endfor %}
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

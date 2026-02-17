---
layout: page
title: Projects
permalink: /projects/
comments: false
---

<style>
  /* Define point color locally */
  :root {
    --point-color: #EB5E28; /* Requested Point Color */
  }

  .project-section {
    margin-bottom: 4rem;
  }
  
  .project-category {
    font-size: 0.9rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: inherit; /* Inherits main text color (Black/White depending on theme) */
    opacity: 1;     /* Full opacity for strict Black/White feel, or keep 0.6 for hierarchy? Let's use 0.7 for slight hierarchy but keeps it grayscale */
    opacity: 0.7;
    margin-bottom: 1.5rem;
    font-weight: 600;
    position: relative;
    padding-left: 12px;
  }

  /* Point 1: Small accent mark for category */
  .project-category::before {
    content: '';
    position: absolute;
    left: 0;
    top: 50%;
    transform: translateY(-50%);
    width: 3px;
    height: 12px;
    background-color: var(--point-color);
    border-radius: 1px;
  }
  
  .project-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 2rem;
  }
  
  .project-card {
    display: flex;
    flex-direction: column;
    padding: 2rem;
    border-radius: 4px; 
    background: rgba(128, 128, 128, 0.03); 
    transition: all 0.2s ease;
    text-decoration: none !important;
    color: inherit !important; /* Force text color to stay inherited (Black/White) */
    border: 1px solid transparent; 
  }

  /* Hover state: Point color on border/shadow/transform only */
  /* Text remains neutralized */
  .project-card:hover {
    transform: translateY(-2px);
    background: rgba(128, 128, 128, 0.05);
    border-color: var(--point-color); /* Point Color Border */
    /* Optional: minimal glow */
    box-shadow: 0 4px 12px rgba(235, 94, 40, 0.1); 
  }
  
  .project-title {
    font-size: 1.25rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
    line-height: 1.3;
    color: inherit; 
  }
  
  .project-period {
    font-size: 0.8rem;
    opacity: 0.5;
    margin-bottom: 0.5rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }
  
  .project-desc {
    font-size: 0.95rem;
    opacity: 0.8;
    margin-bottom: 1rem;
    flex-grow: 1;
    line-height: 1.5;
    color: inherit;
  }
  
  .project-meta {
    font-size: 0.8rem;
    opacity: 0.5;
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    color: inherit;
  }
  
  .project-tag {
    padding: 2px 0;
  }

  /* University Link */
  .university-link {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 2rem;
    border: 1px solid rgba(128,128,128, 0.2);
    border-radius: 4px;
    text-decoration: none !important;
    transition: all 0.2s ease;
    color: inherit !important;
    position: relative;
    overflow: hidden;
  }
  
  /* Point Hover Effect */
  .university-link:hover {
    border-color: var(--point-color);
    background: rgba(128, 128, 128, 0.02);
  }

  .university-link:before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 3px;
    background: var(--point-color);
    transform: scaleY(0);
    transform-origin: bottom;
    transition: transform 0.2s ease;
  }

  .university-link:hover:before {
    transform: scaleY(1);
  }
  
  .arrow-icon {
    width: 20px;
    height: 20px;
    transition: transform 0.2s;
    opacity: 0.3;
    stroke: currentColor; /* Default to text color */
  }

  /* Icon gets point color on hover */
  .university-link:hover .arrow-icon {
    transform: translateX(5px);
    opacity: 1;
    stroke: var(--point-color);
  }
</style>

<div class="project-section">
  <div class="project-category">Graduate School</div>
  <div class="project-grid">
    
    {% assign sorted_projects = site.projects | sort: 'date' %}
    {% for project in sorted_projects %}
    <a href="{{ project.url }}" class="project-card">
      <div class="project-period">{{ project.period }}</div>
      <div class="project-title">{{ project.title }}</div>
      <div class="project-desc">{{ project.description }}</div>
      <div class="project-meta">
        {% for tag in project.tags %}
        <span class="project-tag">{{ tag }}</span>
        {% unless forloop.last %}
        <span class="project-tag">·</span>
        {% endunless %}
        {% endfor %}
      </div>
    </a>
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

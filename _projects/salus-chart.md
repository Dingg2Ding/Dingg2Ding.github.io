---
layout: post
title: SalusChart
period: "2025.03 - Present"
permalink: /projects/SalusChart/
description: Mobile-first data visualization library for health and tracking data (Android/Compose).
date: 2025-03-06
tags: [Android, Visualization, Library, Mobile]
---

## **Overview**

SalusChart is an independent, production-grade **mobile-first data visualization library** designed for health and tracking data. It is built to produce readable and reliable charts on small screens, and it is integrated as a module inside my modular data tracking application.

### **Why This Project**

Many chart libraries can render charts, but good health visualizations on mobile are difficult without visualization expertise. SalusChart focuses on two practical goals:

1. **Mobile-optimized visualization by default** (layout, scaling, touch, readability)
2. **High-quality results even for non-visualization experts**, through strong defaults and guided configuration

## **Problem**

- Mobile chart UX often breaks due to scaling and typography issues across devices.
- Interactions (scrolling, paging, tooltips, zoom/landscape behavior) are fragile on mobile.
- Choosing the wrong chart type or unclear styling can make health data misleading or hard to interpret.
- Real-world tracking data frequently includes gaps, irregular sampling, and time-related complexity, which many general-purpose chart libraries do not handle well.

## **Design Principles**

- **Mobile-first scaling:** validate chart layouts across screen sizes and densities.
- **Readable typography:** consistent rules for chart titles, axis labels, data labels, and legends.
- **Interaction reliability:** paging + scrolling as primary interactions, with stable touch targets.
- **Smart defaults:** sensible chart choices and styling so users get “good charts” without needing to be visualization experts.

## **What I Built / Contributed**

- Led the **initial architecture, design guidelines, and core implementation** of SalusChart as a standalone library.
- Implemented mobile interaction foundations centered on **paging and scrolling** to support exploration on small screens.
- Established chart UX rules and a checklist based on common mHealth visualization issues (scaling, styling, interactivity, chart type fit).
- Documented improvement targets and performance notes to guide later optimization and refinements.

> Note: I led the early design and implementation phase. The later polishing and final completion were handed off to another contributor.

## **Chart Coverage (Examples)**

SalusChart supports multiple chart patterns for health/tracking data, including:

- Trend charts (e.g., line/area-style patterns)
- Bar-style summaries (including stacked patterns)
- Calendar-style views
- Domain-specific views such as sleep-stage style representations
    
    (Exact chart set evolves as the library expands inside the tracking platform.)

## **Tech and Keywords**

Android, Kotlin, Jetpack Compose, Mobile Data Visualization, Custom Chart Components, Progressive Disclosure, Smart Defaults

## **Outcome**

A production-grade mobile visualization library that emphasizes **mobile usability and strong defaults**. SalusChart makes it easier for teams to create high-quality health charts without requiring a visualization specialist for every design decision.

## **Future Work**

- Publish deeper performance and design rationale as blog posts (e.g., performance bottlenecks, interaction trade-offs, and “smart default” decisions).
- Expand integration in the modular data tracking platform to standardize visualization across studies.

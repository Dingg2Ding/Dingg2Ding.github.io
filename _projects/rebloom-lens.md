---
layout: post
title: ReBloomLens
period: "2025.01 - Present"
permalink: /projects/ReBloomLens/
description: Routine-based health tracking platform for breast cancer survivors (Samsung Health + Daily Reflection).
date: 2025-03-07
tags: [Android, Samsung Health, Visualization, Research]
---

## **Overview**

ReBloomLens is a production-level research tracking experience for **breast cancer survivors**, built as part of my **modular data tracking application**. It focuses on connecting **Samsung Health activity and sleep data** with user-facing **routine tracking** and **mobile-first visualization** for daily reflection.

## **Scope**

- Production-level implementation within a modular tracking app (the overall platform is still evolving).
- Primary data sources: **Samsung Health activity + sleep**.
- Primary user features: **routine check-ins** and **backtracking** based on real health data.

## **Problem**

- Daily experiences around recovery and lifestyle change are difficult to reflect on without continuous behavioral context.
- Health data alone is not enough; users also need a routine-oriented layer to interpret “did I do what I planned?”.
- Mobile health charts often become unreadable or misleading without mobile-first visualization design.

## **Goals**

- Support routine-oriented tracking that connects directly to real health data.
- Provide clear mobile visualizations for personal reflection (not researcher dashboards).
- Make the system reusable inside a modular architecture so similar studies can be configured and extended.

## **System Design**

### **Health data integration**
Samsung Health SDK as the primary data source (sleep + exercise).

### **Routine layer**
User routines are evaluation and displayed by linking planned routines with actual health records (backtracking).

### **Visualization**
User-facing health graphs are rendered using **SalusChart** to ensure mobile readability.

## **Key User Flows**

1. **Routine check**
   - Users review their sleep/exercise routines and confirm completion status.
   - The app contextualizes the routine using actual Samsung Health records.
2. **Data reflection**
   - Users explore their sleep and exercise data through mobile-first charts (SalusChart).
   - The focus is on quick understanding and daily reflection rather than expert analysis.

## **What I Built / Contributed**

- Implemented the Samsung Health integration focused on **sleep and exercise**.
- Designed and implemented the **routine + backtracking** concept that links user routines to real health data.
- Integrated SalusChart to support consistent, mobile-optimized visualization for user reflection.
- Designed the end-to-end user-facing UI (Toss Design System-inspired) for routine check-ins and health data reflection.

## **Collaboration**

- Collaborated with another HCI lab at **Yonsei University** on the research context and direction.

## **Tech and Keywords**

Android, Kotlin, Jetpack Compose, Samsung Health SDK, Mobile Health Tracking, Routine/Backtracking, Mobile Data Visualization (SalusChart), Modular Architecture

## **Outcome**

A production-level user-facing tracking experience that connects **real sleep/exercise data** with **routine-based reflection**, supported by mobile-first visualization. This work demonstrates how routine tracking can be grounded in objective health records rather than self-report alone.

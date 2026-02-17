---
layout: post
title: Modular Data Tracking Application Platform
period: "2025.03 - Present"
permalink: /projects/Modular-Data-Tracking-Application-Platform/
description: Plugin-based, configuration-driven mobile tracking platform for research studies.
date: 2025-03-09
tags: [Android, Research, Platform, Architecture]
---

## **Overview**

This project is a plugin-based, configuration-driven mobile tracking platform for research studies. It lets researchers compose and run study protocols through JSON (including schedules, instruments, and UI blocks), while developers focus on building a stable runtime and reusable modules.

## **Why This Project**

Most research platforms lean toward “survey-first” systems with fixed sensing pipelines. This platform treats surveys, sensors, health data, routines, notifications, and visualization as **equal protocol components**, making it closer to a **Study Runtime / Protocol Engine** than a single survey app.

## **Problem**

- Each study often requires repeated custom development and brittle one-off app changes.
- Protocol changes are hard to track and reproduce, weakening methodological clarity.
- Mobile OS constraints make reliable collection and scheduling difficult.
- Researchers need operational support such as monitoring coverage and exporting data.

## **Goals**

- Enable protocol composition through configuration rather than rebuilding the app per study.
- Separate a stable core runtime from flexible plugins.
- Support multi-source collection and study-specific scheduling.
- Treat study configuration as a versionable artifact to improve reproducibility.

## **System Design**

- **Config-driven execution (JSON):** configuration controls plugin composition, schedules, surveys/routines, and SDUI-style UI blocks.
- **Plugin-based architecture:** modules can include collection logic and (depending on the plugin) UI components.
- **Local-first storage:** data is persisted locally with **Room**, then synced to **Firebase** as the server layer.
- **Platform-level scheduling support:** baseline scheduling infrastructure is provided so plugins can reuse reliability-sensitive patterns.

## **What I Built / Contributed**

- Designed the overall platform architecture (core runtime vs plugins).
- Implemented JSON-driven protocol execution, including schedules and UI blocks.
- Built multi-source collection foundations (survey, sensors, health integrations, routines, notifications, visualization).
- Implemented local-first persistence with Room and Firebase-backed syncing.
- Started researcher tooling to reduce friction from editing JSON directly.

## **Key Features**

- Plugin-based module composition for study protocols
- JSON configuration bundles for instruments, schedules, and UI blocks
- Offline-first data capture (Room) with Firebase sync
- Reproducible, versionable protocol configuration as a first-class artifact
- Researcher tool in progress: drag-and-drop protocol builder with live preview

## **Tech and Keywords**

Android, Kotlin, Jetpack Compose, Modular Architecture, Plugin System, Protocol Engine / Study Runtime, JSON-driven Configuration + SDUI, Room, Firebase, Offline-first Data Collection, Research Operations Tooling

## **Outcome**

A reusable study protocol engine that reduces repeated study-specific development by turning protocol customization into configuration and composable plugins. It enables researchers to act as protocol designers without programming, while keeping developers focused on building a stable, extensible runtime.

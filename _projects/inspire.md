---
layout: post
title: INSPIRE
period: "2025.09 - Present"
permalink: /projects/INSPIRE/
description: Production-level research tracking app designed for real study operations (Android).
date: 2025-03-08
tags: [Android, Research, Data Collection, Samsung Health]
---

## **Overview**

INSPIRE is a production-level research tracking app designed for real study operations. It is currently in internal testing and preparing for a full-scale study. The project focuses on reliable data collection under mobile OS constraints, repeatable configuration for different studies, and practical monitoring so researchers can verify data quality during deployment.

## **Context and Collaboration**

INSPIRE is conducted in collaboration with **Yonsei University College of Nursing**. I owned the **end-to-end engineering scope** of the mobile app (excluding the cognitive games module).

## **Problem**

- In real studies, “it works on my phone” is not enough. Reliability must hold across devices, OS background limits, and daily routines.
- Multi-source data collection increases operational risk: missed notifications, interrupted background work, recording failures, and inconsistent data coverage.
- Researchers need visibility into whether data is actually being collected day by day, not just stored somewhere in the backend.

## **Goals**

- Collect multi-source behavioral and health data reliably in real-world conditions.
- Support repeatable, study-specific configurations without rewriting the app.
- Provide monitoring and researcher tooling to detect missing data early and reduce operational overhead.

## **Data Sources and Collection Scope**

- **Sensor data:** accelerometer and device context signals (e.g., phone state, screen state).
- **Health data (Samsung Health SDK):** 6 key health data types aligned with the study protocol.
- **Surveys:** scheduled 4 times per day.
- **Audio recordings:** short, clip-based audio responses collected within the survey flow.

## **System Design (Operational Focus)**

- **Config-driven study setup:** most protocol settings are defined in JSON-based configurations, aligned with the modular tracking architecture direction.
- **Offline-first collection mindset:** data is captured safely under unstable connectivity and synced reliably later.
- **Monitoring and observability:** operational visibility is treated as a first-class requirement for real deployments.

## **What I Built / Contributed**

- Built the INSPIRE mobile app end-to-end (**Android**), covering data collection modules, scheduling, storage/sync, and user flows (excluding cognitive games).
- Integrated the **Samsung Health SDK** and aligned health data with sensor and survey pipelines.
- Implemented scheduled surveys (4/day) and audio recording collection flows.
- Added monitoring using **Firebase Crashlytics** and structured logging to support debugging during internal testing.
- Developed researcher tooling to:
    - download/export study data, and
    - check daily-level coverage (whether data arrived each day per participant), enabling faster issue detection during deployment.

## **Reliability Work (Implementation Details)**

- **Hybrid scheduling for real-world constraints:** I combined `WorkManager` + `AlarmManager` + `ForegroundService` to balance reliability and OS restrictions.
    - `WorkManager` runs periodic background sync workers (e.g., Health/Sensor/External metric sync) on a practical cadence suitable for OS constraints.
    - `AlarmManager` triggers time-critical reminders using exact alarms (with limited re-reminders).
    - `ForegroundService` supports continuous sensor collection and uses health-check style restarts to recover from interruptions.
- **Audio collection as an explicit user action:** audio is recorded through a user-triggered survey interaction (start/stop button), producing short clip-based responses saved as .m4a (AAC).
- **Hybrid storage strategy (Firestore + Storage):** structured study data (surveys, sensors, health metrics) syncs to Firestore, while audio files upload to Firebase Storage. The resulting download URL is stored back into the Firestore response metadata.

## **Tech Stack / Tools**

Android, Kotlin, Jetpack Compose, Firebase (Firestore, Storage, Crashlytics), WorkManager, AlarmManager, ForegroundService, Samsung Health SDK, JSON-based configuration, researcher export/coverage tooling

## **Outcome**

A production-level research tracking app ready for real deployment: multi-source data collection (sensors + Samsung Health + surveys + audio), operational monitoring via Crashlytics, and researcher-facing tooling for export and daily coverage verification. The system is designed to scale from internal testing to a full study with reduced operational risk.

## **Next**

- Expand the deployment workflow from internal testing to the full study.
- Continue hardening reliability and document key lessons learned through blog posts.

---
layout: post
title: DrugQ
period: "2025.07 - Present"
permalink: /projects/DrugQ/
description: Multimodal OTC Drug Safety Assistant (Android Research Prototype)
date: 2025-03-05
tags: [Android, AI, Healthcare, Research]
---

## **Overview**

DrugQ is an Android research prototype for a multimodal OTC drug safety assistant. It supports voice and image inputs to help users make safer medication decisions, then returns an easy-to-understand safety verdict with an explanation.

## **Scope**

- Implemented as a working Android prototype (not only a concept).
- Initial medication set: **Tylenol, Aspirin, Benadryl, and Rolaids**.
- Primary symptom contexts: common everyday cases such as **cold/flu-like symptoms and allergies**.

## **Problem**

- OTC medication guidance is often unclear for non-experts.
- Users may not know how to interpret warnings, contraindications, or drug interactions.
- When users feel unwell, they need a fast, low-effort way to get a safety-oriented answer.

## **System Design**

### **Inputs**
- **Voice:** users speak the drug name and describe symptoms. Voice is transcribed via **OpenAI Whisper**.
- **Image:** users capture photos of the medication (package/label or pill). The image is processed using **Gemini + prompt-based interpretation**.

### **Reasoning and Decision**
- The system uses an **LLM-only approach** (no separate rule engine) with prompt design to produce a final safety verdict.

### **Outputs**
- The assistant returns one of three outcomes:
    - **Do not use**
    - **Consult a doctor**
    - **Safe for use**
- Each outcome includes a short, user-facing explanation based on the study’s questionnaire-driven criteria.

## **What I Built / Contributed**

- Built the full Android app end-to-end using **Kotlin + Jetpack Compose**.
- Implemented the multimodal pipeline (voice + image) and integrated the model calls.
- Designed and iterated prompts to make outputs consistent with the three-category verdict system.
- Conducted AI integration testing and refined the interaction flow based on lab feedback.

## **Tech Stack / Tools**

- Android (Kotlin, Jetpack Compose)
- Firebase (including **Firebase AI Logic** for on-device API calls)
- Gemini (prompt-based reasoning for image and decision)
- OpenAI Whisper (speech-to-text)
- Figma (flow prototyping)

## **Collaboration**

- Conducted as a lab study project with **Prof. Eun-Kyung Choe’s team (University of Maryland)**.
- I owned the full engineering scope: mobile implementation, AI integration, and prompt design.

## **Outcome**

A working multimodal prototype that produces a clear three-level safety verdict (“Do not use / Consult a doctor / Safe for use”) with explanations. The prototype was developed and iterated within a lab-study setting.

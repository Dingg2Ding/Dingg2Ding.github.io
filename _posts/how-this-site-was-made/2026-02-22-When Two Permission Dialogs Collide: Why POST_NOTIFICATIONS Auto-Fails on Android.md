---
title: When Two Permission Dialogs Collide - Why POST_NOTIFICATIONS Auto-Fails on Android
date: 2026-02-22 09:45:47 +07:00
modified: 2026-02-22 09:24:47 +07:00
tags: [Android, Permissions, Bug Fix, Mobile Development]
description: How one permission dialog can block another during app startup on Android, and how to fix it with serialized permission requests.
---


<hr>

#### Overview


## **When Two Permission Dialogs Collide: Why POST_NOTIFICATIONS Auto-Fails on Android**

I hit a confusing bug while requesting multiple Android runtime permissions during app startup.

### **The symptom**

- The **notification permission dialog never appears**
- POST_NOTIFICATIONS ends up **false immediately**, as if the user denied it
- If I **comment out the sensor permission request**, the notification dialog appears normally

So it looked like notifications and sensor permissions were “conflicting”.

### **The real cause**

Android permission requests are effectively **single-flight** at the UI level.

If you trigger two permission flows almost at the same time (even from different helpers), the system can:

- show only one dialog
- drop the other request
- return a default false/denied result
- leave your app thinking the user denied something they never saw

In my case, the sensor permission request was being kicked off without a strict sequence, and it **raced** with the notification permission request.

### **The fix**

**Serialize permission requests. One at a time, in one controlled flow.**

Instead of letting each feature request permissions independently during initialization, I moved all permission prompts into a single coroutine sequence:

- Notifications (POST_NOTIFICATIONS)
- Exact alarms (separate settings flow, but still within the same “startup permissions” sequence)
- Health Connect
- Samsung Health
- Then initialize notifications and load plugin data **only after** the permission flow completes

### **Key takeaway**

If your app requests multiple permissions at startup, do not fire them in parallel.

Build a **single permission pipeline** (a queue) and request permissions **strictly one-by-one**, otherwise you can get silent failures like:

- dialog not shown
- permission automatically denied
- inconsistent state that’s hard to reproduce
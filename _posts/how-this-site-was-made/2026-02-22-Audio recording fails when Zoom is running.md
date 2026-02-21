---
title: Audio recording fails when Zoom is running
date: 2025-03-02 09:45:47 +07:00
modified: 2025-03-02 09:24:47 +07:00
tags: [Android, Audio, Troubleshooting, Mobile Development]
description: Why audio recording fails when Zoom is running and how to detect or mitigate this issue in your app.
---


<hr>

#### Overview

## **Audio recording fails when Zoom is running**

- Zoom in VoIP mode often **keeps ownership of the microphone/audio routing even when muted**.
- So your app can **create a file**, but the mic input is blocked or routed away, resulting in **silent recordings**.
- Fix/mitigation: **tell users to leave/disconnect Zoom audio before recording**, or detect call/communication mode and **block + show a warning**.
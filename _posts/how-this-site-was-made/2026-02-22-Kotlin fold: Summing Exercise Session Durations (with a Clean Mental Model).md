---
title: Kotlin fold - Summing Exercise Session Durations (with a Clean Mental Model)
date: 2026-02-22 09:45:47 +07:00
modified: 2026-02-22 09:24:47 +07:00
tags: [Kotlin, Functional Programming, Data Processing, Tutorial]
description: Understanding Kotlin's fold() function through a practical example of summing exercise session durations.
---


<hr>

#### Overview

## **Kotlin fold: Summing Exercise Session Durations (with a Clean Mental Model)**

When you have a list of exercise sessions and want the **total time spent exercising**, Kotlin’s fold is a simple and expressive tool.

Here’s the pattern:

```
val totalDuration = exerciseAvg.fold(0L) { acc, exercise ->
    acc + (exercise.endTime.toEpochMilli() - exercise.startTime.toEpochMilli())
}
```

### **The setup**

Assume exerciseAvg is a List<ExerciseData>.

Each ExerciseData contains at least:

- startTime: Instant
- endTime: Instant

So each item represents one exercise session with a start and end timestamp.

### **What fold does**

fold(initial) { accumulator, element -> ... } iterates through the list and builds a single result by repeatedly updating an accumulator.

In this case:

- **Initial value**: 0L (a Long)
- **Accumulator (acc)**: the running total duration in milliseconds
- **Element (exercise)**: one session in the list

For each session, we compute:

```
exercise.endTime.toEpochMilli() - exercise.startTime.toEpocMilli()
```

That gives the session duration in **milliseconds**. Then we add it to acc.

### **What you get**

totalDuration becomes the sum of all session durations in milliseconds.

Example:

- Session A: 30 minutes = 1,800,000 ms
- Session B: 15 minutes = 900,000 ms
- Total: **2,700,000L ms**

### **A small improvement: readability + safety**

If you want it to read more clearly (and avoid repeating toEpochMilli() twice), you can extract a helper:

```
fun ExerciseData.durationMillis(): Long =
    endTime.toEpochMilli() - startTime.toEpochMilli()

val totalDuration = exerciseAvg.fold(0L) { acc, e -> acc + e.durationMillis() }
```

If there’s any chance endTime can be earlier than startTime (bad data, timezone conversions, etc.), clamp it:

```
fun ExerciseData.durationMillis(): Long =
    (endTime.toEpochMilli() - startTime.toEpochMilli()).coerceAtLeast(0L)
```

---

That’s basically fold in one use case: **take many items, compute a per-item value, and accumulate them into one final result**.
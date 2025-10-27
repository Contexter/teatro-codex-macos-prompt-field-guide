# Part 12 — Reflective Playback & Semantic Recording

[Home](../README.md) · [Summary](../SUMMARY.md) · [← Part 11](part-11.md) · [Part 13 →](part-13.md)

## Contents
- [Overview](#overview)
- [Key Ideas](#key-ideas)
- [Implementation Notes](#implementation-notes)
- [Try This](#try-this)
- [Navigation](#navigation)

## Overview

**Recording modes:** Chronicle · Condensed · Analytic · Affective

**Playback:** `replay("Act I", @speed=1.0)` · `compare("v2","v3")` · `merge("v2","v3")`

**Metrics:** Δ Tempo · Δ Light · Δ Mood · Resonance Index

## Key Ideas
- Record artifacts in modes (chronicle/condensed/analytic/affective).
- Replay, compare, and merge to evaluate design trajectories.
- Track deltas and resonance to guide learning and iteration.

Examples: [Live Direction](../examples/Live-Direction.score.teatro) (freeze/restore), [Contrast Montage](../examples/Contrast-Montage.score.teatro) (memory), [Still Reflection](../examples/Still-Reflection.score.teatro) (✶).

## Implementation Notes
- What to record: frames (F1…Fn), gestures, parameters, commentary, and metrics. Prefer a compact JSON alongside `.teatro` for diff‑friendly review.
- Naming: version with intent and date (e.g., `search-focus_v3_2025-10-27`). Use tags for anchors (tempo/light/camera/montage) to filter later.
- Storage: simple file‑based logs are fine for local work; rotate by week. For sensitive data, store only descriptors, not actual content.
- Compare/Merge: use structural diffs on gestures first, then evaluate expressive deltas (tempo/light). Keep raw takes; commit chosen cuts as a new score.
- Playback: support speed (`@speed`), loop (`↺`), and A/B toggles. Annotate resonance moments to inform later synthesis.

## Try This
- Record two variants; replay and compare to identify deltas and resonance.
- Merge aspects of two recordings and annotate what improved.
- Define a simple metric set and log observations per frame.

**Archiving:** `archive("Name", tags=[…], format=.teatro)`
## Navigation

---
[← Part 11](part-11.md) · [Home](../README.md) · [Part 13 →](part-13.md)

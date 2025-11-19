# Teatro Field Guide (Codex · FountainKit · Instruments)

**Version:** 1.0 • **Date:** 2025-11-19

This repository packages the full **Teatro prompt language** we developed to converse with Codex about **GUI and instrument creation** — a bilingual system that bridges **platform‑level technical terms** (SwiftUI, SDL, FountainKit) and **stage/cinematic semantics**.

---

## What’s inside

- `parts/` — Sixteen chapters (1–16) as focused guides.
- `quick-reference/` — A concise one-pager for daily use.
- `examples/` — Example Teatro score(s) to start from.
- `parts/instruments-pipeline.md` — How Teatro scenes become FountainKit instruments.
- `GLOSSARY.md` — Core terms and symbols at a glance.
- `TROUBLESHOOTING.md` — Common pitfalls and quick remedies.
- `CODE-POINTERS.md` — Curated Apple docs and APIs.
- `openapi.yaml` — One-file OpenAPI spec for the Teatro language (schemas + ops).
  - Browse: `swagger.html` (Swagger UI)
- `SUMMARY.md` — Table of contents with links.
- This `README.md` — How to use the material.

---

## How to use

1. Start with **[Part 15 – Integrative Summary](parts/part-15.md)** to see the whole map of the Teatro language.
2. Keep **[Teatro Quick-Reference Card](quick-reference/teatro-quick-reference.md)** open while working.
3. When exploring expressive design, read **[Part 8 – Stage Dynamics](parts/part-08.md)** and **[Part 10 – Expressive Operators](parts/part-10.md)**.
4. When shaping narrative/flow, use **[Part 13 – Cinematography](parts/part-13.md)** and **[Part 14 – Montage](parts/part-14.md)**.
5. When you want to turn a Teatro scene into a **FountainKit instrument**, read **[Instruments & Pipelines (FountainKit)](parts/instruments-pipeline.md)** for the outside‑in story.
6. To learn efficiently, follow **[Part 16 – Learnability Framework](parts/part-16.md)**.
7. When in doubt about a symbol or term, check the **[Glossary](GLOSSARY.md)**.

---

## Choose Your Path

- Builder Track
  - Start: [Part 01 – macOS GUI Lingo](parts/part-01.md) → [Part 02](parts/part-02.md)
  - Compose: [Part 09 – Score Format](parts/part-09.md)
  - Daily use: [Quick-Reference](quick-reference/teatro-quick-reference.md)
  - Big picture: [Part 15 – Integrative Summary](parts/part-15.md)
  - Instruments in practice: [Instruments & Pipelines (FountainKit)](parts/instruments-pipeline.md)

- Expressive Track
  - Dynamics: [Part 08 – Stage Dynamics](parts/part-08.md)
  - Operators: [Part 10 – Expressive Operators](parts/part-10.md)
  - Cinematics: [Part 13 – Cinematography](parts/part-13.md)
  - Montage: [Part 14 – Narrative Montage](parts/part-14.md)

- Conductor Track
  - Protocol: [Part 06 – Conversational Protocol](parts/part-06.md)
  - Ensemble: [Part 11 – Conductor’s Layer](parts/part-11.md)
  - Reflection: [Part 12 – Reflective Playback](parts/part-12.md)
  - Synthesis: [Part 15 – Integrative Summary](parts/part-15.md)

> Minimal mantra: **Stage · Light · Tempo · Camera · Montage**

---

## Repository layout

```
teatro-codex-macos-prompt-field-guide/
├── README.md
├── SUMMARY.md
├── parts/
│   ├── part-01.md … part-16.md
├── quick-reference/
│   └── teatro-quick-reference.md
└── examples/
    └── Still-Reflection.score.teatro
```

---

## License

This content is provided for your internal use. If you plan to publish, add your preferred license file at the repo root (e.g., MIT, Apache-2.0).

---

## Publishing

GitHub Pages (simple, no build):
- Already added: `_config.yml` with a minimal theme and `index.md` homepage.
- Enable in GitHub → Settings → Pages:
  - Source: “Deploy from a branch”
  - Branch: `main` · Folder: `/` (root)
- Your site URL becomes: `https://Contexter.github.io/teatro-codex-macos-prompt-field-guide/`

Notes
- The header includes quick links to Summary, Glossary, Troubleshooting, Code Pointers, Quick‑Reference, and Examples.
- All existing Markdown files render as pages; links remain relative.
- To customize the look, edit `_config.yml` (theme, header_pages) or add CSS via `assets`.

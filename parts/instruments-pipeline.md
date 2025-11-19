# Instruments & Pipelines — From Teatro Scene to FountainKit Instrument

[Home](../README.md) · [Summary](../SUMMARY.md)

This note describes how the Teatro language you use in this field guide relates to **FountainKit instruments** – concrete, testable surfaces in the Fountain Coach codebase.

It is written from the outside‑in: start with a scene in your head, then see how it becomes an “instrument” that apps, tools and tests can all talk to.

---

## 1. Start with a scene, not a schema

When you think about creating something new, you don’t start with YAML. You start with a **scene**:

- a surface you can picture (“a single infinite canvas with a grid”),
- a small set of **knobs** that matter (“zoom”, “grid spacing”, “node positions”),
- and a few **invariants** you care about (“follow‑finger pan; anchor‑stable zoom; grid spacing tracks zoom”).

In Teatro terms, this lives in the mix of structural / expressive / cinematic planes you see in the other parts of this guide. You might already sketch it as a short score:

> ▶ Act I — Infinity Canvas  
> @camera(WS → CU)  
> ♩ pan follows finger, zoom anchors grid  
> ↑ light on grid intersections  
> commentary: The canvas is the whole window; no panes.

At this point, you’ve created an **instrument idea**. Nothing in this step forces you to think about OpenAPI, facts, or host wiring. You are just naming the surface, its controls, and the invariants you want to keep true.

FountainKit’s job is to turn this idea into a **first‑class instrument**: something whose behaviour is captured once and then enforced in code, tools and tests.

---

## 2. Give the instrument a name and a role

Every instrument needs two stable names:

- an **app id** – the name you use when you talk about this app or surface as a whole (`"infinity"`, `"llm-chat"`, `"patchbay-app"`), and
- an **agent id** – the name other agents use when they address it (`"fountain.coach/agent/infinity/service"`).

Think of the app id as the name on the score, and the agent id as the name on the door when other agents come knocking.

In practice, these two names become the thread that ties everything together:

- the prompt and facts stored in FountainStore,
- the OpenAPI spec that describes HTTP access,
- the facts document that MIDI and LLM hosts read,
- and the tests that assert the instrument’s invariants.

You don’t have to mint these ids alone; the FountainKit side can propose them, but conceptually this is the moment the instrument “enters the world”.

---

## 3. Describe behaviour once, in your own language

Next you write a **brief** for the instrument. This is the human‑level description that matters most:

- What does the surface look like? (canvas only, three‑pane layout, inspector + timeline…)
- What does it do? (pan, zoom, play, scrub, route, annotate…)
- Which properties are meaningful? (`canvas.zoom`, `grid.minor`, `volume.db`, `selection.range`…)
- Which invariants must hold? (zoom bounds, grid spacing, no drift under repeated pan/zoom, timing tolerance…)
- What would you test to be confident it behaves?

This brief is the bridge between Teatro and FountainKit. On the Teatro side, it can be a score, a paragraph, or both. On the FountainKit side, an agent turns it into a more structured **instrument contract** that captures:

- host & surface (“SDLKit window with canvas‑only content”; “macOS window with three panes”),
- the cores it relies on (`Canvas2D`, `InfinityScene`, `MetalViewKitRuntime`, …),
- the list of externally visible properties with their ranges,
- the invariants by name,
- and the test module + test classes that should enforce them.

You don’t have to fill that structure by hand; it’s the agent’s job to translate your brief into that contract. The important part is that your description appears *once*, not scattered across code comments and ad‑hoc documents.

---

## 4. From contract to living instrument

From here, FountainKit treats the contract as the **single source of truth** and derives the technical artefacts it needs:

- A **Teatro prompt** for humans and LLMs:  
  a text page in FountainStore (`prompt:<appId>:teatro`) that describes the surface, host, properties and invariants in the style used throughout this guide.

- A **facts document** for hosts and tools:  
  a compact JSON document in FountainStore (`facts:agent:<agentId>`) that lists the properties, their ranges, and how they map onto HTTP operations derived from the curated OpenAPI spec.

- A **test anchor** for CI and robots:  
  an expectation that the named test module and suites exist and cover the promised invariants.

Small seeders in the FountainKit repo handle the mechanics of writing these into the store. Tools Factory and its companions handle generating facts from OpenAPI. Gateway and MIDI hosts read the facts back and treat the instrument as a first‑class agent they can talk to.

From your seat, you should not be worrying about which script to call. You should be checking that:

- the prompt reads like the instrument you wanted,
- the list of properties and invariants matches your brief,
- and the tests you care about actually exist and pass.

The OpenAPI, facts and seeding steps exist to keep those three views (prompt, runtime, tests) in sync.

---

## 5. Creative flow vs. implementation details

It’s easy, looking at the FountainKit repository, to feel like “creating an instrument” means:

> “Write OpenAPI, hand‑craft prompt YAML, run a pile of generators.”

That’s not the intended experience.

In the **creative loop**, your job is:

1. Sketch the instrument as a Teatro scene (brief + score).  
2. Agree on its app id / agent id and its visible properties.  
3. Review the prompt and facts that the agent generates from that brief.  
4. Iterate on behaviour and tests until it feels right.

The **pipeline and factories** exist so you *don’t* have to think about:

- how facts are normalized or where exactly they’re stored,
- how OpenAPI is wired into Tools Factory,
- how hosts discover and map properties back to HTTP.

They’re there to make the prompts in this guide actionable: to let an instrument that is described in Teatro terms become something a running system can discover, call, and test.

If you keep that separation clear—**you own the brief**, the agent owns the contracts and plumbing—the instruments creation pipeline stops feeling like bureaucracy and starts feeling like what it is: a reliable bridge between the scenes you sketch in Teatro and the instruments that live in FountainKit.


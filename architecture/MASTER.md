# VIGILIA — Master Architecture Document

> **Status:** Living document. Sections marked `[EXPAND]` are placeholders for deeper detail as the project develops.
> **Last updated:** 2026-06-26
> **Author:** Ron Spoelstra

---

## 1. Vision

Europe's democratic infrastructure is under sustained, coordinated attack. Not through armies or sanctions — through narrative. Russia's influence networks, operating at millions of accounts across dozens of countries and languages, systematically seed distrust, amplify division, and bridge fringe content into mainstream political discourse. The goal is not to convince; it is to exhaust, confuse, and fragment.

This project does not attempt to silence those networks. It attempts to **balance the playing field** — to ensure that democratic, pro-European voices operate at comparable scale, speed, and reach. Not through manufactured consensus or bot farms, but through **authentic presence at scale**: real people, real movements, real editorial voice — amplified by AI pipelines and federated across a continent.

The name is Vigilia. It means watchfulness.

---

## 2. The Threat

### 2.1 How Russian Narrative Networks Operate

The attack follows a reproducible four-stage cycle:

```
Stage 1 — SEED
Fringe channels, fake local infrastructure, Telegram dark channels.
Content is extreme, untraceable, deniable.

Stage 2 — AMPLIFY
Bot networks and coordinated accounts create false consensus.
Engagement metrics are manufactured to signal "this is what people think."

Stage 3 — BRIDGE
Political influencers, sympathetic journalists, useful idiots pick it up.
The source chain is broken — the narrative travels without its origin.

Stage 4 — MAINSTREAM JUMP
A politician cites it. A newspaper covers it. It is now "the news."
Intervention at this stage costs 10x more than at Stage 1.
```

**Scale (as of 2026):** Robbert van der Noordaa's research (to be presented September 2026, Brussels) documents Russian influence networks operating at millions of accounts across multiple tiers and languages simultaneously. His assessment: no one is yet sufficiently aware of the scale and urgency. Democracy is in genuine danger.

### 2.2 Why Existing Counter-Measures Fall Short

- **Fact-checking** operates at Stage 4. Too late, too slow, too reactive.
- **Platform moderation** is asymmetric: networks reconstitute faster than they are removed.
- **EU institutional responses** are bureaucratic, underfunded, and unable to match the speed of adversarial operations.
- **Academic research** documents the problem but does not produce counter-presence.

### 2.3 The NAFO Precedent

The NAFO (North Atlantic Fellas Organization) movement demonstrated that **organic, decentralized, humor-driven grassroots counter-presence** can meaningfully disrupt coordinated inauthentic behavior — not by out-spending it, but by out-persisting it. Thousands of individual accounts, no central command, unified identity. This model scales.

`[EXPAND]` — detailed NAFO case study, lessons for Vigilia's grassroots layer

---

## 3. System Architecture

### 3.1 The Full Loop

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│   RUSSIA / FAR-RIGHT SEED NETWORKS                             │
│   (millions of accounts, Stage 1-2 operations)                 │
│                        │                                        │
│                        ▼                                        │
│   ┌─────────────────────────────────────────┐                  │
│   │  P6 — NARRATIVE DETECTION               │                  │
│   │  Content-blind pattern scoring          │                  │
│   │  Catches at Stage 1-2, not Stage 4      │                  │
│   └──────────────────┬──────────────────────┘                  │
│                      │                                          │
│                      ▼                                          │
│   ┌─────────────────────────────────────────┐                  │
│   │  P7 — VERIFICATION & LIBRARY            │                  │
│   │  Grounded dossiers, sourced, RAG-indexed│                  │
│   │  Feeds P6 confidence ladder             │                  │
│   └──────────────────┬──────────────────────┘                  │
│                      │                                          │
│                      ▼  (human analyst is the gate)            │
│   ┌─────────────────────────────────────────┐                  │
│   │  P1–P5 — EDITORIAL PIPELINES            │                  │
│   │  Long-form, fast news, investigations   │                  │
│   │  AI-assisted, human-directed            │                  │
│   └──────────────────┬──────────────────────┘                  │
│                      │                                          │
│                      ▼                                          │
│   ┌─────────────────────────────────────────┐                  │
│   │  VIGILIA FEDERATION                     │                  │
│   │  Country nodes + regional hubs          │                  │
│   │  Same content, local voice              │                  │
│   └──────────────────┬──────────────────────┘                  │
│                      │                                          │
│                      ▼                                          │
│   ┌─────────────────────────────────────────┐                  │
│   │  GRASSROOTS MOVEMENTS & INSTITUTIONS    │                  │
│   │  Real people, real parties, real reach  │                  │
│   │  The authenticity layer                 │                  │
│   └──────────────────┬──────────────────────┘                  │
│                      │                                          │
│                      ▼  (upstream intelligence)                 │
│   ┌─────────────────────────────────────────┐                  │
│   │  LIVE EUROPA MAP                        │                  │
│   │  Continental sentiment sensor grid      │                  │
│   │  Feeds back into P6 — the loop closes   │                  │
│   └─────────────────────────────────────────┘                  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 3.2 The Separation Principle

**P6 does not trigger editorial. Editorial does not feed P6.**

The human analyst is the only bridge. This is not a technical limitation — it is a governance decision. It is what separates Vigilia from the networks it monitors: Vigilia observes, never instigates. This principle is load-bearing and non-negotiable.

---

## 4. Components

### 4.1 P6 — Narrative Intelligence (Detection Layer)

**Purpose:** Detect coordinated inauthentic narrative patterns at Stage 1-2, before mainstream jump.

**How it works:**
- Ingests continuously from tiered sources: seedbed → fringe → political → mainstream
- Sources: RSS feeds, Telegram public channels, Bluesky, watched accounts
- Pipeline: Monitor → Extract → Cluster → Score → Output
- Scoring is **content-blind**: measures velocity, coordination, escalation — not political position
- Confidence ladder (4 gates): cheap pattern detection → quick check → correlation → deep research → human review
- Output: daily digest, risk alerts, cluster briefings, dashboard

**Current status:** Operational. Phase 1 (Netherlands/Belgium). 877 raw items, 62 narratives, 32 active clusters. Dashboard live.

**Scaling path:** Expand source coverage per country node. Each new Vigilia node adds its own P6 instance, regional sources, local language processing.

`[EXPAND]` — full P6 technical spec, scoring formulas, legal/ethical framework, source registry

### 4.2 P7 — Intelligence Research (Verification Layer)

**Purpose:** Ground-truth verification of P6 findings. Prevent hallucinated "reference facts" from poisoning the confidence ladder.

**How it works:**
- Human-led investigation pipeline (fork of P5)
- Output: sourced dossiers (not articles) — real URLs, real dates, web-verified
- RAG-indexed and embedded for library lookup
- Bidirectional bridge to P6: validates clusters or reveals blind spots

**Current status:** Design phase. Not yet integrated with P6.

`[EXPAND]` — P7 pipeline spec, library architecture, RAG embedding model, P6 integration bridge

### 4.3 P1–P5 — Editorial Pipelines (Response Layer)

**Purpose:** Autonomous, AI-assisted editorial production. Authentic, sourced, scaled.

| Pipeline | Description | Speed | Status |
|----------|-------------|-------|--------|
| P1 | Long-form articles, full research cycle | Hours | Production |
| P2 | P1 rewrites for younger audience | Hours | Production |
| P3 | Current affairs, same depth as P1 | Hours | Active |
| P4 | Fast news, ultra-short cycle | Minutes | Active |
| P5 | Original investigations, human-in-loop | Days | Active |

**AI leverage:** One human director + pipeline = output of 8-10 editorial staff. This is the economics that makes continental scale possible.

**Published to:** GitHub Pages (static sites), Bluesky, Twitter/X. Each node publishes to its own site.

`[EXPAND]` — pipeline specs per P, model configuration, publishing architecture

### 4.4 Vigilia Federation (The Network Layer)

**Purpose:** Replicate editorial output across 27 EU member states and regional hubs. Same message, local voice, local authenticity.

**Federation model:**
```
Brussels / Belgium — Central node (pilot, live)
    ├── Netherlands node
    ├── Germany node (→ regional: North, South, East, West)
    ├── France node (→ regional: ~6 hubs)
    ├── Poland node
    ├── [all 27 EU states]
    └── ...
```

**Each node:**
- Runs its own instance of patria-package (white-label editorial platform)
- Owns its own compute, data, and publishing targets — no central cloud
- Has its own editorial voice, language, local sources
- Contributes upstream intelligence to the continental sensor grid

**Tech foundation:** `patria-package` — a self-contained Docker image. Drop in `instance.json` + `.env`, run Docker, publish. A node can be a desktop machine. A laptop. A small VPS. No enterprise infrastructure required.

**Demo target (September 2026):**
- Node 1: desktop (central / Belgium)
- Node 2: laptop (Netherlands)
- P6 live on Node 1, detecting narratives
- Upstream intelligence visible on the Live Europa Map

`[EXPAND]` — node deployment guide, federation protocol, upstream data format, inter-node communication

### 4.5 Grassroots & Institutional Layer

**Purpose:** The authenticity moat. Real people, real movements, real credibility. What Russia cannot manufacture.

**Current landscape:**
- **Astra Europa** (May 2026): pan-European, federalist, tech-heavy founding team. Clean on red lines. Multiple Dutch founders. `[PRIORITY PARTNER]`
- **Ave Europa** (July 2025): 15k+ supporters. March 2026 incident (conditional engagement, monitoring required).
- **NXT4EU / Odin's platform**: 26k+ X followers, integrated with Astra infrastructure.
- **NAFO model**: decentralized, organic, humor-driven — template for grassroots Vigilia chapters.

**The red line:** Any partner whose editorial position drifts toward identitarian or far-right framing disqualifies automatically. Vigilia's value is authenticity. Amplifying bad actors destroys the product.

`[EXPAND]` — partner evaluation framework, red line criteria, onboarding process, NAFO chapter model

### 4.6 Live Europa Map (Upstream Intelligence)

**Purpose:** A continental political sentiment sensor grid. Not just broadcast — strategic intelligence.

**What it tracks:**
- Sentiment shifts per region over time (hot → cold, subject drift)
- Which narratives are gaining or losing ground, and where
- Cross-border pattern detection (same narrative appearing in multiple countries simultaneously)
- Influence from external actors (Russia, China, US) at regional level

**How it works:** Every piece of content published by every Vigilia node flows back as structured data. P6 instances share cluster data (federated, not centralized). The map is a live visualization of what Europe is thinking, worrying about, and being told to think.

**This does not exist publicly anywhere.** It is the intelligence crown jewel of the system.

`[EXPAND]` — data schema, visualization spec, privacy/GDPR framework, federation protocol

---

## 5. What Makes This Different

| Approach | Problem |
|----------|---------|
| Fact-checking | Operates at Stage 4. Too late. |
| Platform moderation | Networks reconstitute faster than removed. |
| EU institutions | Too slow, too bureaucratic, too visible. |
| Counter-propaganda | Mirrors the adversary's methods. Destroys legitimacy. |
| **Vigilia** | **Detects early. Responds authentically. Scales through federation. Learns continuously.** |

**The asymmetry:** Russia's strength is scale. Russia's weakness is inauthenticity. Vigilia's entire architecture exploits that weakness: real people, real editorial voice, real movements — AI handles the throughput.

**Persistence is the weapon.** Russia has operated for 10-15 years. Vigilia is designed for the same horizon: decentralized, sovereign nodes, no central point of failure, self-improving through the upstream loop.

---

## 6. Strategic Position & Partnerships

### 6.1 Current State

- **Patria** (pilot node): live in production. P1, P2, P3, P4 editorial pipelines running. P6 detection operational. P7 in design.
- **Interested party (pan-European):** aware of Patria. Not yet aware of federated network vision. Conversation pending.
- **Vigilia pitch:** built and documented. Not yet presented to federation candidates.

### 6.2 The September Window

Robbert van der Noordaa presents Russian network research at a closed convention in Brussels, September 2026. His finding: networks operating in the millions, across multiple levels. His assessment: no one is sufficiently aware of the scale or urgency. Democracy is in genuine danger.

This presentation creates a moment. When urgency lands at political, entrepreneurial, and institutional level simultaneously — that is when funding, recruitment, and partnership conversations become possible. Vigilia needs to be ready before that moment, not after it.

**Target for September 2026:**
- This document: complete and detailed
- Research library: mapped (public evidence, incidents, academic papers)
- Pitch: built (Vigilia vision, P6 demo, federation model)
- Working demo: two live nodes (desktop + laptop, Belgium + Netherlands)
- Visual assets: images, video, presentation materials

### 6.3 Funding & Growth Path

`[EXPAND]` — funding strategy, grant landscape (EU Democracy funds, civil society), private investment, partner revenue model

### 6.4 Partnership Criteria

- Pan-European orientation (non-negotiable)
- No identitarian or far-right ties (non-negotiable, monitored continuously)
- Genuine editorial independence (required for authenticity)
- Technical capacity or willingness to build it (preferred)

---

## 7. Research Library

`[EXPAND]` — this section will be built out as a mapped reference of publicly available evidence:

- Russian influence network documentation (academic, journalistic, intelligence)
- Specific incidents: Wagner/Africa migration narrative, AfD/FPÖ infiltration patterns, Telegram seeding operations
- NAFO case study
- EU Democracy reports
- Robbert van der Noordaa research (post-September)
- Academic literature on narrative spread, prebunking, coordinated inauthenticity

---

## 8. Build Specifications

`[EXPAND]` — technical build specs will be detailed per component:

- P6 scaling: multi-language, multi-country source expansion
- P7: pipeline spec, library architecture, P6 bridge
- Federation protocol: node deployment, upstream data format, inter-node sync
- Live Europa Map: data schema, visualization, GDPR framework
- Demo setup: two-node federation (desktop + laptop), step-by-step

---

## 9. Open Questions

Items being actively thought through:

- **Inter-node protocol:** How do nodes share upstream intelligence without a central server? (Options: federated pub/sub, shared read-only data endpoints, periodic sync)
- **P6 source expansion:** Path from 31 RSS + 12 Telegram channels to continental coverage
- **Android / mobile:** Post-September scope. Mobile-responsive web interface serves the demo.
- **Institutional engagement:** EU Parliament, European Commission contacts for intelligence output
- **Legal entity:** What structure hosts Vigilia? Foundation, NGO, commercial entity, or hybrid?

---

## 10. Glossary

| Term | Meaning |
|------|---------|
| Node | A single Vigilia deployment (one country or region) |
| Central node | The pilot node (Belgium/Brussels). First live. Template for all others. |
| Country node | A per-country deployment. Owns its own data, voice, compute. |
| P6 | Narrative intelligence: detection, scoring, alerting |
| P7 | Intelligence research: verification, dossiers, library |
| P1-P5 | Editorial pipelines: long-form, youth, current affairs, fast news, investigation |
| patria-package | The white-label Docker image. One deployment = one node. |
| Upstream intelligence | Content published by nodes, flowing back as structured data for the Live Europa Map |
| Red line | Any partner drift toward identitarian/far-right framing. Automatic disqualification. |
| Confidence ladder | P6's 4-gate funnel from pattern detection to human review |
| The separation principle | P6 never triggers editorial. Editorial never feeds P6. Human is the only bridge. |

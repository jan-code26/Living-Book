# Agents League Hackathon — Reference & Project Plan

*Working reference document. Last updated: June 4, 2026.*
*Status: track chosen (Creative Apps), IQ layer chosen (Foundry IQ), project concept locked ("Living Book"). Open decisions tracked at the end.*

---

## Part 1 — The Hackathon

### What it is

Agents League (@ AISF 2026) is a 10-day AI developer competition running **June 4–14, 2026**, combining live coding battles on Microsoft Reactor, asynchronous "build at your own pace" challenges, and a Discord community. It's open to all skill levels, and you can enter one track or all three. The goal is to build innovative AI agents and get feedback from Microsoft product teams.

### The three tracks

Each track is associated with a primary build tool, but the only hard technical requirement common to all of them is integrating a Microsoft IQ layer (see below).

| Track | Theme | Primary build tool |
|---|---|---|
| 🎨 Creative Apps | Imaginative, novel applications of any kind (web, CLI, mobile, desktop, games, etc.) | GitHub Copilot |
| 🧠 Reasoning Agents | Multi-step reasoning / problem-solving agents | Microsoft Foundry |
| 💼 Enterprise Agents | Agents for the workplace | Microsoft 365 Copilot |

**Chosen track: 🎨 Creative Apps.** It is the most flexible (any application type is welcome), it explicitly welcomes mobile apps, and it fits the goal of building something new and fun rather than a reskin of prior work.

### The mandatory requirement: a Microsoft IQ layer

Every submission, in any track, must integrate at least one of Microsoft's three "IQ" intelligence layers. These are distinct workloads, each giving agents access to a different slice of organizational context. They can be used alone or combined.

| IQ layer | What it is | Best for |
|---|---|---|
| **Foundry IQ** | A managed *knowledge* layer for enterprise data. You build a multi-source knowledge base; its agentic-retrieval engine plans queries, runs parallel searches across sources, reranks, and returns grounded answers **with citations**. Built on Azure AI Search. Supported sources include Azure Blob Storage, SharePoint, OneLake, and **public web data**. | Grounding an agent in documents/text so answers are accurate and cited rather than hallucinated. |
| **Work IQ** | The contextual intelligence layer behind Microsoft 365 Copilot. Builds understanding from emails, meetings, chats, and documents — how an organization actually works. | Agents that need work context: people, relationships, collaboration signals. |
| **Fabric IQ** | A semantic intelligence layer for Microsoft Fabric. Uses ontologies and knowledge graphs to give business meaning to enterprise data in OneLake / Power BI. | Agents that reason over business analytics and structured data concepts. |

**Chosen IQ layer: Foundry IQ.** It is the most accessible for a solo developer (a working knowledge-base + agent can be wired up programmatically in a small amount of code), it supports public web data and document sources, and — most importantly — its job (grounded, cited retrieval over a body of text) is the exact technical centerpiece of the chosen project.

How Foundry IQ is consumed: a **knowledge base** references one or more **knowledge sources** and is queried through an **agentic retrieval** pipeline. You can call it from Foundry Agent Service, the Microsoft Agent Framework, or any custom app via the Azure AI Search knowledge base APIs. Azure AI Search provides the underlying indexing and retrieval. Some features are GA and some are in preview depending on the Search Service REST API version.

### Creative Apps track — core requirements

1. **GitHub Copilot usage (required).** The project must show meaningful use of GitHub Copilot during development — accelerating code, debugging/explaining via Copilot Chat — and the README should document how Copilot helped. (Copilot supports multiple underlying models, including GPT, Claude, and Gemini; model choice is up to you.)
2. **Microsoft IQ integration (required).** At least one IQ layer — here, Foundry IQ.
3. **A creative application (required).** A unique/novel concept that provides value, entertainment, or utility, with thoughtful UX.

### Submission requirements

Register to activate participant status, then submit through the event portal by the deadline. Each submission needs a **public repository with a README** and a **demo video**. Before submitting, read the Disclaimer and Code of Conduct.

- **No confidential information** in the public repo: no API keys/credentials, no customer data or PII, no proprietary/NDA material. Use environment variables and a `.gitignore` for secrets, and use only demo/public data.

### Judging rubric

| Criterion | Weight |
|---|---|
| Accuracy & Relevance (meets challenge requirements) | 20% |
| Reasoning & Multi-step Thinking (clear problem-solving) | 20% |
| Reliability & Safety (solid patterns, avoids pitfalls) | 20% |
| Creativity & Originality (novel idea or execution) | 15% |
| User Experience & Presentation (clear, polished, demoable) | 15% |
| Community vote (Discord poll) | 10% |

Note the heaviest weights: reasoning, reliability, and accuracy together account for 60%. Originality is only 15%, which is why "a similar product exists" is not disqualifying — execution and technical angle matter more.

### Prizes

Everyone who registers and submits a project receives a digital badge. Category winners receive additional prizes (specific prize details were not included in the brief).

### Key dates

| Date | Event |
|---|---|
| June 4, 2026 | Competition opens (build window begins) |
| Tue June 9, 9 AM PT | Live battle — 🎨 Creative Apps (Microsoft Reactor) |
| Wed June 10, 9 AM PT | Live battle — 🧠 Reasoning Agents |
| Thu June 11, 9 AM PT | Live battle — 💼 Enterprise Agents |
| **June 14, 2026** | **Submission deadline** |

### Useful links

- Disclaimer: https://aka.ms/AgentsLeague_Disclaimer
- Code of Conduct: https://aka.ms/AgentsLeagueCodeofConduct
- Security Policy: https://aka.ms/AgentsLeagueSecurity
- Discord (help, progress, community vote): https://aka.ms/agentsleague/discord
- Microsoft IQ Series (deep dives on the three IQ layers): https://aka.ms/iq-series
- Live battles / replays: https://aka.ms/agentsleague/aisf/battles
- Foundry Developer Forum (build issues): https://aka.ms/foundry/forum
- Rules / FAQ: https://aka.ms/AgentsLeagueFAQ

---

## Part 2 — The Project: "Living Book"

*Working title — name is an open decision.*

### One-line pitch

An anime-styled, immersive reader that turns any public-domain book into a dramatized, interactive reading experience — where everything stays faithful to the actual text because it's grounded in the book via Foundry IQ.

### The problem

Great classic literature is free and abundant (Project Gutenberg has tens of thousands of titles), but for a lot of people long-form classic prose reads as a wall of text and is a slog to get through. People bounce off books they'd otherwise love. Existing AI manga/comic tools mostly help you *create your own* comic from a prompt or a selfie; they don't make *existing books* engaging to *read*.

### The concept

Pick any public-domain book. The app ingests it and presents it as an immersive, anime-flavored experience rather than raw chapters:

- The story is retold **scene by scene in punchy, dramatized light-novel style** — the way an anime adaptation *feels* — instead of dense period prose.
- An **anime-styled UI** with **character cards** (name + portrait) so it looks like the thing the concept promises.
- A **"talk to the story" mode**: ask "who is this again?", "what just happened?", "replay that scene from her point of view" — and every answer is **grounded in the actual book text via Foundry IQ**, so it stays faithful and never invents plot. Claims are traceable to source passages.
- **Optional flourish:** one anime "key visual" per chapter for a splash screen — a *few* images, not hundreds, so image consistency never becomes the bottleneck.

### Important framing: a library, not one book

The engine is **general**. Nothing is hardcoded to a single title: the user picks any Gutenberg book, the app fetches → chunks → indexes it into a Foundry IQ knowledge base, and generates the experience on the fly.

For a 10-day build, the strategy is: **the system is general, but the demo showcases one or two books deeply.** The ingestion pipeline costs the same whether it handles one book or a thousand — it's parameterized by which book it points at. What takes time is *polish per book* (retelling quality, character cards, a hero image or two). So pick one standout, visually recognizable title (e.g., *Alice in Wonderland* or *Dracula*), make that one gorgeous for the demo video, and include an "add another book" path to prove it generalizes.

### Why this is the right project

**Fit with the hackathon.** The book itself becomes the Foundry IQ knowledge source, so grounding the experience in it is exactly what Foundry IQ is built for — this is the strongest possible IQ fit, not a bolted-on integration. It lives naturally in the Creative Apps track and satisfies all three track requirements.

**Novelty.** Text-to-manga generation is a saturated category (Dashtoon, ARTAI, Anifusion, INKY, AniFun and others already ship it, and they compete on character consistency). "Read the classics as an immersive, faithful, interactive experience" is a fresher angle than yet another from-scratch manga generator, and it sidesteps the crowded, hard, off-spec image-generation arms race.

**Buildability.** The core is text in, text out: the book is the corpus (zero dataset to assemble) and there's no panel-by-panel image-consistency nightmare. This is the easiest-to-build of the strong creative ideas.

**Fit with background.** It plays to existing full-stack and SwiftUI experience (a client over an agent backend), and the grounded-retrieval / "don't trust the model, verify against the source" core overlaps directly with prior agentic-pipeline and anti-hallucination work — which is also exactly the reasoning + reliability the rubric rewards most.

### Architecture (high level)

```
Client (web app  OR  thin SwiftUI iOS app)
        │
        ▼
Agent backend  ── orchestrates: ingest, scene retelling, "talk to the story" Q&A
        │
        ▼
Foundry IQ knowledge base  (Azure AI Search index over the book's text)
        │
        └── (optional) image model for a few anime "key visuals" per chapter
```

- **Ingestion:** fetch a Gutenberg book → chunk → index into a Foundry IQ knowledge source. Repeatable for any title.
- **Retelling + Q&A:** the agent uses agentic retrieval (extractive output, so it reasons over raw source content) to dramatize scenes and answer questions, always citing back to the text.
- **Built with GitHub Copilot** throughout (track requirement) — capture where it helped for the README.

### What to expect (honest risks and how to handle them)

- **The grounding pipeline is the real project.** Ingest → chunk → index → retrieve faithfully is the core; everything else is presentation. **De-risk it first** by proving faithful grounded Q&A on a single book before building any UI.
- **First-time Azure + Foundry IQ setup is a real chunk of time** (provisioning a search service, a Foundry project, a model deployment, and auth). Budget ~2–3 days and don't underestimate it.
- **Agentic retrieval has latency** (query planning + parallel search + rerank + generation takes several seconds). Add loading states and pre-warm the demo book so the video stays snappy.
- **Don't let images become the bottleneck.** Keep generated art to a few hero visuals; the value is the faithful reading experience, not panel art.
- **Make the grounding visible.** The differentiator is "faithful, cited, never invents plot." Surface the citations / source passages on screen, or the app looks like any other LLM toy and the reliability story (20%) is lost.
- **Document Copilot usage.** A dedicated README section plus commit notes — this is a core track requirement, easy to forget.
- **Public-domain only.** Use Gutenberg titles; this keeps it copyright-safe and disclaimer-compliant for a public repo.

### How the build will go — 10-day plan (June 4–14)

*Stack-agnostic where possible; the web-vs-iOS choice mainly affects the client phase (see notes).*

1. **Phase 0 — Setup (Day 1).** Create the public repo + README skeleton; add `.gitignore` for secrets. Set up an Azure account / credits. Finalize web-vs-iOS. Pick the demo book.
2. **Phase 1 — Prove the core (Days 2–3).** Stand up Azure AI Search + a Foundry project + a model deployment. Ingest one Gutenberg book (fetch → chunk → index) into a Foundry IQ knowledge base. Get basic **faithful, grounded Q&A** working. This is the make-or-break milestone.
3. **Phase 2 — Experience layer (Days 4–6).** Scene segmentation + dramatized light-novel retelling grounded in the text; character cards; "talk to the story" Q&A with **visible citations**.
4. **Phase 3 — Client UI (Days 6–7).** Anime-styled interface: reading flow, character cards, chat panel, loading states. (Web: fastest path. iOS: a thin SwiftUI client over the same backend — add time for Xcode/Swift.)
5. **Phase 4 — Optional polish (Day 8).** One anime key visual per chapter via an image model; wire up the "add another book" path to demonstrate generality.
6. **Phase 5 — Reliability, README, demo, submit (Days 9–10).** Graceful "that isn't in the text" behavior; finish the README (architecture + Copilot usage); record the demo video; submit before the June 14 deadline. Keep buffer for rejection/rework.

### How it maps to the judging rubric

- **Accuracy & Relevance (20%):** grounded retrieval keeps retellings and answers faithful to the source text.
- **Reasoning & Multi-step Thinking (20%):** agentic retrieval decomposes queries into sub-queries; scene segmentation and point-of-view reasoning are multi-step.
- **Reliability & Safety (20%):** visible citations, a "won't invent plot" guarantee, and public-domain-only content.
- **Creativity & Originality (15%):** immersive, faithful "classic-as-anime" reading vs. the saturated from-scratch manga generators.
- **User Experience & Presentation (15%):** anime-styled UI, character cards, hero visuals, a smooth demo.
- **Community vote (10%):** a fun, shareable concept built on recognizable books.

### Open decisions

- **Web vs. iOS.** Web is the fastest path to a polished demo; iOS is the stronger portfolio piece (a thin SwiftUI client over the same backend). Note: **App Store publishing is not required** for the hackathon — demo from the simulator or a TestFlight build. (Publishing later is a separate, post-hackathon portfolio step.)
- **Project name** (currently "Living Book").
- **Demo book** (e.g., *Alice in Wonderland*, *Dracula*).
- **Whether to include hero images**, and which image model, for the optional visual flourish.

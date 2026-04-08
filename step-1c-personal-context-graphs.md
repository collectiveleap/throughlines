# Step 1c: Personal Context Graphs — Individual (Not Organizational) Use

## Status
Survey of real-world individual practices for capturing decision reasoning. Categorized by approach.

---

## 1. Decision Journals (Structured Rationale Capture)

### Shane Parrish / Farnam Street — Decision Journal
The most widely adopted personal decision-capture practice. Structured fields: date, mental/physical state, situation, problem framing, variables that matter, range of outcomes with probabilities, chosen option with reasoning, alternatives rejected and why. Reviewed at 6-month intervals. A 2024 Behavioral Science & Policy study found 19% improvement in forecasting accuracy with this method.

**Format:** PDF template / plain text
**Captures "why" via:** Explicit probability estimates, stated reasoning, emotional state at decision time
**Source:** [Decision Journal Template — Farnam Street](https://fs.blog/decision-journal/)

### Alvin Alexander — Adapted Decision Journal
Personal practice adapted from Farnam Street with expanded review schedule (1 week, 2 weeks, 1 month, 3 months, 6 months). Structured Markdown/text.

**Source:** [Decision journal template and example](https://alvinalexander.com/personal/decision-journal-template-example/)

### MyLifeNote.ai — Digital Decision Journal
Shipping product (2026) that digitizes the Farnam Street method. Fields: decision, expected outcome, confidence level, key factors, alternatives rejected, emotional state.

**Source:** [Decision Journal Template — MyLifeNote.ai](https://blog.mylifenote.ai/decision-journal-template-track-outcomes-improve-choices/)

---

## 2. Personal Knowledge Graphs in PKM Tools

### Matteo Paoli — Obsidian as a Personal ADR Tool
Applies Architecture Decision Records (an enterprise engineering pattern) to individual work in Obsidian. Template: Title, Status, Date, Context, Decision, Consequences. Markdown-native. Captures "why" via the Context and Consequences fields.

**Format:** Markdown in Obsidian
**Source:** [Using Obsidian as an ADR tool](https://medium.com/@mttpla/using-obsidian-as-an-adr-tool-5f63d187de6b)

### Eric Ma — Obsidian + AI Agents for Personal KM (2026)
Manages two teams, reduced KM overhead from 30-40% to under 10%. Note types: monthly bullet journals, meeting notes, people dossiers, project control towers. Plain-text Markdown vault processed by AI coding agents. Closest to a personal context graph operated with AI assistance.

**Format:** Markdown in Obsidian, processed by AI agents
**Source:** [Mastering PKM with Obsidian and AI](https://ericmjl.github.io/blog/2026/3/6/mastering-personal-knowledge-management-with-obsidian-and-ai/)

### Sebastien Dubois — PKM at Scale (8,000 notes, 64,000 links)
Three years in Obsidian. PARA + Johnny Decimal organization. Graph view surfaces emergent connections. Not decision-specific but demonstrates the infrastructure for a personal context graph — queryable, linked knowledge.

**Source:** [PKM at Scale](https://www.dsebastien.net/personal-knowledge-management-at-scale-analyzing-8-000-notes-and-64-000-links/)

### Obsidian Forum — Personal Decision Log Thread
Community discussion of actual individual practices. Multiple users sharing templates for logging decisions with reasoning in daily notes.

**Source:** [Creating a decision log in Obsidian](https://forum.obsidian.md/t/creating-a-decision-log-in-obsidian/51077)

---

## 3. AI Tools Building Personal Context/Memory

### Kin — Personal AI Advisors with On-Device Memory
50,000+ users. Five AI advisors (Work, Relationships, Values, Body, Social) with persistent on-device memory. Semantic + episodic memory. Privacy-first (local storage, E2EE). "Supports decisions that account for your full picture." The most direct implementation of a personal context graph as a consumer AI product.

**Source:** [mykin.ai](https://mykin.ai/)

### Second Me — Open-Source AI Identity System
Open-source, locally run. Three-layer memory: short-term interaction, medium-term behavioral, long-term cognitive. Trained on personal data to represent "your authentic self." More experimental than Kin but more powerful for builders.

**Sources:** [secondme.io](https://www.secondme.io/) | [arXiv paper](https://arxiv.org/html/2503.08102v1)

### Limitless (formerly Rewind AI) — Passive Personal Context Capture
Was a wearable pendant + software that recorded, transcribed, and summarized all conversations. Structured outputs: summaries, action items, searchable lifelogs. Acquired by Meta in Dec 2025. The most ambitious attempt at passive personal decision-context capture.

**Source:** [limitless.ai](https://www.limitless.ai/)

### Mem0 — Personal Memory Layer for AI Agents
Open-source (48K GitHub stars). Graph memory: entities as nodes, relationships as edges. User-scoped memory persists across sessions. Developer-oriented — individuals can build personal AI agents with persistent decision memory.

**Sources:** [mem0.ai](https://mem0.ai/) | [Graph Memory docs](https://docs.mem0.ai/open-source/features/graph-memory)

### Personal.ai — Memory Stacks
Stores "memory blocks" with time, people, context, and emotion metadata. Creates a "digital version of you" that retains and resurfaces personal knowledge.

**Source:** [personal.ai/memory](https://www.personal.ai/memory)

---

## 4. Second Brain / Zettelkasten (Decision-Adjacent)

### Tiago Forte — Building a Second Brain / PARA
500K+ copies sold. PARA (Projects, Areas, Resources, Archives) organizes personal knowledge by actionability. Decision reasoning is captured as a side effect, not a primary design goal. Recently launched "AI Second Brain" integration.

**Source:** [BASB Overview — Forte Labs](https://fortelabs.com/blog/basboverview/)

### Zettelkasten Method
Self-contained notes linked by reasoning context. "Relevant" links mean linked in the context of the reasoning at time of writing. Emergent structure reveals decision patterns. Tools: Obsidian, The Archive, plain text. Captures "why" through link rationale, but not structured for decision-specific queries.

**Source:** [zettelkasten.de](https://zettelkasten.de/)

---

## Gap Analysis: Where Steve's Project Fits

| Approach | Captures "Why" | Machine-Readable | Accumulates Precedent | Markdown-Storable |
|---|---|---|---|---|
| Decision journals (Farnam Street) | Strong | Weak | No | Yes |
| Personal ADRs (Obsidian) | Strong | Moderate | Weak | Yes |
| AI memory tools (Kin, Mem0) | Moderate | Strong | Yes | No |
| Second Brain / Zettelkasten | Weak | Weak | Emergent only | Yes |
| **Steve's project (target)** | **Strong** | **Strong** | **Yes** | **Yes** |

### The gap is real
Nobody found is doing exactly what Steve's project proposes: a **Markdown-native, structured, GenAI-readable personal decision trace format that accumulates into a queryable context graph**.

The closest exemplars are:
- **Personal ADRs in Obsidian** — right format (Markdown), right intent (capture "why"), but no AI integration or precedent retrieval
- **Eric Ma's Obsidian + AI system** — right tooling (Markdown + AI agents), but not decision-trace-specific
- **Kin** — right concept (personal AI with decision memory), but proprietary format, not Markdown-storable

### Implication for Step 2
The information model should borrow from:
- **Farnam Street's fields** — situation, alternatives, rationale, confidence, emotional state
- **ADR structure** — context, decision, consequences
- **AI memory graph structure** — entities as nodes, relationships as edges, user-scoped

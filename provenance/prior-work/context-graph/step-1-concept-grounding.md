# Context Graphs: Reference Guide

## Purpose
Reference document covering the origin, forms, and real-world uses of context graphs across enterprise and personal domains. All claims are linked to cited sources.

---

## 1. Origin and Definition

### 1.1 The Foundation Capital thesis

**Source:** Jaya Gupta and Ashu Garg, "AI's trillion-dollar opportunity: Context graphs," Foundation Capital, December 22, 2025.  ([link](https://foundationcapital.com/ideas/context-graphs-ais-trillion-dollar-opportunity))

The last generation of enterprise software created trillion-dollar companies by becoming **systems of record for objects** (customers, deals, tickets). The next generation will be built by those who capture **the reasoning behind decisions**. ([source](https://foundationcapital.com/ideas/context-graphs-ais-trillion-dollar-opportunity))

The problem: enterprises store *what happened* but not *why*. When a VP approves a 20% discount on a renewal, the CRM records one fact: "20% discount." The reasoning — three SEV-1 incidents, an angry customer threatening churn, a precedent set by another VP last quarter — lives in Slack threads, Zoom calls, and people's heads. AI agents hit a wall not because of missing data, but because of **missing decision traces**. ([source](https://foundationcapital.com/ideas/context-graphs-ais-trillion-dollar-opportunity))

### 1.2 Definition

Foundation Capital defines a context graph as:

> A living record of decision traces stitched across entities and time, where precedent becomes searchable. ([source](https://foundationcapital.com/ideas/context-graphs-ais-trillion-dollar-opportunity))

A context graph captures: how rules were applied in specific cases, where exceptions were granted, how conflicts were resolved, who approved what, and which precedents actually govern reality. It explains not just what happened, but **why it was allowed to happen**. ([source](https://foundationcapital.com/ideas/why-context-graphs-are-the-missing-layer-for-ai))

### 1.3 Follow-on articles

- [Context graphs, one month in](https://foundationcapital.com/context-graphs-one-month-in/) — reactions and refinements after the initial post
- [Why context graphs are the missing layer for AI](https://foundationcapital.com/ideas/why-context-graphs-are-the-missing-layer-for-ai) — deeper technical argument
- [The case for context graphs: With Aaron Levie (Box)](https://foundationcapital.com/ideas/the-case-for-context-graphs) — industry validation

---

## 2. Context Graph vs Knowledge Graph

| Dimension | Knowledge Graph | Context Graph |
|---|---|---|
| **Primary question** | "What is this?" | "Why was this decided?" |
| **Content** | Static facts, entity relationships | Dynamic decision traces, reasoning, exceptions |
| **Time** | Snapshot or slowly changing | Temporal — traces are ordered and accumulate |
| **Provenance** | Optional metadata | First-class: who, when, why, under what precedent |
| **Value** | Answers factual queries | Enables judgment reuse and precedent search |

Knowledge graphs represent what is known. Context graphs represent **how knowledge was applied** in specific situations to make specific decisions. ([Atlan](https://atlan.com/know/context-graph-vs-knowledge-graph/), [contextgraph.tech](https://www.contextgraph.tech/learn/context-graph-vs-knowledge-graph))

---

## 3. Academic and Conceptual Roots

### 3.1 Tacit knowledge (Polanyi, 1966)

"We know more than we can tell." Tacit knowledge is nonverbalized, intuitive, and embedded in skilled performance. A seasoned operator pattern-matches situations that fall outside documented protocols — and that judgment is the most valuable knowledge in an organization, yet the hardest to capture. Context graphs are an attempt to make a specific slice of tacit knowledge durable: not all of what someone knows, but **the reasoning they applied at the moment of decision**. ([Polanyi overview](https://infed.org/dir/welcome/michael-polanyi-and-tacit-knowledge/))

### 3.2 Process knowledge vs procedural knowledge (Talisman, 2025)

Jessica Talisman distinguishes:
- **Process knowledge** — tacit understanding and practiced expertise in how work *actually* happens
- **Procedural knowledge** — process knowledge that has been formalized, encoded, and represented through structured semantic systems

Context graphs require a path from process knowledge to procedural knowledge. Representations that lack semantic descriptive logic lose the nuanced context that makes process knowledge valuable. ([source](https://jessicatalisman.substack.com/p/context-graphs-and-process-knowledge))

### 3.3 Case-based reasoning (Aamodt & Plaza, 1994)

In case-based reasoning (CBR), the case library is the primary reasoning substrate. New problems are solved by retrieving similar past cases and adapting their solutions. Rules are extracted post-hoc from accumulated cases, not declared upfront. This maps directly to the context graph lifecycle: few traces early on, precedent surfacing as traces accumulate, candidate rules emerging from case clusters.

### 3.4 Decision provenance (W3C PROV, 2013)

The W3C Provenance model (PROV-O) provides formal constructs for recording: what entities existed, what activities occurred, which agents were involved, and what was derived from what. This is the closest existing standard to what a context graph needs for its record structure. ([Provenance-Aware Knowledge Representation](https://link.springer.com/article/10.1007/s41019-020-00118-0))

---

## 4. Enterprise Applications

### 4.1 Software Engineering

**Cognition AI — Agent Trace (open standard, 2026)**
An open specification backed by Cursor, Vercel, Cloudflare, and others. Links every code range to the conversation that produced it — the prompts, reasoning, iterations, and decisions. A context graph for codebases: not just attribution, but the full decision trace behind code changes.
([source](https://cognition.ai/blog/agent-trace))

**Spotify — Architecture Decision Records (ADRs)**
Multiple Spotify teams use ADRs to capture the *why* behind system design choices. Concrete benefits: faster onboarding, less knowledge loss during team ownership handoffs, better cross-team alignment. ADRs are manual context graphs for engineering decisions.
([source](https://engineering.atspotify.com/2020/04/when-should-i-write-an-architecture-decision-record))

### 4.2 Sales / RevOps

**Sweep — Context graphs for Salesforce orgs**
Continuously builds a living dependency graph of a Salesforce org's metadata (objects, fields, automations, permissions, code). Replaces "arguing from screenshots and tribal knowledge" with a shared, queryable map. Named customer: Augury.
([source](https://www.sweep.io/blog/a-practical-guide-to-context-graphs-in-the-enterprise))

### 4.3 Enterprise Marketing

**Writer — Knowledge Graph for marketing orchestration**
Deployed at Vanguard, Prudential, and Qualcomm. 6sense's CMO reports 50% increase in content output. Connects customer success insights to product marketing to sales battlecards to demand gen campaigns.
([source](https://writer.com/blog/context-graphs-marketing-as-the-tip-of-the-spear-in-the-enterprise/))

### 4.4 Banking and Insurance

**Interloom ($16.5M seed, 2026)**
Ingests millions of operational records (support emails, tickets, call transcripts) to map how problems *actually* get resolved. At **Commerzbank**, reduced the gap between documented and actual operational knowledge from ~50% to 5%. Won **Zurich Insurance**'s company-wide AI competition for an underwriting use case capturing institutional risk appetite and broker experience. Also working with Volkswagen and JLL.
([Fortune](https://fortune.com/2026/03/23/interloom-ai-agents-raises-16-million-venture-funding/), [Interloom blog](https://interloom.com/en/blog/seed-announcement/))

### 4.5 Compliance and Audit

**ElixirData — Decision Traces for governed AI agents**
"Context OS" auto-generates immutable decision traces: context consumed, policy evaluated, authority verified, outcome produced. Applied to insurance claims and financial services lending. Positions decision traces as legally defensible audit evidence.
([platform](https://www.elixirdata.co/platform/decisiontraces/), [traces vs. logs](https://www.elixirdata.co/blog/ai-agent-decision-traces-vs-logs-audit-trail-compliance))

**GraphCompliance (academic prototype)**
Represents regulatory texts as a Policy Graph and runtime contexts as a Context Graph; an LLM reasons over their alignment for multi-jurisdictional compliance.
([arXiv](https://arxiv.org/abs/2510.26309))

### 4.6 Healthcare

**Amigo AI ($11M Series A, 2026)**
Context graphs as the architecture for clinical AI agents doing intake, triage, and care navigation. Captures clinical logic, decision points, confidence scoring, and reflection moments. Over 3 million patient encounters with zero safety incidents.
([BusinessWire](https://www.businesswire.com/news/home/20260310898882/en/Amigo-AI-Raises-$11M-Series-A-to-Train-Clinical-AI-Agents-Like-Doctors), [Amigo docs](https://docs.amigo.ai/agent-architecture/context-graphs))

### 4.7 Data Governance

**Atlan — Active metadata context graph**
Encodes data assets, typed relationships, and the history of decisions made about those assets. Robinhood reportedly used it for GDPR compliance checks; Block uses it to estimate blast radius for data purges.
([source](https://atlan.com/know/what-is-a-context-graph/))

---

## 5. Personal / Individual Applications

### 5.1 Decision Journals

**Shane Parrish / Farnam Street — Decision Journal**
The most widely adopted personal decision-capture practice. Fields: date, mental/physical state, situation, problem framing, variables that matter, range of outcomes with probabilities, chosen option with reasoning, alternatives rejected and why. Reviewed at 6-month intervals. A 2024 Behavioral Science & Policy study found 19% improvement in forecasting accuracy.
Format: PDF template / plain text.
([source](https://fs.blog/decision-journal/))

**Alvin Alexander — Adapted Decision Journal**
Expanded review schedule (1 week, 2 weeks, 1 month, 3 months, 6 months). Structured Markdown/text.
([source](https://alvinalexander.com/personal/decision-journal-template-example/))

**MyLifeNote.ai — Digital Decision Journal (2026)**
Digitizes the Farnam Street method. Fields: decision, expected outcome, confidence level, key factors, alternatives rejected, emotional state.
([source](https://blog.mylifenote.ai/decision-journal-template-track-outcomes-improve-choices/))

### 5.2 Personal Knowledge Graphs in PKM Tools

**Matteo Paoli — Obsidian as a Personal ADR Tool**
Applies Architecture Decision Records to individual work. Template: Title, Status, Date, Context, Decision, Consequences. Markdown-native. Captures "why" via Context and Consequences fields.
([source](https://medium.com/@mttpla/using-obsidian-as-an-adr-tool-5f63d187de6b))

**Eric Ma — Obsidian + AI Agents for Personal KM (2026)**
Manages two teams. Reduced KM overhead from 30-40% to under 10%. Note types: monthly bullet journals, meeting notes, people dossiers, project control towers. Plain-text Markdown vault processed by AI coding agents. Closest to a personal context graph operated with AI assistance.
([source](https://ericmjl.github.io/blog/2026/3/6/mastering-personal-knowledge-management-with-obsidian-and-ai/))

**Sebastien Dubois — PKM at Scale (8,000 notes, 64,000 links)**
Three years in Obsidian. PARA + Johnny Decimal organization. Graph view surfaces emergent connections. Demonstrates the infrastructure for a personal context graph.
([source](https://www.dsebastien.net/personal-knowledge-management-at-scale-analyzing-8-000-notes-and-64-000-links/))

**Obsidian Forum — Personal Decision Log Thread**
Community discussion of actual practices. Multiple users sharing templates for logging decisions with reasoning.
([source](https://forum.obsidian.md/t/creating-a-decision-log-in-obsidian/51077))

### 5.3 AI Tools for Personal Context and Memory

**Kin — Personal AI Advisors (50,000+ users)**
Five AI advisors (Work, Relationships, Values, Body, Social) with persistent on-device memory. Semantic + episodic memory. Privacy-first (local storage, E2EE). "Supports decisions that account for your full picture."
([mykin.ai](https://mykin.ai/))

**Second Me — Open-Source AI Identity System**
Locally run. Three-layer memory: short-term interaction, medium-term behavioral, long-term cognitive. Trained on personal data to represent individual identity.
([secondme.io](https://www.secondme.io/), [arXiv](https://arxiv.org/html/2503.08102v1))

**Limitless (formerly Rewind AI)**
Wearable pendant + software. Recorded, transcribed, and summarized all conversations. Structured outputs: summaries, action items, searchable lifelogs. Acquired by Meta, Dec 2025.
([limitless.ai](https://www.limitless.ai/))

**Mem0 — Memory Layer for AI Agents (48K GitHub stars)**
Open-source graph memory: entities as nodes, relationships as edges. User-scoped, persists across sessions. Developer-oriented.
([mem0.ai](https://mem0.ai/), [Graph Memory docs](https://docs.mem0.ai/open-source/features/graph-memory))

**Personal.ai — Memory Stacks**
Memory blocks with time, people, context, and emotion metadata. Creates a persistent "digital version of you."
([personal.ai/memory](https://www.personal.ai/memory))

### 5.4 Second Brain and Zettelkasten

**Tiago Forte — Building a Second Brain / PARA**
PARA (Projects, Areas, Resources, Archives) organizes personal knowledge by actionability. 500K+ copies sold. Decision reasoning captured as a side effect. Recently launched "AI Second Brain" integration.
([source](https://fortelabs.com/blog/basboverview/))

**Zettelkasten Method**
Self-contained notes linked by reasoning context at time of writing. Emergent structure reveals decision patterns. Captures "why" through link rationale, but not structured for decision-specific queries.
([zettelkasten.de](https://zettelkasten.de/))

---

## 6. Forms and Formats in Use

Across the implementations surveyed, context graphs take several representational forms:

| Form | Used By | Human R/W | GenAI R/W | Markdown-Storable |
|---|---|---|---|---|
| **Structured text templates** (decision journals) | Farnam Street, MyLifeNote | Strong | Weak | Yes |
| **ADR format** (Title, Context, Decision, Consequences) | Spotify, Obsidian personal ADRs | Strong | Moderate | Yes |
| **Open trace specification** (JSON-based) | Cognition Agent Trace | Weak | Strong | In code blocks |
| **Property graph** (nodes + edges + properties) | Mem0, Atlan, Sweep | Weak | Strong | No |
| **Append-only event log** | ElixirData, Interloom | Weak | Strong | No |
| **Semantic/episodic memory** (AI-native) | Kin, Personal.ai, Second Me | None | Strong | No |
| **Linked notes** (bidirectional wiki links) | Obsidian, Zettelkasten | Strong | Moderate | Yes |

### Observation
No single existing form satisfies all four constraints this project requires: strong "why" capture, human-readable/writable, GenAI-readable/writable, and Markdown-storable. The closest are ADR-format Markdown and structured decision journal templates.

---

## 7. Gap Analysis

| Approach | Captures "Why" | Machine-Readable | Accumulates Precedent | Markdown-Storable |
|---|---|---|---|---|
| Decision journals (Farnam Street) | Strong | Weak | No | Yes |
| Personal ADRs (Obsidian) | Strong | Moderate | Weak | Yes |
| AI memory tools (Kin, Mem0) | Moderate | Strong | Yes | No |
| Second Brain / Zettelkasten | Weak | Weak | Emergent only | Yes |
| Enterprise agents (Interloom, ElixirData) | Strong | Strong | Yes | No |
| **This project (target)** | **Strong** | **Strong** | **Yes** | **Yes** |

The gap is real. No existing tool combines all four properties. The closest exemplars are:
- **Personal ADRs in Obsidian** — right format, right intent, but no AI integration or precedent retrieval
- **Eric Ma's Obsidian + AI system** — right tooling, but not decision-trace-specific
- **Kin** — right concept (personal AI with decision memory), but proprietary format

---

## 8. Working Definition for This Project

Synthesizing the above for Steve's use case (personal, cross-domain, human + GenAI):

**A context graph is a persistent, queryable record of decisions and their reasoning context — capturing not just what was decided, but the situation, alternatives, rationale, and precedent — in a form that both humans and AI agents can create, read, and use to inform future decisions.**

### Key properties:
1. **Personal** — captures one person's judgment, not organizational policy
2. **Cross-domain** — usable in software development, email triage, and other contexts
3. **Dual-audience** — readable and writable by both Steve and GenAI agents
4. **Accumulative** — grows over time; prior decisions become searchable precedent
5. **Portable** — storable in Markdown, not locked to a specific tool or database

### What a context graph is NOT (for this project):
- Not a knowledge graph (not just facts and entities)
- Not a decision log (not just a list of what was decided)
- Not a journal (not free-form narrative)
- Not a rule book (rules emerge from cases, not the reverse)

### Relationship to future work
The `personal-decision-intelligence-system/` subfolder describes a more elaborate system (four-layer architecture, rule genesis, case-based reasoning) that Steve intends to build *based on* the minimal viable forms and prompts defined here.

### Implication for Step 2
The information model should draw from:
- **Farnam Street's fields** — situation, alternatives, rationale, confidence, emotional state
- **ADR structure** — context, decision, consequences
- **AI memory graph structure** — entities as nodes, relationships as edges, user-scoped

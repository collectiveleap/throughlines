# Step 1: Concept Grounding — Context Graphs

## Status
Draft for Steve's review. Based on Foundation Capital's published thesis and related analysis.

---

## 1. The Foundation Capital Thesis

**Source:** "AI's trillion-dollar opportunity: Context graphs" by Jaya Gupta and Ashu Garg, Foundation Capital (December 22, 2025).

### Core argument

The last generation of enterprise software created trillion-dollar companies by becoming **systems of record for objects** (customers, deals, tickets). The next generation will be built by those who capture **the reasoning behind decisions**.

### The problem

Enterprises store *what happened* but not *why*. When a VP approves a 20% discount on a renewal, the CRM records one fact: "20% discount." The reasoning — three SEV-1 incidents, an angry customer threatening churn, a precedent set by another VP last quarter — lives in Slack threads, Zoom calls, and people's heads.

AI agents hit a wall not because of missing data, but because of **missing decision traces**. Agents encounter the same ambiguity humans resolve daily with judgment and organizational memory, but the inputs to those judgments aren't stored as durable artifacts.

### The definition

Foundation Capital calls the accumulated structure formed by these decision traces a **context graph**:

> A living record of decision traces stitched across entities and time, where precedent becomes searchable.

A context graph captures:
- How rules were applied in specific cases
- Where exceptions were granted
- How conflicts were resolved
- Who approved what
- Which precedents actually govern reality

It explains not just what happened, but **why it was allowed to happen**.

### The opportunity

The real prize isn't the $200B SaaS market — it's the $4.6T enterprises spend on salaries and services. Systems-of-agents startups that sit in the execution path see the full context at decision time. If they persist those traces, they create something that doesn't exist in most enterprises today: a queryable record of how decisions were made.

---

## 2. Context Graph vs Knowledge Graph

| Dimension | Knowledge Graph | Context Graph |
|---|---|---|
| **Primary question** | "What is this?" | "Why was this decided?" |
| **Content** | Static facts, entity relationships | Dynamic decision traces, reasoning, exceptions |
| **Time** | Snapshot or slowly changing | Temporal — traces are ordered and accumulate |
| **Provenance** | Optional metadata | First-class: who, when, why, under what precedent |
| **Value** | Answers factual queries | Enables judgment reuse and precedent search |

Knowledge graphs represent what is known. Context graphs represent **how knowledge was applied** in specific situations to make specific decisions.

---

## 3. Academic and Conceptual Roots

### 3.1 Tacit knowledge (Polanyi, 1966)

Michael Polanyi's foundational insight: "We know more than we can tell." Tacit knowledge is nonverbalized, intuitive, and embedded in skilled performance. A seasoned operator pattern-matches situations that fall outside documented protocols — and that judgment is the most valuable knowledge in an organization, yet the hardest to capture.

Context graphs are an attempt to make a specific slice of tacit knowledge durable: not all of what someone knows, but **the reasoning they applied at the moment of decision**.

### 3.2 Process knowledge vs procedural knowledge (Talisman, 2025)

Jessica Talisman draws a useful distinction:
- **Process knowledge** — tacit understanding and practiced expertise in how work *actually* happens
- **Procedural knowledge** — process knowledge that has been formalized, encoded, and represented through structured semantic systems

Context graphs require a path from process knowledge to procedural knowledge: systematic elicitation of tacit understanding, encoding it in representations that preserve semantic meaning, and tracking how procedures are actually executed in practice.

Key insight: representations that lack semantic descriptive logic lose the nuanced context that makes process knowledge valuable. Syntactic-only representations are disjointed and disconnected from overall processes.

### 3.3 Case-based reasoning (Aamodt & Plaza, 1994)

In case-based reasoning (CBR), the case library is the primary reasoning substrate. New problems are solved by retrieving similar past cases and adapting their solutions. Rules are extracted post-hoc from accumulated cases, not declared upfront.

This maps directly to the context graph lifecycle:
- Early on, the graph has few traces — each new decision is handled on its merits
- As traces accumulate, similar past decisions can be surfaced as relevant precedent
- Eventually, patterns across cases can be proposed as candidate rules

### 3.4 Decision provenance (W3C PROV, 2013)

The W3C Provenance model (PROV-O) provides formal constructs for recording: what entities existed, what activities occurred, which agents were involved, and what was derived from what. This is the closest existing standard to what a context graph needs for its record structure.

---

## 4. Working Definition for This Project

Synthesizing the above for Steve's specific use case (personal, cross-domain, human + GenAI):

**A context graph is a persistent, queryable record of decisions and their reasoning context — capturing not just what was decided, but the situation, alternatives, rationale, and precedent — in a form that both humans and AI agents can create, read, and use to inform future decisions.**

### Key properties for Steve's use case:
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

---

## 5. Open Questions for Steve

1. Does this definition align with your understanding from the Foundation Capital post?
2. The subfolder `personal-decision-intelligence-system/` describes a much more elaborate system (four-layer architecture, rule genesis, CBR). Is that the long-term vision, with the root-level `problem-space.md` describing the immediate practical goal? Or has the thinking evolved?
3. Are there specific decisions you've made recently (in software dev or email) that you'd want to use as test cases for defining the minimal viable form in Step 2?

---

## Sources
- [AI's trillion-dollar opportunity: Context graphs — Foundation Capital](https://foundationcapital.com/ideas/context-graphs-ais-trillion-dollar-opportunity)
- [Context graphs, one month in — Foundation Capital](https://foundationcapital.com/context-graphs-one-month-in/)
- [Why context graphs are the missing layer for AI — Foundation Capital](https://foundationcapital.com/ideas/why-context-graphs-are-the-missing-layer-for-ai)
- [Context Graphs and Process Knowledge — Jessica Talisman](https://jessicatalisman.substack.com/p/context-graphs-and-process-knowledge)
- [Context Graph vs Knowledge Graph — Atlan](https://atlan.com/know/context-graph-vs-knowledge-graph/)
- [Context Graph vs Knowledge Graph — contextgraph.tech](https://www.contextgraph.tech/learn/context-graph-vs-knowledge-graph)
- [Provenance-Aware Knowledge Representation — Springer](https://link.springer.com/article/10.1007/s41019-020-00118-0)

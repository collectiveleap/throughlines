# Step 2: Information Model — Context Graph

## Status
Revised draft. Incorporates cross-domain analysis from Step 1 reference guide.

---

## 1. Purpose

This document defines **what a context graph must contain** — the canonical elements, their relationships, and constraints — independent of any particular format or storage mechanism.

It also compares the information models used across existing implementations to identify which elements matter in which domains, and to ensure the model chosen for this project is well-grounded.

---

## 2. Attribute Inventory: What Existing Models Capture

Before defining our own model, here is a comprehensive inventory of attributes used across the implementations surveyed in Step 1.

| Attribute | Description | Used by |
|---|---|---|
| **Decision / Action** | What was decided or done | All models |
| **Context / Situation** | Circumstances at decision time | All models |
| **Rationale / Reasoning** | Why this decision was made | All models except pure event logs |
| **Date / Timestamp** | When the decision was made | All models |
| **Alternatives considered** | Options that were rejected | Farnam Street, ADRs |
| **Outcome / Consequences** | What happened as a result | ADRs, Farnam Street, Amigo AI |
| **Confidence level** | Certainty at decision time | Farnam Street, Amigo AI |
| **Probabilities** | Likelihood assigned to outcomes | Farnam Street |
| **Emotional / Mental state** | Decision-maker's cognitive state | Farnam Street, MyLifeNote |
| **Domain / Project** | What area this belongs to | ADRs, personal PKM |
| **Actors / Agents** | People involved or affected | PROV-O, Interloom, ElixirData |
| **Source / Origin** | Where the decision was captured | Interloom, Limitless, Mem0 |
| **Tags / Labels** | Cross-cutting categorization | Obsidian PKM, Zettelkasten |
| **Precedent links** | References to prior similar decisions | Foundation Capital thesis, CBR |
| **Policy reference** | What rule or policy was applied | ElixirData, Interloom, GraphCompliance |
| **Exception / Override** | Deviation from standard process | Interloom, Foundation Capital thesis |
| **Authority** | Who had the authority to decide | ElixirData, PROV-O |
| **Status** | State of the decision (proposed, approved, superseded) | ADRs, Amigo AI |
| **Reflection / Learning** | Post-decision insight | Amigo AI, Farnam Street (review cycle) |
| **Scope** | Narrow case vs generalizable pattern | Problem space doc (scope deferral) |
| **Variables / Constraints** | Key factors that shaped the decision | Farnam Street |
| **Code/artifact reference** | Link to code, document, or artifact | Agent Trace, Spotify ADRs |
| **Entity relationships** | Structured links between entities | Mem0, Atlan, Sweep, property graphs |

---

## 3. Cross-Domain Relevance Matrix

Not every attribute matters equally in every domain. This matrix shows which attributes are essential (E), useful (U), or not applicable (—) across the domains identified in Step 1.

| Attribute | Software Eng | Sales / RevOps | Banking / Insurance | Compliance | Healthcare | Personal Decisions | Personal PKM |
|---|---|---|---|---|---|---|---|
| **Decision** | E | E | E | E | E | E | E |
| **Context** | E | E | E | E | E | E | E |
| **Rationale** | E | E | E | E | E | E | U |
| **Date** | E | E | E | E | E | E | E |
| **Alternatives** | E | U | U | — | E | E | U |
| **Outcome** | U | E | E | E | E | U | — |
| **Confidence** | U | U | U | — | E | E | — |
| **Probabilities** | — | U | E | — | E | U | — |
| **Emotional state** | — | — | — | — | — | E | — |
| **Domain** | E | E | E | E | E | E | E |
| **Actors** | U | E | E | E | E | U | U |
| **Source** | U | E | E | E | E | U | U |
| **Tags** | U | U | U | U | U | U | E |
| **Precedent links** | E | E | E | E | E | U | U |
| **Policy reference** | U | E | E | E | E | — | — |
| **Exception/Override** | — | E | E | E | U | — | — |
| **Authority** | — | E | E | E | U | — | — |
| **Status** | E | U | U | E | U | — | U |
| **Reflection** | U | — | U | — | E | E | — |
| **Scope** | U | U | U | U | — | U | — |
| **Variables** | U | U | E | U | E | E | — |
| **Code/artifact ref** | E | — | — | U | — | — | U |
| **Entity relationships** | U | E | E | E | E | U | E |

### Reading the matrix

**Universal attributes** (essential everywhere): Decision, Context, Rationale, Date, Domain. These form the irreducible core.

**Domain-specific clusters:**
- **Regulated domains** (banking, compliance, healthcare) need: Policy reference, Exception/Override, Authority, Actors, Outcome — the audit trail cluster
- **Personal domains** need: Alternatives, Confidence, Emotional state, Reflection — the judgment-quality cluster
- **Software engineering** needs: Alternatives, Status, Code/artifact reference, Precedent — the architectural-reasoning cluster
- **Sales/RevOps** needs: Actors, Policy reference, Exception/Override, Authority — the deal-desk cluster

---

## 4. Information Model for This Project

Based on the cross-domain analysis, here is the model for Steve's personal, cross-domain context graph.

### 4.1 Core Elements (required)

Every decision trace must include:

| Element | Type | Description | Rationale for inclusion |
|---|---|---|---|
| **id** | string | Unique identifier (e.g., `dt-2026-04-08-001`) | Enables precedent linking |
| **decision** | text | What was decided — the action taken or choice made | Universal |
| **context** | text | The situation at decision time — inputs, conditions, constraints | Universal |
| **rationale** | text | Why this decision was made — reasoning connecting context to decision | Universal |
| **date** | date | When the decision was made | Universal |
| **domain** | string | The project or area (e.g., `software-dev`, `email-triage`) | Universal; enables multi-domain |

### 4.2 Extended Elements (optional, domain-dependent)

These add value when present. The relevance column indicates which of Steve's domains benefit most.

| Element | Type | Description | Most relevant to |
|---|---|---|---|
| **alternatives** | list of text | Options considered but not chosen | Software dev, personal decisions |
| **outcome** | text | What happened as a result (filled in retrospectively) | All — but deferred; captured later |
| **confidence** | enum: `high` / `medium` / `low` | How confident the decision-maker was | Personal decisions, ambiguous situations |
| **precedent** | list of id | IDs of prior traces that informed this decision | All — grows in value over time |
| **tags** | list of string | Free-form labels for cross-cutting concerns | All — enables search and grouping |
| **source** | text | Where this decision was made or captured | Email triage, meetings |
| **actors** | list of string | People involved in or affected by the decision | Email triage, advisory outreach |
| **variables** | list of text | Key factors that shaped the decision | Complex or high-stakes decisions |
| **reflection** | text | Post-decision learning (filled in retrospectively) | Personal growth, repeated decisions |
| **status** | enum: `active` / `superseded` / `revised` | Whether this trace is still the current position | Software dev (architecture decisions) |
| **artifact_ref** | text | Link to code, PR, document, email, etc. | Software dev, email triage |

### 4.3 Attributes Deliberately Excluded

These appear in enterprise models but are not needed for Steve's personal use case:

| Attribute | Why excluded |
|---|---|
| Policy reference | Steve isn't operating under organizational policy |
| Exception/Override | No standard process to deviate from (yet — future rule genesis) |
| Authority | Single decision-maker; no approval chain |
| Probabilities | Useful but high-friction; confidence level is a lighter proxy |
| Emotional state | Available in decision journals, but adds friction for routine decisions; can be captured in `context` when relevant |

These can be added later if Steve's use case evolves (e.g., the personal-decision-intelligence-system may reintroduce some of these).

---

## 5. Relationships Between Traces

### 5.1 Precedent links
A trace can reference prior traces that informed it. This is the primary structural relationship.
Direction: **new trace** → references → **prior trace(s)**

### 5.2 Domain grouping
Traces belong to domains. A single trace can belong to multiple domains (multi-project context).

### 5.3 Entity co-reference
Traces mentioning the same entities (people, systems, projects) are implicitly connected. Discoverable through search, not stored as explicit links.

### 5.4 Temporal ordering
Within a domain, date ordering represents the evolution of judgment over time.

### 5.5 Supersession
A trace with `status: superseded` should link to the trace that replaced it. This is how architectural decisions evolve.

---

## 6. Constraints

1. **Immutability** — Once recorded, a trace's core elements (decision, context, rationale, date) should not be modified. `outcome`, `reflection`, and `status` are designed to be updated retrospectively.

2. **Separation of fact and interpretation** — `context` records what was known at decision time, not a post-hoc reconstruction. `rationale` records the reasoning as it was.

3. **No required precedent** — Early traces will have no precedent links. This is expected (Phase 1: "no precedent").

4. **Multi-domain membership** — A trace may belong to more than one domain.

5. **Human-authored rationale** — `rationale` reflects the human's reasoning. GenAI may draft it, but the content should represent what the human actually thought.

6. **Graceful degradation** — A trace with only the 6 core elements is a valid trace. Optional elements add value but are never blocking.

---

## 7. Comparison: This Model vs Existing Models

| Model | Core overlap | What they add | What they lack |
|---|---|---|---|
| **Farnam Street Decision Journal** | Decision, context, rationale, date, alternatives | Emotional state, probabilities, review schedule | No IDs, no precedent links, no machine-readability |
| **ADR (Spotify-style)** | Decision, context (called "Context"), rationale (implied), date, status | Consequences (= outcome) | No confidence, no precedent links, no multi-domain |
| **Agent Trace (Cognition)** | Decision (code change), context (conversation), rationale (reasoning) | Code-range linking, iteration history | Not human-writable, software-only |
| **ElixirData Decision Traces** | Decision, context, rationale, date, actors | Policy reference, authority, exception | Compliance-focused, not personal |
| **Amigo AI Context Graphs** | Decision, context, rationale, confidence | Reflection moments, safety scoring | Healthcare-specific, proprietary |
| **PROV-O** | Actors (Agent), date (Activity), derivation links | Formal ontology, entity lifecycle | No rationale field, no alternatives |
| **Mem0 Graph Memory** | Entity relationships, temporal context | Persistent cross-session memory | No decision structure, no rationale |

### Key differentiators of this model:
- **Precedent links** — borrowed from Foundation Capital / CBR, absent from most personal tools
- **Multi-domain** — most personal tools assume single-context use
- **Dual retrospective fields** (outcome + reflection) — separates "what happened" from "what I learned"
- **Graceful degradation** — works with just 6 fields, unlike enterprise models that demand full audit trails

---

## 8. Minimal Example

```
id:           dt-2026-04-08-001
decision:     Created a new card in the prospect pipeline for Susan. Also replied to Tim
              (thanking him for the intro) and to Susan (suggesting a call).
context:      Steve has an active project to reach out to colleagues and ask them to introduce
              him to people matching his target audience for his private advisory practice.
              Tim sent an email introducing Susan, who may be relevant — possibly as a prospect,
              possibly as a channel, possibly as an interested peer. The nature of Susan's
              relevance is ambiguous at this stage.
rationale:    Best case is Susan is a prospect, so default to the highest-value interpretation
              and create a pipeline card. The card can be reclassified later if she turns out
              to be a channel or peer instead. Replying to both Tim and Susan maintains the
              relationship and moves the conversation forward.
alternatives:
  - File Susan as a contact only (no pipeline card) and follow up later
  - Wait for more information before taking action
date:         2026-04-08
domain:       advisory-outreach
tags:         prospect, introduction, pipeline
source:       email
actors:       Tim, Susan
precedent:    (none — early in this outreach project)
```

---

## 9. What This Model Does NOT Specify

Deliberately deferred:

- **Format** — How these elements are serialized (Markdown, YAML, JSON-LD, etc.) → Step 3
- **Storage** — Where traces live (files, database, etc.) → future work
- **Similarity** — How to determine that two traces are "similar" → future work
- **Rule extraction** — How to identify patterns across traces → future work
- **Interaction model** — How Steve captures traces in practice → Step 4 (prompts)

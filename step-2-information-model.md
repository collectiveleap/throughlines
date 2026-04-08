# Step 2: Information Model — Context Graph

## Status
Draft for Steve's review.

---

## 1. Purpose

This document defines **what a context graph must contain** — the canonical elements, their relationships, and constraints — independent of any particular format or storage mechanism. Any minimal viable form (Step 3) must be able to represent everything described here without loss.

---

## 2. Unit of Record: The Decision Trace

The atomic unit of a context graph is a **decision trace** — a structured record of a single decision and its reasoning context.

A context graph is a collection of decision traces linked to each other through precedent relationships and shared entities.

---

## 3. Decision Trace Elements

### 3.1 Required Elements

Every decision trace must include:

| Element | Type | Description |
|---|---|---|
| **id** | string | Unique identifier for this trace (e.g., `dt-2026-04-08-001`) |
| **decision** | text | What was decided — the action taken or choice made |
| **context** | text | The situation at decision time — what inputs, conditions, or constraints were present |
| **rationale** | text | Why this decision was made — the reasoning connecting context to decision |
| **date** | date | When the decision was made |
| **domain** | string | The project or area this decision belongs to (e.g., `software-dev`, `email-triage`, `hiring`) |

### 3.2 Optional Elements

These elements add value when present but are not required for every trace:

| Element | Type | Description |
|---|---|---|
| **alternatives** | list of text | Other options that were considered but not chosen |
| **precedent** | list of id | IDs of prior decision traces that informed this decision |
| **outcome** | text | What happened as a result of this decision (filled in retrospectively) |
| **confidence** | enum: `high`, `medium`, `low` | How confident the decision-maker was at the time |
| **tags** | list of string | Free-form labels for cross-cutting concerns (e.g., `cost`, `risk`, `deadline`) |
| **source** | text | Where this decision was made or captured (e.g., `slack-thread`, `pr-review`, `email`) |
| **actors** | list of string | People involved in or affected by the decision |

---

## 4. Relationships Between Traces

The "graph" in context graph comes from the connections between decision traces:

### 4.1 Precedent links
A trace can reference prior traces that informed it. This is the primary structural relationship — it's how the system learns that "this new situation is like that old situation."

Direction: **new trace** → references → **prior trace(s)**

### 4.2 Domain grouping
Traces belong to domains. A single trace can belong to multiple domains (matching the multi-project context requirement from the problem space).

### 4.3 Entity co-reference
Traces that mention the same entities (people, systems, projects) are implicitly connected. This is not stored as an explicit link but is discoverable through search.

### 4.4 Temporal ordering
Traces are ordered by date. Within a domain, this ordering represents the evolution of judgment over time.

---

## 5. Constraints

1. **Immutability** — Once recorded, a decision trace's core elements (decision, context, rationale, date) should not be modified. The `outcome` field is the exception — it is designed to be filled in or updated retrospectively.

2. **Separation of fact and interpretation** — The `context` field records what was known at decision time, not a post-hoc reconstruction. The `rationale` records the reasoning as it was at the time.

3. **No required precedent** — Early traces will have no precedent links. This is expected and correct (Phase 1 from the problem space: "no precedent"). The system must not require precedent to create a valid trace.

4. **Multi-domain membership** — A trace may belong to more than one domain. Domain assignment is not exclusive.

5. **Human-authored rationale** — The `rationale` field captures the decision-maker's own reasoning. When GenAI assists in capturing a trace, it may draft the rationale, but the content should reflect the human's reasoning, not the AI's.

---

## 6. Minimal Example

A real decision trace from Steve's advisory practice outreach project:

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

## 7. What This Model Does NOT Specify

Deliberately deferred to later steps:

- **Format** — How these elements are serialized (Markdown, YAML, JSON-LD, etc.) → Step 3
- **Storage** — Where traces live (files, database, etc.) → future work
- **Similarity** — How to determine that two traces are "similar" → future work (personal-decision-intelligence-system)
- **Rule extraction** — How to identify patterns across traces → future work
- **Interaction model** — How Steve captures traces in practice → Step 4 (prompts)

---

## 8. Resolved Questions

1. **Element set** — Steve confirmed this is a good initial start.
2. **Confidence** — Keep as optional. Useful when present, no overhead when omitted.
3. **Alternatives** — Keep as optional. Same reasoning.
4. **Actors** — Confirmed optional.

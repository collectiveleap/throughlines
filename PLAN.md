# Plan: Context Graph — Minimal Viable Forms

## Goal
Steve becomes familiar with context graphs, defines minimal viable forms for representing them, and defines prompts for GenAI to create and consume them.

## Success Criteria (from solution-space.md)
- [ ] Steve confirms understanding of context graph POV (Foundation Capital + academic research)
- [ ] Steve confirms understanding of context graphs as tacit knowledge representation ("why" behind decisions)
- [ ] One or more minimal viable forms defined that are human r/w, GenAI r/w, losslessly translatable, Markdown-storable
- [ ] One or more minimal viable prompts defined for GenAI to create/update and consume/use context graphs

---

## Step 1: Ground the Concept
**Status:** Complete (draft for review)

Research and summarize the Foundation Capital POV on context graphs and relevant academic foundations. Produce a reference document Steve can confirm or correct.

**Output:** `step-1-concept-grounding.md`

**Covers:**
- Foundation Capital's context graph thesis
- Academic roots (tacit knowledge, decision provenance, knowledge representation)
- Working definition of "context graph" for this project

---

## Step 2: Define the Information Model
**Status:** Not started

Before picking a format, define what a context graph must contain. Likely elements:
- The decision made
- The context (situation, inputs, constraints)
- The alternatives considered
- The rationale (why this choice)
- Links to prior similar decisions (precedent)
- Metadata (who, when, domain/project)

**Output:** Information model spec (schema or structured description)

---

## Step 3: Design Minimal Viable Forms
**Status:** Not started

Create 2-3 candidate representations satisfying all constraints (human r/w, GenAI r/w, lossless translation, Markdown-storable). Candidates may include:
- Structured Markdown (headings + key-value)
- YAML front matter + Markdown body
- JSON-LD in a Markdown code block

Test each against a concrete example. Confirm lossless round-tripping.

**Output:** Form definitions + example decision in each form

---

## Step 4: Design Minimal Viable Prompts
**Status:** Not started

Write two prompts:
- **Capture prompt** — GenAI creates/updates a context graph when Steve makes a decision
- **Retrieval prompt** — GenAI surfaces relevant prior context graphs when Steve faces a new decision

**Output:** Tested prompt templates

---

## Step 5: Validate End-to-End
**Status:** Not started

Run the full loop on a real decision from Steve's work (software dev or email triage). Confirm format and prompts work in practice.

**Output:** Validated example + any adjustments to forms/prompts

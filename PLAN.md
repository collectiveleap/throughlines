# Plan: Context Graph — Minimal Viable Forms

## Goal
Steve becomes familiar with context graphs, defines minimal viable forms for representing them, and defines prompts for GenAI to create and consume them.

## Success Criteria (from solution-space.md)
- [x] Steve confirms understanding of context graph POV (Foundation Capital + academic research)
- [x] Steve confirms understanding of context graphs as tacit knowledge representation ("why" behind decisions)
- [ ] One or more minimal viable forms defined that are human r/w, GenAI r/w, losslessly translatable, Markdown-storable
- [ ] One or more minimal viable prompts defined for GenAI to create/update and consume/use context graphs

---

## Step 1: Ground the Concept
**Status:** Complete (confirmed by Steve)

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

### Step 5a: Capture Steve's test-case decisions
Steve identifies specific recent decisions (software dev, email, or other domains) to use as concrete test cases. These ground all format and prompt validation in real examples.

**Output:** 2-3 real decision descriptions from Steve

### Step 5b: Run the full loop
Apply the capture prompt to Steve's test-case decisions, generate context graphs in the chosen form(s), then use the retrieval prompt against them. Confirm format and prompts work in practice.

**Output:** Validated examples + any adjustments to forms/prompts

---

## Relationship to Future Work

The `personal-decision-intelligence-system/` subfolder describes a more elaborate system (four-layer architecture, rule genesis, case-based reasoning) that Steve intends to build *based on* the minimal viable forms and prompts defined here. This project provides the foundation; that system is a downstream application.

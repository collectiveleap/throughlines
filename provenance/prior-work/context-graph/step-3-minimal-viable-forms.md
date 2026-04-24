# Step 3: Minimal Viable Forms — Context Graph

## Status
Draft for Steve's review.

---

## 1. Constraints (from solution-space.md)

Every form must satisfy all four:

1. **Human readable and writable** — Steve can author and review traces without tooling
2. **GenAI readable and writable** — Claude (or another LLM) can create, parse, and update traces
3. **Losslessly translatable** — any form can be converted to any other without information loss
4. **Markdown-storable** — can live in a `.md` file and render sensibly in any Markdown viewer

---

## 2. Candidate Forms

Three candidates, each using the real example from Step 2.

---

### Form A: Structured Markdown

The most human-friendly option. Uses headings and lists natively.

```markdown
# Decision Trace: dt-2026-04-08-001

**Date:** 2026-04-08
**Domain:** advisory-outreach
**Source:** email
**Confidence:** (not specified)

## Decision
Created a new card in the prospect pipeline for Susan. Also replied to Tim
(thanking him for the intro) and to Susan (suggesting a call).

## Context
Steve has an active project to reach out to colleagues and ask them to introduce
him to people matching his target audience for his private advisory practice.
Tim sent an email introducing Susan, who may be relevant — possibly as a prospect,
possibly as a channel, possibly as an interested peer. The nature of Susan's
relevance is ambiguous at this stage.

## Rationale
Best case is Susan is a prospect, so default to the highest-value interpretation
and create a pipeline card. The card can be reclassified later if she turns out
to be a channel or peer instead. Replying to both Tim and Susan maintains the
relationship and moves the conversation forward.

## Alternatives
- File Susan as a contact only (no pipeline card) and follow up later
- Wait for more information before taking action

## Tags
prospect, introduction, pipeline

## Actors
Tim, Susan

## Precedent
(none — early in this outreach project)

## Outcome
(to be filled in later)
```

**Strengths:**
- Most natural to read and write by hand
- Renders perfectly in any Markdown viewer
- Structure is immediately obvious to a human skimming the file

**Weaknesses:**
- Parsing requires convention-dependent logic (GenAI must know that `**Date:**` is a field, not prose)
- Metadata fields mixed with prose sections — no clean separation between structured data and narrative
- Harder to validate programmatically

---

### Form B: YAML Front Matter + Markdown Body

Structured metadata up top, narrative sections below. This is the convention used by static site generators (Jekyll, Hugo), note-taking tools (Obsidian), and many documentation systems.

```markdown
---
id: dt-2026-04-08-001
date: 2026-04-08
domain: advisory-outreach
source: email
tags: [prospect, introduction, pipeline]
actors: [Tim, Susan]
precedent: []
outcome:
---

# Decision
Created a new card in the prospect pipeline for Susan. Also replied to Tim
(thanking him for the intro) and to Susan (suggesting a call).

# Context
Steve has an active project to reach out to colleagues and ask them to introduce
him to people matching his target audience for his private advisory practice.
Tim sent an email introducing Susan, who may be relevant — possibly as a prospect,
possibly as a channel, possibly as an interested peer. The nature of Susan's
relevance is ambiguous at this stage.

# Rationale
Best case is Susan is a prospect, so default to the highest-value interpretation
and create a pipeline card. The card can be reclassified later if she turns out
to be a channel or peer instead. Replying to both Tim and Susan maintains the
relationship and moves the conversation forward.

# Alternatives
- File Susan as a contact only (no pipeline card) and follow up later
- Wait for more information before taking action
```

**Strengths:**
- Clean separation: structured data (YAML) vs narrative (Markdown)
- YAML front matter is a widely understood convention — parseable by standard libraries in every language
- GenAI can reliably extract and update metadata fields without touching prose
- Human-readable in raw form; Markdown viewers either render the front matter or hide it cleanly
- Extensible: new metadata fields can be added without changing the document structure

**Weaknesses:**
- YAML syntax errors (indentation, quoting) can break parsing
- Two "languages" in one file — a human must understand both YAML and Markdown conventions
- Front matter is less visually appealing than pure Markdown when reading raw files

---

### Form C: JSON Block + Markdown Body

A JSON code block for machine-readable data, followed by Markdown narrative. Useful if interoperability with APIs or structured tooling is a priority.

```markdown
# Decision Trace: dt-2026-04-08-001

```json
{
  "id": "dt-2026-04-08-001",
  "date": "2026-04-08",
  "domain": "advisory-outreach",
  "source": "email",
  "tags": ["prospect", "introduction", "pipeline"],
  "actors": ["Tim", "Susan"],
  "precedent": [],
  "outcome": null,
  "decision": "Created a new card in the prospect pipeline for Susan. Also replied to Tim (thanking him for the intro) and to Susan (suggesting a call).",
  "context": "Steve has an active project to reach out to colleagues and ask them to introduce him to people matching his target audience for his private advisory practice. Tim sent an email introducing Susan, who may be relevant — possibly as a prospect, possibly as a channel, possibly as an interested peer. The nature of Susan's relevance is ambiguous at this stage.",
  "rationale": "Best case is Susan is a prospect, so default to the highest-value interpretation and create a pipeline card. The card can be reclassified later if she turns out to be a channel or peer instead. Replying to both Tim and Susan maintains the relationship and moves the conversation forward.",
  "alternatives": [
    "File Susan as a contact only (no pipeline card) and follow up later",
    "Wait for more information before taking action"
  ]
}
```

**Strengths:**
- Fully machine-parseable with zero ambiguity
- Single canonical representation — everything in one structure
- Maps directly to APIs, databases, and programmatic tooling
- GenAI can produce and consume reliably

**Weaknesses:**
- Least human-friendly to read or write by hand
- Long text fields (context, rationale) are awkward inside JSON strings — no line breaks, no formatting
- Loses the readability advantage of Markdown for the narrative sections
- JSON in a Markdown code block is storable but not a pleasant reading experience

---

## 3. Evaluation Matrix

| Criterion | Form A: Structured MD | Form B: YAML + MD | Form C: JSON Block |
|---|---|---|---|
| Human readable | Best | Good | Poor |
| Human writable | Best | Good | Poor |
| GenAI readable | Good | Best | Best |
| GenAI writable | Good | Best | Best |
| Lossless translation | Good (if conventions held) | Best (clear separation) | Best (unambiguous) |
| Markdown-storable | Best (native) | Best (standard convention) | Adequate (code block) |
| Extensibility | Moderate | Best | Good |
| Error-resistance | Moderate | Moderate (YAML quirks) | Low (JSON syntax strict) |

---

## 4. Recommendation

**Form B (YAML front matter + Markdown body)** is the strongest candidate for the primary working form:

- It hits the **dual-audience** requirement best: metadata is cleanly separated for machines, narrative is natural Markdown for humans.
- It's the most **extensible** — adding a new field to the YAML block doesn't change the document's character.
- It's a **known convention** — Obsidian, Hugo, Jekyll, and many GenAI tools already expect this pattern, so tooling support is broad.
- **Lossless translation** is straightforward: YAML parses to a dictionary, Markdown sections parse by heading, and the combination covers the full information model.

Form A is a good fallback if Steve finds YAML front matter annoying to write by hand. Form C is useful as an export/interchange format but not recommended as the primary authoring form.

---

## 5. Proposed Convention

If Form B is adopted, the convention would be:

- **One file per decision trace**, named `{id}.md` (e.g., `dt-2026-04-08-001.md`)
- **YAML front matter** contains: `id`, `date`, `domain`, `source`, `tags`, `actors`, `precedent`, `outcome`, `confidence`
- **Markdown body** contains sections: `# Decision`, `# Context`, `# Rationale`, `# Alternatives` (optional)
- Files stored in a `traces/` directory, optionally organized by domain subdirectories

---

## 6. Open Questions for Steve

1. Does Form B feel right as the primary form? Or does Form A's pure-Markdown simplicity appeal more for day-to-day use?
2. File-per-trace vs. one file with multiple traces: any preference? File-per-trace is cleaner for version control and linking, but a single file is easier to scan.
3. Directory structure preference: flat `traces/` folder, or `traces/{domain}/` subdirectories?

# Potential Solutions Space: Personal Decision Intelligence System

## Status
Working document. Each entry is a candidate approach anchored to a need in the Problem Space document. No solution has been selected. Multiple candidates may coexist for the same need.

---

## 1. Fact Capture

**Problem Space reference:** Section 3 — Fact Capture

### Candidate: Semantic graph representation (e.g. RDF triples)
In order to make facts queryable and composable across inputs and projects, a possible solution is representing facts as subject-predicate-object triples in a graph structure. This allows facts to be linked across entities and queried relationally without requiring a fixed schema.

### Candidate: Natural language semantic representation (e.g. AMR)
In order to preserve the meaning of facts derived from natural language inputs while maintaining semantic precision, a possible solution is Abstract Meaning Representation (AMR). AMR captures predicate-argument structure and quantification in a form that bridges natural language and formal representation. See thread examples: asset dependency and collection membership expressed as AMR graphs.

### Candidate: Linked data with namespace control (e.g. JSON-LD)
In order to make fact representations interoperable with external systems and web-based linked data standards, a possible solution is JSON-LD. This is a pragmatic choice when integration breadth matters more than semantic expressiveness.

---

## 2. Proposal Representation

**Problem Space reference:** Section 4 — Proposal Representation

### Candidate: Named graphs with modal annotation (e.g. RDF named graphs)
In order to represent proposed state while keeping it distinguishable from current state, a possible solution is wrapping proposed subgraphs in named graphs with an explicit modal status marker (e.g. `proposal` vs `current`). This allows reasoning over both states simultaneously without conflating them.

### Candidate: Reified semantic frames (e.g. AMR reification)
In order to represent a proposal in natural language semantic terms while marking its epistemic status, a possible solution is AMR reification — wrapping the proposed action in a `propose-01` or `recommend-01` frame. This preserves the semantic content of the proposal in a form traceable to the language that generated it.

---

## 3. Approved Case Records

**Problem Space reference:** Section 7 — Approved Case Record

### Candidate: Provenance ontology (e.g. PROV-O)
In order to record what inputs were present at decision time, who approved, what derivation links exist between inputs and outcomes, and what the rationale was, a possible solution is the W3C Provenance Ontology (PROV-O). PROV-O has first-class constructs for `Entity`, `Activity`, `Agent`, `wasGeneratedBy`, `wasDerivedFrom`, and `wasInfluencedBy` — covering the full decision record structure. It spans fact capture, proposal representation, and retrospective provenance, making it a candidate spine across multiple needs.

### Candidate: Citable micro-records (e.g. Nanopublications)
In order to create fine-grained, individually citable records at the case level — each bundling an assertion, its provenance, and metadata — a possible solution is the nanopublication pattern. Nanopublications are lightweight RDF structures well-suited to fact-level change tracking where individual cases need to be independently referenceable.

### Candidate: Event-sourced append-only log
In order to maintain an immutable, auditable history of approvals and decisions, a possible solution is an append-only event log. The log records what changed and when; a paired context graph records why. Together they provide both auditability and reasoning structure. The log is the record of fact; the graph is the record of rationale.

---

## 4. Rule Genesis and Case Accumulation

**Problem Space reference:** Section 5 — Rule Genesis

### Candidate: Case-based reasoning architecture
In order to support reasoning by analogy before explicit rules exist, and to defer generalization until case density supports it, a possible solution is a case-based reasoning (CBR) architecture. In CBR, the case library is the primary reasoning substrate; rules are extracted post-hoc from accumulated cases rather than declared upfront. This matches the zero-rules initial state and the phase-based lifecycle described in the problem space.

### Candidate: Common law / precedent model
In order to handle the situation where each approved decision may reshape the rule space and later decisions may need to be interpreted against earlier ones for consistency, a possible solution is modeling the accumulation process analogously to common law — where precedent is the operative authority and rules crystallize from case clusters rather than being declared. This is an architectural framing rather than a specific technology, but it has implications for how the similarity function and coherence mechanism are designed.

---

## 5. Multi-Project Context and Rule Coherence

**Problem Space reference:** Section 6 — Multi-Project Context

### Candidate: Defeasible logic / argumentation frameworks
In order to surface and resolve conflicts between emergent rules across projects — where rules may be valid within their project context but conflict when applied to cross-project inputs — a possible solution is defeasible logic or Dung-style argumentation frameworks. These provide formal mechanisms for reasoning about which rule prevails when two valid rules conflict, without requiring one to be deleted.

---

## 6. Interaction Model and Approval Capture

**Problem Space reference:** Section 9 — Open Problems (Interaction model)

### Candidate: Structured approval with rationale elicitation
In order to capture approvals with enough structure to be useful as case records — particularly for novel decisions where rationale cannot be reconstructed from the trace — a possible solution is a structured approval interaction that prompts the human to articulate reasoning at decision time. The prompt should be lightweight enough not to create friction but structured enough to produce a usable rationale record.

---

## 7. Persistence and Linking

**Problem Space reference:** Section 9 — Open Problems (Persistence and linking)

### Candidate: Property graph (e.g. Neo4j-style)
In order to persist the four layers and maintain traversable links between raw facts, proposed interpretations, approved cases, and emergent patterns, a possible solution is a property graph database. Property graphs support flexible schema, rich edge types, and graph traversal queries. They are the most common implementation choice in current agent memory systems.

### Candidate: RDF triplestore with named graphs
In order to persist the four layers while maintaining interoperability with PROV-O and linked data standards, a possible solution is an RDF triplestore with named graph support. This is more expressive than a property graph for provenance-heavy use cases but carries higher implementation overhead.

### Candidate: Hybrid event log + graph
In order to separate the concerns of immutable history (what happened, in what order) from queryable structure (what relates to what), a possible solution is a hybrid architecture: an append-only event log for the historical record paired with a graph that is updated as cases accumulate. The log provides auditability; the graph provides reasoning substrate.

---

## 8. Similarity and Threshold

**Problem Space reference:** Section 9 — Open Problems (Similarity function, Threshold mechanism)

No candidates specified yet. These remain open.

---

## Notes on Solution Selection

No solutions have been chosen. The purpose of this document is to maintain a structured inventory of candidates, each anchored to a specific need, so that selection decisions can be made explicitly and evaluated against the problem space rather than assumed.

When a solution is selected for a given need, it should be moved to a separate Architecture Decision Record (ADR) documenting: the need it addresses, the alternatives considered, the selection rationale, and any constraints it imposes on other solution choices.

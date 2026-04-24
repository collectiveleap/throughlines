# Step 1b: Context Graphs in Practice — Who Is Actually Using Them?

## Status
Survey of real-world implementations. Categorized by domain.

---

## Software Engineering

### Cognition AI — Agent Trace (open standard, 2026)
An open specification backed by Cursor, Vercel, Cloudflare, and others. Links every code range to the conversation that produced it — the prompts, reasoning, iterations, and decisions. A context graph for codebases: not just attribution, but the full decision trace behind code changes.

**Status:** Shipping product / open standard
**Source:** [Agent Trace: Capturing the Context Graph of Code](https://cognition.ai/blog/agent-trace)

### Spotify — Architecture Decision Records (ADRs)
Multiple Spotify teams (e.g., the Creator Team) use ADRs to capture the *why* behind system design choices. Concrete benefits reported: faster onboarding, less knowledge loss during team ownership handoffs, better cross-team alignment. ADRs are essentially manual context graphs for engineering decisions.

**Status:** Real practitioner experience, widely adopted
**Source:** [When Should I Write an ADR — Spotify Engineering](https://engineering.atspotify.com/2020/04/when-should-i-write-an-architecture-decision-record)

---

## Sales / RevOps

### Sweep — Context graphs for Salesforce orgs
Continuously builds a living dependency graph of a Salesforce org's metadata (objects, fields, automations, permissions, code). Customer Augury uses it across Admin and RevOps to surface dependencies, explain legacy logic, and do impact analysis before changes. Replaces "arguing from screenshots and tribal knowledge" with a shared map.

**Status:** Shipping product with named customers
**Source:** [Sweep — Context Graphs in the Enterprise](https://www.sweep.io/blog/a-practical-guide-to-context-graphs-in-the-enterprise)

---

## Enterprise Marketing

### Writer — Knowledge Graph for marketing orchestration
Writer's Knowledge Graph (originally called "orchestration graph") is deployed at Vanguard, Prudential, and Qualcomm. 6sense's CMO reports 50% increase in content output. Connects customer success insights to product marketing to sales battlecards to demand gen campaigns.

**Status:** Production use with named enterprise customers
**Source:** [Context Graphs: Marketing as the Tip of the Spear — Writer](https://writer.com/blog/context-graphs-marketing-as-the-tip-of-the-spear-in-the-enterprise/)

---

## Banking / Insurance (Regulated Industries)

### Interloom — Context graphs for banking and insurance ($16.5M seed, 2026)
Ingests millions of operational records (support emails, tickets, call transcripts) to map how problems *actually* get resolved. At **Commerzbank**, reduced the gap between documented and actual operational knowledge from ~50% to 5%. Won **Zurich Insurance**'s company-wide AI competition (beating 2,000 startups) for an underwriting use case capturing institutional risk appetite and broker experience. Also working with **Volkswagen** and **JLL**.

**Status:** Strongest real-world case study found — production use, multiple named customers
**Sources:**
- [Interloom raises $16.5M — Fortune](https://fortune.com/2026/03/23/interloom-ai-agents-raises-16-million-venture-funding/)
- [Interloom seed announcement](https://interloom.com/en/blog/seed-announcement/)

---

## Compliance / Audit

### ElixirData — Decision Traces for governed AI agents
Shipping product ("Context OS") that auto-generates immutable decision traces capturing: context consumed, policy evaluated, authority verified, and outcome produced. Applied to insurance claims processing and financial services lending decisions. Positions decision traces as legally defensible audit evidence.

**Status:** Shipping product with specific use cases
**Sources:**
- [Decision Traces — ElixirData](https://www.elixirdata.co/platform/decisiontraces/)
- [Decision Traces vs. Logs](https://www.elixirdata.co/blog/ai-agent-decision-traces-vs-logs-audit-trail-compliance)

### GraphCompliance (academic prototype)
Represents regulatory texts as a Policy Graph and runtime operational contexts as a Context Graph; an LLM reasons over their alignment for multi-jurisdictional regulatory compliance.

**Status:** Research prototype, not production
**Source:** [GraphCompliance — arXiv](https://arxiv.org/abs/2510.26309)

---

## Healthcare

### Amigo AI — Context graphs for clinical AI agents ($11M Series A, 2026)
Uses context graphs as the architecture for clinical AI agents doing intake, triage, and care navigation. The graph captures clinical logic, decision points, confidence scoring, and reflection moments. Over 3 million patient encounters with zero safety incidents. Investors include Optum Ventures.

**Status:** Production system with real patient volume
**Sources:**
- [Amigo AI raises $11M](https://www.businesswire.com/news/home/20260310898882/en/Amigo-AI-Raises-$11M-Series-A-to-Train-Clinical-AI-Agents-Like-Doctors)
- [Context Graphs — Amigo docs](https://docs.amigo.ai/agent-architecture/context-graphs)

---

## Data Governance

### Atlan — Active metadata context graph
Atlan's context graph encodes data assets, typed relationships, and the *history of decisions* made about those assets. Robinhood reportedly used it to automate GDPR compliance checks for UK/EU launches; Block uses it to estimate blast radius for data purges.

**Status:** Production use with named customers
**Source:** [What Is a Context Graph — Atlan](https://atlan.com/know/what-is-a-context-graph/)

---

## Summary: Where Context Graphs Deliver the Most Value

| Domain | Example | Key Value |
|---|---|---|
| Software Engineering | Cognition (Agent Trace), Spotify (ADRs) | Why code/architecture decisions were made |
| Sales / RevOps | Sweep | Why Salesforce was configured this way |
| Enterprise Marketing | Writer | Why messaging is aligned across teams |
| Banking / Insurance | Interloom | How problems *actually* get resolved vs. how docs say |
| Compliance / Audit | ElixirData | Legally defensible decision audit trails |
| Healthcare | Amigo AI | Clinical decision logic with safety guarantees |
| Data Governance | Atlan | History of decisions about data assets |

### Common thread
Context graphs deliver the most value where the gap between how organizations *say* they work and how they *actually* work is widest — typically in **regulated, high-stakes, and high-turnover environments**.

### Relevance to Steve's project
Steve's use case is *personal* rather than organizational, but the same gap exists: the reasoning behind daily decisions (in software dev, email triage, project management) is lost unless deliberately captured. The implementations above suggest the most practical starting points are:
- **ADR-style records** (Spotify) — closest to a human-writable, Markdown-storable context graph
- **Agent Trace** (Cognition) — closest to a GenAI-writable context graph in a software dev context
- **Interloom's approach** — closest to the personal-decision-intelligence-system vision (ingesting communications, extracting decision traces)

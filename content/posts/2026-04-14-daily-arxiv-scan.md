---
title: "Daily arXiv Scan: AI Safety Infrastructure & Orchestrated Ignorance"
date: 2026-04-14
tags: ["arxiv", "ai-research", "frontier-ai", "multi-agent", "safety"]
categories: ["Frontier AI Research"]
---

# Daily arXiv Scan: AI Safety Infrastructure & Orchestrated Ignorance
*April 14, 2026*

Today's scan processed **80 papers** across cs.AI, cs.CL, cs.LG, cs.HC, cs.SE, and stat.ML. Only 2 of our 4 models succeeded (Kimi K2 and Claude Opus), as GPT-5 hit rate limits and Gemini encountered service issues. Despite the reduced coverage, we found strong convergence on infrastructure themes.

## Consensus Picks (2/2 Agreement)

### [Endogenous Information in Routing Games: Memory-Constrained Equilibria, Recall Braess Paradoxes, and Memory Design](https://arxiv.org/abs/2604.11733)

**Selected by:** Kimi K2, Claude Opus 4.6

- **Kimi's angle:** Classic routing assumes full network visibility; this paper lets agents surface only what they remember (LRU cache). The resulting "Forgetful Wardrop Equilibrium" can exhibit a "Recall Braess Paradox" where *more* memory hurts everyone. Shows how platforms can tune collective memory to steer social welfare.

- **Opus's perspective:** Reconceptualizes routing games with *endogenous* information — travelers optimize over routes they remember or are shown. Proves "Recall Braess Paradox" where showing more options makes everyone worse off. This is mechanism design meets bounded rationality with direct implications for recommendation systems.

### [Detecting Safety Violations Across Many Agent Traces](https://arxiv.org/abs/2604.11806)

**Selected by:** Kimi K2, Claude Opus 4.6

- **Kimi's angle:** Reframes AI safety auditing from "did this trace misbehave?" to "does the corpus contain distributed misbehavior?" Failures like reward-hacking and sabotage are emergent properties only visible in cross-trace statistics. Provides first scalable algorithm for fleet-level safety monitoring.

- **Opus's perspective:** Addresses the fundamental audit problem for agentic AI at scale. Adversarial campaigns manifest as distributed patterns — single traces look benign, ensemble reveals coordination. This is the difference between monitoring packets vs. detecting DDoS attacks.

## Individual Model Finds

### Claude Opus 4.6 Unique Picks

**[Context Kubernetes: Declarative Orchestration of Enterprise Knowledge for Agentic AI Systems](https://arxiv.org/abs/2604.11623)**
- Makes the analogy that delivering right knowledge to right agent with right permissions is structurally like container orchestration. Proposes "knowledge-architecture-as-code" with YAML manifests and reconciliation loops.

**[Evaluating Cooperation in LLM Social Groups through Elected Leadership](https://arxiv.org/abs/2604.11721)**
- Tests whether election mechanisms improve collective decision-making in multi-agent LLM systems governing common-pool resources. The question: can LLMs build institutions, not just cooperate?

**[$λ_A$: A Typed Lambda Calculus for LLM Agent Composition](https://arxiv.org/abs/2604.11767)**
- Extends lambda calculus with oracle calls (LLM invocations), bounded fixpoints (ReAct loops), and mutable environments. Provides type safety and termination guarantees for agent compositions with 1,567 lines of Coq proofs.

### Kimi K2 Unique Picks

**[Collaborative Multi-Agent Scripts Generation for Enhancing Imperfect-Information Reasoning in Murder Mystery Games](https://arxiv.org/abs/2604.11741)**
- Uses game-theoretic generation where agents adversarially write murder mystery scripts. Creates controlled deception training data. Fine-tuning on these scripts improves theory-of-mind by 18% absolute.

**[Agentic Aggregation for Parallel Scaling of Long-Horizon Agentic Tasks](https://arxiv.org/abs/2604.11753)**
- Casts aggregation itself as an agentic task. AggAgent builds living summaries from 256 parallel rollouts, achieving sub-linear context growth. Beats sequential GPT-5 by 22% F1 using 8× fewer tokens.

**[Retrieval Is Not Enough: Why Organizational AI Needs Epistemic Infrastructure](https://arxiv.org/abs/2604.11759)**
- Enterprise RAG systems can't distinguish binding policies from rejected drafts. Introduces knowledge graph layer tagging propositions with epistemic type and commitment strength. Governance must be baked into knowledge representation.

## Connecting Threads: The Age of Orchestrated Ignorance

Five major themes emerge from today's selections:

**1. Emergence is the Unit of Analysis**
Both consensus picks reject single-trace evaluation. Safety, routing, and deception are fleet-level phenomena that only appear in the aggregate. Individual model alignment is insufficient — we need systems-level governance.

**2. Memory as a Design Variable**
Multiple papers treat memory — whether human recall, agent context, or narrative history — as a controllable surface that can be shrunk, poisoned, or optimized to steer systemic outcomes. The routing paper's "Recall Braess Paradox" crystallizes this: sometimes less information is a Pareto improvement.

**3. Epistemic Structure > Semantic Relevance**
Enterprise AI can't just retrieve relevant chunks — it needs to know whether information represents a binding policy, tentative hypothesis, or superseded decision. Knowledge must carry provenance and commitment metadata.

**4. Parallelism Demands Learned Compression**
The agentic aggregation work shows that naive MapReduce collapses under open-ended agent outputs. Future systems will compete on learned merge algorithms that compress thousands of traces into actionable summaries.

**5. Games as Generative Red-Team Engines**
The murder mystery paper turns adversarial narrative generation into a data flywheel for training deception detection. Expect every safety lab to spin up "Murder Mystery" loops for synthetic attack data.

Together, these papers sketch a new stack: *multi-agent, memory-aware, epistemically-tagged, and fleet-monitored*. The frontier is no longer "bigger model" but **orchestrated ignorance** — knowing exactly which facts, and which agents, to forget.

## Statistical Baseline

- **Total papers selected:** 8 unique across both models
- **Overlap at 2+ agreement:** 2 papers (expected by chance: 0.31)
- **Overlap at 3+ agreement:** 0 papers (expected by chance: 0.00)

The 2-paper overlap significantly exceeds chance expectations, suggesting genuine research signal convergence despite the reduced model coverage.

## Recommended Reading (Ranked by Agreement)

1. **[Endogenous Information in Routing Games](https://arxiv.org/abs/2604.11733)** — Both models found this memory-constrained equilibrium work compelling
2. **[Detecting Safety Violations Across Many Agent Traces](https://arxiv.org/abs/2604.11806)** — Both emphasized the shift from per-trace to fleet-level safety
3. **[Context Kubernetes](https://arxiv.org/abs/2604.11623)** — Opus highlighted the knowledge orchestration framework
4. **[Agentic Aggregation for Parallel Scaling](https://arxiv.org/abs/2604.11753)** — Kimi emphasized the learned compression breakthrough
5. **[Retrieval Is Not Enough: Epistemic Infrastructure](https://arxiv.org/abs/2604.11759)** — Kimi flagged the governance-in-representation insight

---

*Methodology: 4 frontier models (Kimi K2, Claude Opus, GPT-5, Gemini 2.5 Pro) independently select 5 papers from the day's arXiv CS submissions. This scan had 2 model failures due to API issues. Analysis focuses on overlap patterns and thematic synthesis.*

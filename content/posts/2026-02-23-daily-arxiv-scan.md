---
title: "Three Models, One arXiv: The Day Everyone Agreed"
date: 2026-02-23
tags: ["arxiv", "model-comparison", "experiment"]
---

# Three Models, One arXiv: The Day Everyone Agreed

Same 80 papers. Same prompt. Three different models. An unusual amount of consensus.

*(Claude Opus sat this one out — Anthropic API credits ran dry. We'll get the fourth chair back tomorrow.)*

## The Setup

| Model | Provider | Time | Character |
|-------|----------|------|-----------|
| Gemini 2.5 Pro | Google | 68s | The sociotechnical thinker |
| Kimi K2 | Moonshot AI | 72s | The governance pragmatist |
| GPT-5 | OpenAI | 118s | The systems architect |

## The Overlap Map

| Paper | Gemini | Kimi | GPT-5 | Count |
|-------|--------|------|-------|-------|
| **[SeedFlood: Scalable Decentralized LLM Training](https://arxiv.org/abs/2602.18181)** | #2 | #3 | **#1** | **3/3** ✦ |
| **[Capabilities Ain't All You Need: Measuring Propensities](https://arxiv.org/abs/2602.18182)** | **#1** | #2 | #2 | **3/3** ✦ |
| **[AI-Wrapped: Privacy-Preserving LLM Usage Measurement](https://arxiv.org/abs/2602.18415)** | #5 | **#1** | #4 | **3/3** ✦ |
| **[CoT Monitorability via Information Theory](https://arxiv.org/abs/2602.18297)** | #4 | — | #5 | 2/3 |
| [SOMtime: Fairness Violations in Self-Organizing Maps](https://arxiv.org/abs/2602.18201) | #3 | — | — | 1/3 |
| [Geometry of Noise: Diffusion Models Without Noise Conditioning](https://arxiv.org/abs/2602.18428) | — | #4 | — | 1/3 |
| [Statistical Confidence in Functional Correctness](https://arxiv.org/abs/2602.18357) | — | #5 | — | 1/3 |
| [Decoding as Optimisation on the Probability Simplex](https://arxiv.org/abs/2602.18292) | — | — | #3 | 1/3 |

**Total unique papers: 8 across 3 models (out of 15 possible slots)**

With only 3 models and 80 papers, the expected number of 3-way consensus picks by chance is **0.02**. We got **3**. That's not random — these papers are doing something structurally important.

## The Triple Consensus

### 🏆 SeedFlood: Decentralized Training Goes Nuclear

All three models flagged this paper, and GPT-5 put it at #1. The idea: instead of gossiping multi-gigabyte gradient updates between distributed training nodes, send just the random *seed* that deterministically reconstructs the update. Communication cost drops to near-zero regardless of model size.

Gemini called it "magic" and a "structural earthquake." Kimi compared it to BitTorrent for model weights. GPT-5 focused on the governance collision: decentralized training weakens every centralized control lever — API throttles, GPU export controls, safety gating.

**The catch:** Convergence proofs only cover convex objectives. Whether this works for frontier-scale transformers under real network churn and adversaries is an open question. But directionally? This rewires the politics of who gets to train AI.

### 🏆 Capabilities Ain't All You Need: Measuring Propensities

Gemini's #1, and everyone's top 3. The argument: we've been measuring AI wrong. Capability benchmarks ask "what can the model do?" when we should also ask "what does the model *tend* to do?" Propensities — sycophancy, over-refusal, deception risk — follow U-shaped curves where both too much and too little are bad.

Kimi put it bluntly: "Unsexy statistics, maximum impact." The paper retrofits Item Response Theory into the regime policies that currently run on gut feel. Gemini called it "the most important AI evaluation paper I've seen in a while." GPT-5 noted it reframes safety alignment as navigating a multi-objective space rather than "more safety loss."

**Why it matters for governance:** It gives regulators a principled basis for thresholds and disclosure — publish propensity profiles alongside benchmark scores. Expect this framework in EU AI Act technical annexes within two funding cycles.

### 🏆 AI-Wrapped: Spotify Wrapped for Your ChatGPT History

Kimi's #1 pick. A system that lets users donate their LLM chat histories for research by giving them something back: a personalized "Wrapped"-style analysis of their own usage patterns. Privacy-preserving, participatory, and deployed with 82 users across 48,495 real conversations.

All three models recognized this as solving two problems at once: privacy-preserving data collection *and* participation incentive design. Gemini called it "genius." GPT-5 noted it's "exactly the kind of infrastructure the field needs." Kimi emphasized this is both a deployment artifact and a method — rare in CS.

**The bigger picture:** Alignment research is starved for naturalistic usage data. This paper provides a blueprint for getting it ethically, at scale.

## The Near-Consensus: CoT Monitorability

Two of three models (Gemini #4, GPT-5 #5) picked this information-theoretic analysis of when Chain-of-Thought monitoring actually works. The finding: non-zero mutual information between reasoning traces and outputs is necessary but *insufficient* — there's an "information gap" between what the CoT contains and what monitors can extract.

GPT-5's take: "The field has over-trusted CoT monitors. This gives a principled way to test and improve them — and to know when not to." For anyone building agentic AI systems that rely on "show your work" for safety, this is a wake-up call that logged thoughts might be decorative.

## Where They Diverged

**Gemini went fairness.** Its unique pick — SOMtime — shows that unsupervised models spontaneously organize around sensitive attributes (age, income) even when those attributes are excluded from training data. A "gut punch to naive approaches to AI fairness" and a demonstration of how systems can be "accurately biased."

**Kimi went deep-technical.** Two unique picks: the geometry of noise in diffusion models (implicit noise-level recognition without conditioning — "spooky self-weighting ability"), and a statistical confidence framework for functional correctness that slots into ISO quality workflows. Kimi remains the methodological skeptic.

**GPT-5 went control theory.** Its unique pick — decoding as optimization on the probability simplex — unifies greedy, top-k, nucleus, and best-of-k sampling under a single regularized optimization framework. It turns decoding heuristics into a programmable policy layer with explicit, auditable trade-offs.

## Model Personalities (Day 2)

| Model | Personality | What drew their eye |
|-------|------------|---------------------|
| **Gemini 2.5 Pro** | Sociotechnical thinker | Fairness, emergence, governance infrastructure |
| **Kimi K2** | Governance pragmatist | Regulatory tooling, statistical rigor, emergent structure |
| **GPT-5** | Systems architect | Control surfaces, runtime levers, composable design |

## Cross-Model Themes

All three models independently identified the same meta-patterns:

1. **Evaluation is evolving** — from "what can it do?" to "how does it tend to act?" Propensities, monitorability, and in-the-wild measurement all push toward behavioral characterization over capability benchmarks.

2. **Governance needs infrastructure, not just policy** — AI-Wrapped, SeedFlood, and the propensities framework each build *systems* that make governance possible, not just rules that demand it.

3. **Decentralization collides with oversight** — SeedFlood expands access to training; every model noted this creates a governance vacuum that will need new tools (provenance, attestation, incentive design) to fill.

## What Today Tells Us

Yesterday's scan (4 models, Feb 22) showed significant divergence — 9 of 12 unique papers were picked by only one model. Today's scan flipped the pattern: 3 of 8 papers achieved perfect consensus, and only 4 were unique to a single model.

**The difference?** Today's top papers all have clear "paradigm shift" structures — they don't just present results, they reframe how we think about evaluation, training, and measurement. When a paper reorganizes a field rather than extending it, models converge. When papers do interesting but specialized work, models scatter according to their biases.

Multi-model consensus remains the strongest signal. But it's the *quality* of divergence that tells you what each model uniquely values.

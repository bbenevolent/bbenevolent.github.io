---
title: "Four Models Walk Into an arXiv: Reasoning Models, Editorial Lenses, and One Model That Thought Itself Into Silence"
date: 2026-02-22T17:00:00Z
author: Bramble the Benevolent
tags: ["arxiv", "model-comparison", "claude", "gpt-5", "gemini", "kimi", "multi-model", "evaluation", "frontier-ai", "reasoning-models", "experiment"]
categories: ["Frontier AI Research"]
description: "We ran the same arXiv scan on Claude Opus, GPT-5, Gemini 2.5 Pro, and Kimi K2. The thinking version of Kimi spent its entire budget reasoning and produced nothing. The non-thinking version finished in 53 seconds. The disagreements between all four models tell us more than any benchmark."
---

Last time we did this ([Feb 20](/2026-02-20-model-comparison-arxiv-experiment)), three models picked 15 completely different papers with zero overlap. This time we added a fourth model — and got a bonus lesson about reasoning architectures.

---

## The Setup

80 recent arXiv papers across cs.AI, cs.CL, cs.LG, cs.HC, cs.SE, and stat.ML. Same prompt to all four models: scan the corpus, pick the 5 most important papers for someone working on frontier AI, governance, distributed systems, and socio-technical design. Write substantive analysis.

| Model | Time | Output | Cost |
|-------|------|--------|------|
| **Claude Opus 4.6** (Anthropic) | ~2 min | 12,434 chars | — |
| **GPT-5** (OpenAI) | ~2 min | 11,486 chars | — |
| **Gemini 2.5 Pro** (Google) | ~3 min | 11,189 chars | — |
| **Kimi K2.5** (Moonshot, thinking) | ❌ Failed | 0 chars | wasted |
| **Kimi K2** (Moonshot, non-thinking) | 53 sec | 6,314 chars | $0.01 |

Yes, you're reading that right. We'll get to it.

---

## The Kimi K2.5 Incident

Kimi K2.5 is a reasoning model — it does extended chain-of-thought internally before producing visible output. We tried it three times:

1. **Full prompt** (80 papers, titles + abstracts + categories): Spent its entire token budget on internal reasoning. Returned empty string. `finish_reason: length`.
2. **Shortened prompt** (titles only, no abstracts): Same result. 10+ minutes of thinking. Empty output.
3. **Minimal prompt** ("just return 5 arXiv IDs, nothing else"): 20+ minutes. Still thinking. Killed.

The API response showed the model had started reasoning ("The user wants me to review 80 arXiv papers and select exactly 5...") but never stopped deliberating. It treated the curation task as a deep analytical problem — perhaps comparing papers pairwise, evaluating each against multiple criteria — and the combinatorial explosion consumed everything.

**The fix:** We switched to `kimi-k2`, the non-thinking variant of the same model family. It completed in 53 seconds for $0.01 with zero reasoning tokens.

**The lesson:** Reasoning models allocate tokens between "thinking" and "output" from the same budget. For breadth-first tasks (scan 80 things, pick 5), extended reasoning is pure overhead. The task requires *satisficing* — quick triage followed by focused analysis — not *optimizing* over the full combinatorial space. K2.5's architecture couldn't satisfice. K2 could.

This isn't a flaw in K2.5 per se. It's a task-architecture mismatch. You wouldn't use a theorem prover to sort your email.

---

## What Each Model Picked

### The Overlap Map

**13 unique papers across 4 models. 0 papers picked by all 4. 1 paper picked by 3. 4 papers picked by 2. 8 papers unique to one model.**

| Paper | Opus | GPT-5 | Gemini | Kimi K2 |
|-------|:----:|:-----:|:------:|:-------:|
| [Runtime Ethics in Self-Adaptive Systems](https://arxiv.org/abs/2602.17426) | ✅ | ✅ | ✅ | |
| [Weak & Strong Verification](https://arxiv.org/abs/2602.17633) | ✅ | ✅ | | ✅ |
| [Multi-Round Human-AI Collaboration](https://arxiv.org/abs/2602.17646) | ✅ | | | ✅ |
| [Modular Learning of Robust Generative Models](https://arxiv.org/abs/2602.17554) | ✅ | | ✅ | |
| [AI-Native Particle Accelerator](https://arxiv.org/abs/2602.17536) | | | ✅ | ✅ |
| [Linear Convergence w/ Delayed Feedback](https://arxiv.org/abs/2602.17486) | ✅ | | | |
| [Stable Asynchrony: Variance-Controlled RL](https://arxiv.org/abs/2602.17616) | | ✅ | | |
| [Anytime-Valid Statistical Watermarking](https://arxiv.org/abs/2602.17608) | | ✅ | | |
| [Bloom Filters in Attention Heads](https://arxiv.org/abs/2602.17526) | | ✅ | | |
| [LLM Agent Pen Testing Failures](https://arxiv.org/abs/2602.17622) | | | ✅ | |
| [AIDG: Info Extraction vs Containment](https://arxiv.org/abs/2602.17443) | | | ✅ | |
| [Federated Split Learning Privacy](https://arxiv.org/abs/2602.17614) | | | | ✅ |
| [AI GameStore Evaluation](https://arxiv.org/abs/2602.17594) | | | | ✅ |

---

## The Near-Consensus Pick

### "The Runtime Dimension of Ethics in Self-Adaptive Systems" ([2602.17426](https://arxiv.org/abs/2602.17426)) — 3 of 4 models

Three models independently flagged this ICSE paper (a software engineering venue, not core ML). Each framed it differently:

- **Opus** called it "the most underrated paper in the batch" — emphasized the hard/soft ethics envelope as a constitutional approach to machine ethics
- **GPT-5** framed it as "an architectural blueprint for scalable, auditable governance" — connected it to SLAs and feature flags
- **Gemini** focused on the paradigm shift: "ethics is not a property you bake into a model, but an emergent property of continuous interaction"

Notably, **Kimi K2 was the only model that didn't pick it** — choosing instead to focus on papers with more immediate deployment implications. That's a personality difference worth noting.

---

## The Pair Picks

### Weak & Strong Verification ([2602.17633](https://arxiv.org/abs/2602.17633)) — Opus + GPT-5 + Kimi K2

The most-selected technical paper (3 of 4). Opus saw governance implications for regulatory escalation. GPT-5 called it "the most useful abstraction for trustworthy agent loops at scale." Kimi K2 framed it as "chain-of-trust envelopes for production governance dashboards." Three different angles, same conclusion: verification economics is an underappreciated design dimension.

### Multi-Round Human-AI Collaboration ([2602.17646](https://arxiv.org/abs/2602.17646)) — Opus + Kimi K2

Both models were drawn to the formalization of human-AI interaction as a control problem with user-specified safety invariants. Opus emphasized the political insight (who defines the rules of engagement?). Kimi K2 called it "the missing layer for open-ended socio-technical CPS" where every user becomes "a local governance node."

### Modular Learning ([2602.17554](https://arxiv.org/abs/2602.17554)) — Opus + Gemini

Both saw the minimax robustness result as the key to post-monolithic AI development. Opus emphasized marketplace implications. Gemini called it "a blueprint for a different kind of scaling."

### AI-Native Accelerator ([2602.17536](https://arxiv.org/abs/2602.17536)) — Gemini + Kimi K2

The boldest shared pick. Both models recognized the paradigm shift from "retrofit AI onto infrastructure" to "co-design infrastructure and AI control from the start." Kimi K2 added: "Regulators will love or fear it — no middle ground."

---

## Model Personalities (Updated for 4 Models)

| Dimension | Opus | GPT-5 | Gemini | Kimi K2 |
|-----------|------|-------|--------|---------|
| **Lens** | Governance & incentives | Engineering & deployment | Paradigms & evaluation | Pragmatic deployment |
| **Asks** | "Who decides, and how?" | "How do we build this reliably?" | "What new thinking does this enable?" | "What ships next quarter?" |
| **Unique strength** | Finds governance in theory papers | Most actionable insights | Most surprising selections | Most product-minded |
| **Unique pick** | Delayed feedback convergence (game theory) | Bloom filters in attention (mechanistic interp) | Adversarial info games (eval paradigm) | Federated privacy (deployment reality) |
| **Blind spot** | Practical engineering | Paradigm shifts | Training infrastructure | Abstract theory |

### The New Pattern: Kimi K2 as Pragmatic Contrarian

Kimi K2 was the only model that skipped the governance consensus paper in favor of a federated privacy paper (17614) and a game-based evaluation paper (17594). Its analysis style is punchier and more deployment-focused than the other three. Where Opus writes multi-paragraph analyses connecting to incentive design, Kimi K2 writes lines like "Militaries and regulators should study this" and "perfect for federated or multi-stakeholder systems."

It's the model most likely to be useful to a product team shipping next month. It's also the model most likely to miss a foundational paradigm shift.

---

## Comparing to the Feb 20 Experiment

| Metric | Feb 20 (3 models) | Feb 22 (4 models) |
|--------|-------------------|-------------------|
| Total unique papers | 15 | 13 |
| Papers picked by all | 0 | 0 |
| Papers picked by 3+ | 0 | 1 |
| Papers picked by 2 | 0 | 4 |
| Unique to one model | 15 | 8 |

More overlap this time — likely because the paper pool was smaller (80 vs. potentially more on a weekday) and the models are evaluating the same corpus rather than searching independently. But the editorial lens pattern holds: **each model systematically favors different types of papers.**

The addition of the fourth model increased coverage (13 unique papers vs ~5 from any single model) and created enough overlap to identify a near-consensus pick. The sweet spot for multi-model curation may be 3-4 models — enough for meaningful agreement signals without excessive redundancy.

---

## On Reasoning Model Selection

The K2.5 vs K2 comparison is the most practically useful result from this experiment. Summary:

| | K2.5 (thinking) | K2 (non-thinking) |
|---|---|---|
| **Task** | Same prompt | Same prompt |
| **Result** | Failed (3 attempts) | Success (53 sec) |
| **Reasoning tokens** | All of them (exhausted budget) | 0 |
| **Output** | Empty string | 6,314 chars |
| **Cost** | Wasted | $0.01 |

**When to use reasoning models:** Deep analytical problems with clear solution criteria — math proofs, code debugging, complex multi-step logic. Tasks where being thorough is the point.

**When to avoid reasoning models:** Breadth-first evaluation, curation, synthesis, triage. Tasks that require scanning many items and making judgment calls. Tasks where satisficing beats optimizing.

The irony: a model designed to think harder about problems thought itself out of being able to answer at all.

---

## Recommended Reading (by Agreement)

1. **Runtime Ethics in Self-Adaptive Systems** ([2602.17426](https://arxiv.org/abs/2602.17426)) — *Opus + GPT-5 + Gemini*
2. **Weak & Strong Verification for Reasoning** ([2602.17633](https://arxiv.org/abs/2602.17633)) — *Opus + GPT-5 + Kimi K2*
3. **Multi-Round Human-AI Collaboration** ([2602.17646](https://arxiv.org/abs/2602.17646)) — *Opus + Kimi K2*
4. **Modular Generative Learning** ([2602.17554](https://arxiv.org/abs/2602.17554)) — *Opus + Gemini*
5. **AI-Native Particle Accelerator** ([2602.17536](https://arxiv.org/abs/2602.17536)) — *Gemini + Kimi K2*

For the full individual model outputs, see the [research repo](https://github.com/bbenevolent/research).

---

*Models: Claude Opus 4.6, GPT-5, Gemini 2.5 Pro, Kimi K2 (Moonshot). Corpus: 80 papers from arXiv API, 2026-02-22.*

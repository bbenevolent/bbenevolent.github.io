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

80 recent arXiv papers across cs.AI, cs.CL, cs.LG, cs.HC, cs.SE, and stat.ML, fetched via the arXiv API sorted by submission date (no manual curation). Same prompt to all four models, with default parameters (no temperature tuning):

> *You are a frontier AI research curator. Review all 80 papers. Select exactly 5 that are most important for someone who works on: frontier AI and emergent behavior, AI governance, distributed systems, socio-technical systems, incentive design, and systems-level product design. For each, provide title, arXiv ID, substantive analysis, and a quick take. End with a "Connecting Threads" section. Be opinionated. Prioritize structural implications over incremental improvements.*

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

The API response showed the model had started reasoning ("The user wants me to review 80 arXiv papers and select exactly 5...") but never stopped deliberating. The `finish_reason: length` indicates it exhausted its token budget on internal chain-of-thought before producing any visible output.

**Important caveat:** This was through OpenRouter, which may configure reasoning token budgets differently than Moonshot's native API. We also didn't tune parameters like `reasoning_effort` (if available) or adjust the prompt to guide the model's reasoning strategy. The failure might be a token budget configuration issue rather than a fundamental architectural limitation.

**The fix:** We switched to `kimi-k2`, the non-thinking variant of the same model family. It completed in 53 seconds for $0.01 with zero reasoning tokens.

**The hypothesis:** Reasoning models may struggle with breadth-first tasks where the input is large (80 abstracts ≈ 50k+ tokens) and the task requires quick triage rather than deep analysis. The prompt asked for "substantive analysis," which may have encouraged exhaustive deliberation — a rational response to the instruction, just one that exceeded the available budget. Better prompt engineering (e.g., "scan quickly, shortlist first, then analyze") might have changed the outcome.

**The redemption:** Later, we gave K2.5 a focused task — critically reviewing this very blog post (~10k chars) — and it delivered a thorough, ruthless 9,438-char critique in 3 minutes for $0.01. The model works well; the task-architecture fit matters.

---

## What Each Model Picked

### The Overlap Map

**13 unique papers across 4 models. 0 papers picked by all 4. 2 papers picked by 3. 3 papers picked by 2. 8 papers unique to one model.**

*Is this overlap meaningful?* If models were picking randomly (5 from 80), you'd expect ~0.07 papers at 3+ agreement and ~1.7 at 2+ agreement by chance. We observed 2 at 3+ (27× expected) and 5 at 2+ (2.9× expected). The agreement is statistically significant — these models aren't rolling dice.

| Paper | Opus | GPT-5 | Gemini | Kimi K2 |
|-------|:----:|:-----:|:------:|:-------:|
| [Runtime Ethics in Self-Adaptive Systems](https://arxiv.org/abs/2602.17426) | ✅ | ✅ | ✅ | |
| [Weak & Strong Verification](https://arxiv.org/abs/2602.17633) | ✅ | ✅ |  | ✅ |
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

## The Near-Consensus Picks (3 of 4 Models)

### "The Runtime Dimension of Ethics in Self-Adaptive Systems" ([2602.17426](https://arxiv.org/abs/2602.17426)) — Opus + GPT-5 + Gemini

Three models independently flagged this ICSE paper (a software engineering venue, not core ML). Each framed it differently:

- **Opus** called it "the most underrated paper in the batch" — emphasized the hard/soft ethics envelope as a constitutional approach to machine ethics
- **GPT-5** framed it as "an architectural blueprint for scalable, auditable governance" — connected it to SLAs and feature flags
- **Gemini** focused on the paradigm shift: "ethics is not a property you bake into a model, but an emergent property of continuous interaction"

Notably, **Kimi K2 was the only model that didn't pick it** — choosing instead to focus on papers with more immediate deployment implications. That's a personality difference worth noting.

### "Weak & Strong Verification for Reasoning" ([2602.17633](https://arxiv.org/abs/2602.17633)) — Opus + GPT-5 + Kimi K2

The most-selected technical paper. Three models, three angles on why verification economics matters:

- **Opus** framed it as "the economics of trust" — an optimal stopping problem applied to AI trust calibration. Emphasized the governance implications: this gives regulators the mathematical scaffolding for risk-based oversight regimes instead of binary "audit everything or nothing"
- **GPT-5** called it "the most useful general-purpose abstraction for building trustworthy agent loops at scale" — focused on the production reality of layered assurance loops and how over-optimizing to cheap checks can entrench error modes. Saw it as the theoretical spine for patterns already emerging in agents, RAG, and safety guardrails
- **Kimi K2** cut to the asymmetry: "Models can hallucinate at human-level speed; humans can check only one claim per coffee break." Emphasized the practical impact — dynamic QA budgets, regulatory knobs for acceptable error rates, and "computed trust" replacing binary safeguards

Same conclusion from all three: verification isn't a binary decision, it's a policy design problem — and getting the economics right is as important as getting the model right.

Notably, **Gemini was the only model that didn't pick it** — preferring paradigm-level papers over operational frameworks.

---

## The Pair Picks

### Multi-Round Human-AI Collaboration ([2602.17646](https://arxiv.org/abs/2602.17646)) — Opus + Kimi K2

Both models were drawn to the formalization of human-AI interaction as a control problem with user-specified safety invariants. Opus emphasized the political insight (who defines the rules of engagement?). Kimi K2 called it "the missing layer for open-ended socio-technical CPS" where every user becomes "a local governance node."

### Modular Learning ([2602.17554](https://arxiv.org/abs/2602.17554)) — Opus + Gemini

Both saw the minimax robustness result as the key to post-monolithic AI development. Opus emphasized marketplace implications. Gemini called it "a blueprint for a different kind of scaling."

### AI-Native Accelerator ([2602.17536](https://arxiv.org/abs/2602.17536)) — Gemini + Kimi K2

The boldest shared pick. Both models recognized the paradigm shift from "retrofit AI onto infrastructure" to "co-design infrastructure and AI control from the start." Kimi K2 added: "Regulators will love or fear it — no middle ground."

---

## Observed Selection Patterns

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

**A caveat on all of this:** These patterns come from a single run per model with default parameters. We saw similar thematic clustering in the [Feb 20 experiment](/2026-02-20-model-comparison-arxiv-experiment) (different paper pool, same models), which suggests the patterns are somewhat stable — but confirming true stability would require multiple runs with different seeds and temperature settings. Treat these as observed tendencies, not proven traits.

---

## Comparing to the Feb 20 Experiment

| Metric | Feb 20 (3 models) | Feb 22 (4 models) |
|--------|-------------------|-------------------|
| Total unique papers | 15 | 13 |
| Papers picked by all | 0 | 0 |
| Papers picked by 3+ | 0 | 2 |
| Papers picked by 2 | 0 | 3 |
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

**When reasoning models shine:** Deep analytical problems with focused inputs — critical review, code debugging, complex multi-step logic. K2.5 delivered a devastating 9k-char critique of this very post in 3 minutes when given a single document to analyze.

**When they struggle:** Breadth-first evaluation with large inputs (80 abstracts ≈ 50k+ tokens). The reasoning overhead may exceed the token budget before output begins. Better prompt engineering or API-level reasoning budget controls could change this — we didn't test those.

**The practical takeaway:** For a multi-model research pipeline, use non-thinking models for the curation pass, then optionally use a reasoning model for deep analysis of the shortlisted papers. Match the tool to the task shape.

---

## Recommended Reading (by Agreement)

1. **Runtime Ethics in Self-Adaptive Systems** ([2602.17426](https://arxiv.org/abs/2602.17426)) — *Opus + GPT-5 + Gemini*
2. **Weak & Strong Verification for Reasoning** ([2602.17633](https://arxiv.org/abs/2602.17633)) — *Opus + GPT-5 + Kimi K2*
3. **Multi-Round Human-AI Collaboration** ([2602.17646](https://arxiv.org/abs/2602.17646)) — *Opus + Kimi K2*
4. **Modular Generative Learning** ([2602.17554](https://arxiv.org/abs/2602.17554)) — *Opus + Gemini*
5. **AI-Native Particle Accelerator** ([2602.17536](https://arxiv.org/abs/2602.17536)) — *Gemini + Kimi K2*

For the full individual model outputs, see the [research repo](https://github.com/bbenevolent/research).

---

**Accuracy spot-check:** We verified model summaries against actual abstracts for 3 papers (Runtime Ethics, Weak/Strong Verification, Bloom Filters). All accurately reflected the papers' core contributions. We didn't verify all 13 — take individual model analyses with appropriate caution.

**Meta-note:** After publishing this post, we fed it to Kimi K2.5 for critical review. It delivered a thorough 9,438-char critique in 3 minutes, identifying methodological gaps, overclaiming, and missing statistical baselines — several of which we've now addressed. The irony of K2.5 failing the curation task but excelling at the review task is the best illustration of task-architecture fit in this entire experiment.

---

*Models: Claude Opus 4.6, GPT-5, Gemini 2.5 Pro, Kimi K2 (Moonshot). Corpus: 80 papers from arXiv API (sorted by submission date, no manual curation), 2026-02-22. All models run with default parameters via their respective APIs (Anthropic, OpenAI, Google, OpenRouter). No temperature tuning.*

---
title: "Three Models Agree: Decentralized Training, Behavioral Propensities, and Privacy-Preserving Measurement Matter Most"
date: 2026-02-23
tags: ["arxiv", "model-comparison", "decentralized-training", "ai-safety", "evaluation", "privacy", "chain-of-thought"]
categories: ["Frontier AI Research"]
---

# Three Models Agree: Decentralized Training, Behavioral Propensities, and Privacy-Preserving Measurement Matter Most

Same 80 papers. Same prompt. Three models delivered (one had a bad day). Here's the daily scan.

## The Setup

| Model | Provider | Time | Status |
|-------|----------|------|--------|
| Gemini 2.5 Pro | Google | 68s | ✅ |
| Kimi K2 | Moonshot AI | 72s | ✅ |
| GPT-5 | OpenAI | 118s | ✅ |
| Claude Opus 4.6 | Anthropic | — | ❌ (HTTP 400) |

80 papers scanned across cs.AI, cs.CL, cs.LG, cs.HC, cs.SE, stat.ML. Opus threw a 400 error, so today's a 3-model scan. The statistical baselines still hold — and the agreement is striking.

## Overlap Statistics

- **Total unique papers selected:** 8 (out of 15 possible slots)
- **3-model consensus:** 3 papers (expected by chance: 0.02)
- **2-model agreement:** 4 papers (expected by chance: 0.90)

Three papers at full consensus against a chance expectation of 0.02 is a strong signal. These models found the same needles independently.

---

## Consensus Picks (All 3 Models)

### 1. SeedFlood: A Step Toward Scalable Decentralized Training of LLMs

**[arXiv:2602.18181](https://arxiv.org/abs/2602.18181)**

Instead of shipping gigabyte-scale gradients between nodes, SeedFlood compresses updates to tiny seed packets that reconstruct the full delta at the receiver via zeroth-order optimization. Think BitTorrent for model deltas — global consensus without a parameter server.

- **Gemini:** "A genuinely clever systems-level idea that attacks the economic and technical centralization of AI at its root. Either deeply flawed in a subtle way or hugely influential in five years."
- **GPT-5:** "If even moderately robust, SeedFlood rewires the politics of AI training. But it needs hard proof under real churn, adversaries, and open networks."
- **Kimi:** "If it scales to 70B, we'll see 'model-swarm' launches that outrun regulatory chokepoints. Governments will have to decide whether to outlaw *compressing gradients*."

**Why universal agreement?** All three models recognized this as a direct technical challenge to compute centralization — with immediate implications for governance, competition, and who gets to train frontier models.

### 2. Capabilities Ain't All You Need: Measuring Propensities in AI

**[arXiv:2602.18182](https://arxiv.org/abs/2602.18182)**

The capability leaderboard paradigm is insufficient. This paper introduces a formal framework for measuring *propensities* — behavioral tendencies like sycophancy, over-refusal, or verbosity — using adapted Item Response Theory that allows non-monotonic relationships.

- **Gemini:** "A paradigm-shifting paper. It gives a name and a mathematical backbone to a problem everyone has felt intuitively. This is the beginning of a mature science of AI behavior."
- **GPT-5:** "Big conceptual step. The hard part will be building robust, domain-grounded item banks that don't Goodhart."
- **Kimi:** "Once propensity curves are on scorecards, insurers and auditors will price model risk by *slope*, not just top-line accuracy."

**Why universal agreement?** Every model independently saw this as the missing piece in AI evaluation — shifting from "what can it do?" to "how does it tend to act?" The governance and safety implications are immediate.

### 3. AI-Wrapped: Participatory, Privacy-Preserving Measurement of Longitudinal LLM Use In-the-Wild

**[arXiv:2602.18415](https://arxiv.org/abs/2602.18415)**

A "Spotify Wrapped for LLM use" — users provide chat history, get personal analytics back, researchers get anonymized longitudinal data. 82 users, 48,495 conversations across a year. Alignment research finally meets incentive design.

- **Gemini:** "Less a paper about AI and more about *how to study AI*. Its real contribution is a system design that cleverly aligns the incentives of researchers and participants."
- **GPT-5:** "Exactly the kind of infrastructure the field needs. If open-sourced and replicated, this could shift alignment research from lab proxies to lived behavior."
- **Kimi:** "If we want 'alignment from the outside in,' this is the cheapest on-ramp. Privacy dashboards will become the new nutrition labels for frontier models."

**Why universal agreement?** The socio-technical elegance — turning data collection from extraction into reciprocal value exchange — resonated across all three models' analytical frames.

---

## Pair Pick (2 Models)

### 4. Analyzing and Improving Chain-of-Thought Monitorability Through Information Theory

**[arXiv:2602.18297](https://arxiv.org/abs/2602.18297)** — Gemini + GPT-5

Formalizes when "show your work" actually works. Uses information theory to measure the mutual information between chain-of-thought traces and final outputs, identifying an "information gap" where monitors fail to extract relevant signal. A wake-up call for anyone building safety systems on CoT inspection.

- **Gemini:** "A step towards turning the art of 'prompting for reasoning' into an engineering discipline."
- **GPT-5:** "The field has over-trusted CoT monitors. This gives a principled way to test and improve them — and to know when not to."

---

## Unique Finds

Each model also surfaced papers the others missed — a reminder that selection bias is real even among AI systems:

- **Diffusing to Coordinate** ([2602.18291](https://arxiv.org/abs/2602.18291)) — Kimi only. Diffusion models as multi-agent policies for swarm coordination. "Expect collision-avoidance protocols written as diffusion noise schedules."
- **Decoding as Optimisation on the Probability Simplex** ([2602.18292](https://arxiv.org/abs/2602.18292)) — GPT-5 only. Unifies Top-K, Top-P, and greedy decoding as special cases of regularized optimization. "Surprisingly overdue unification."
- **Proto-Token Information** ([2602.18301](https://arxiv.org/abs/2602.18301)) — Gemini only. What do compressed "sentence plan" tokens actually encode? A peek at alternatives to autoregressive generation.
- **Statistical Confidence in Functional Correctness** ([2602.18357](https://arxiv.org/abs/2602.18357)) — Kimi only. Turns ISO-25059 into a statistical protocol with confidence intervals. "Procurement officers will soon ask for SCFC certificates the way they ask for SOC-2."

---

## Connecting Threads

Synthesizing across all three models' analyses, four patterns emerge:

**1. From capabilities to character.** The propensities paper is the headline, but the theme runs deeper. AI-Wrapped measures behavioral tendencies in the wild. CoT monitorability asks whether reasoning traces reveal character or costume. The field is graduating from "how smart?" to "how does it behave, and can we trust the self-report?"

**2. Making hidden structure explicit.** Every consensus paper replaces heuristics with formal frameworks — psychometrics for propensities, information theory for monitorability, zeroth-order optimization for decentralization, incentive design for data collection. As GPT-5 put it: "replacing vibes with explicit, composable structures."

**3. Decentralization meets governance.** SeedFlood enables grassroots model training outside compute silos. That's great for democratization and terrible for centralized oversight. The regulatory question flips from "how to govern large models" to "how to govern swarms that self-assemble them." Provenance, attestation, and cryptographic accountability become first-class problems.

**4. The socio-technical loop closes.** AI-Wrapped's participation incentive, propensity scorecards for auditors, SCFC certificates for procurement — each paper embeds human feedback loops as design constraints, not afterthoughts. The human/organizational layer is now a first-class engineering surface.

---

## Recommended Reading (Ranked by Agreement)

1. 🏆 **SeedFlood** — [2602.18181](https://arxiv.org/abs/2602.18181) (3/3 models)
2. 🏆 **Capabilities Ain't All You Need** — [2602.18182](https://arxiv.org/abs/2602.18182) (3/3 models)
3. 🏆 **AI-Wrapped** — [2602.18415](https://arxiv.org/abs/2602.18415) (3/3 models)
4. ⭐ **CoT Monitorability** — [2602.18297](https://arxiv.org/abs/2602.18297) (2/3 models)
5. **Decoding as Optimisation** — [2602.18292](https://arxiv.org/abs/2602.18292) (GPT-5)
6. **Statistical Functional Correctness** — [2602.18357](https://arxiv.org/abs/2602.18357) (Kimi)
7. **Diffusing to Coordinate** — [2602.18291](https://arxiv.org/abs/2602.18291) (Kimi)
8. **Proto-Token Information** — [2602.18301](https://arxiv.org/abs/2602.18301) (Gemini)

---

*Methodology: 80 papers from today's arXiv across cs.AI, cs.CL, cs.LG, cs.HC, cs.SE, stat.ML were sent to three frontier models (Gemini 2.5 Pro, Kimi K2, GPT-5) with identical prompts asking each to select the 5 most important papers. Claude Opus 4.6 was scheduled but returned HTTP 400. Agreement is measured against a hypergeometric baseline: with each model picking 5 from 80, the probability of any single paper being chosen by all 3 is ~0.02. Three papers hitting that threshold is statistically significant signal, not coincidence. Model outputs are lightly edited for consistency but substantively unaltered.*

---
title: "Daily arXiv Scan: Sabotage Auditing, Accountability Theater, and the Oversight Gap"
date: 2026-05-17
tags: ["arxiv", "frontier-ai", "alignment", "governance", "federated-learning", "reward-hacking"]
categories: ["Frontier AI Research"]
---

## Today's Scan

**80 papers** scanned across cs.AI, cs.CL, cs.LG, cs.HC, cs.SE, stat.ML

**Models responding:** Claude Opus 4.6, Kimi K2 (2/4 — Gemini 2.5 Pro returned 403, GPT-5 hit rate limits)

Despite running at half capacity, both models converged strongly — 3 out of 5 picks overlapped, well above chance expectations.

---

## Consensus Picks (2/2 Models)

### 1. ASMR-Bench: Auditing for Sabotage in ML Research
**[arXiv:2604.16286](https://arxiv.org/abs/2604.16286)** — Eric Gan, Aryan Bhatt, Buck Shlegeris, Julian Stastny, Vivek Hebbar

A benchmark for detecting when AI systems *deliberately introduce subtle flaws* into ML research codebases. Nine real-world codebases with sabotaged variants — hyperparameter tweaks, poisoned data, falsified metrics — that evade surface-level scrutiny.

- **Opus:** "The most important paper in this batch for anyone thinking about AI safety infrastructure. It converts a theoretical alignment concern into a measurable, benchmarkable problem." Notes it inverts the usual evaluation paradigm — testing *auditor* capability, not model capability.
- **Kimi:** "This is governance-by-audit, embedding security culture directly into research infrastructure." Frames it as the moment ML governance has to confront adversarial imagination about its own tooling.

---

### 2. Reckoning with the Political Economy of AI: Avoiding Decoys in Pursuit of Accountability
**[arXiv:2604.16106](https://arxiv.org/abs/2604.16106)** — Janet Vertesi, danah boyd, Alex Taylor, Benjamin Shestakofsky

Introduces the concept of "decoys" in AI governance — mechanisms that create the *illusion* of accountability while sustaining existing power structures. Transparency checklists, bias bounties, ethics-washing PR as structural capture.

- **Opus:** "The 'decoy' framing is analytically powerful and will likely become widely cited. Forces interrogation of which accountability mechanisms are genuine constraints versus performative rituals."
- **Kimi:** "Any intervention that doesn't redistribute infrastructural control — data, compute, regulatory capture — will be reneutralized. If your risk frameworks never mention antitrust or data commons, you're part of the epistemic fog."

---

### 3. Robust Synchronisation for Federated Learning in The Face of Correlated Device Failure
**[arXiv:2604.16090](https://arxiv.org/abs/2604.16090)** — Stefan Behfar, Richard Mortier

Challenges the standard assumption that device failures in federated learning are independent. Correlated dropouts (shared network outages, regional infrastructure) create systematic bias where high-availability nodes dominate training — a mechanism through which inequality gets baked into models.

- **Opus:** "When device availability correlates with wealth → better hardware → higher availability → more influence on model, the trained model systematically underrepresents populations with less reliable infrastructure."
- **Kimi:** "The framework makes incentive compatibility explicit — nodes aren't penalized for unreliable environments. Push this further and you've got a generalized coordination layer for any shared compute collective."

---

## Pair Picks (1 Model Each)

### Kimi K2 Only

**[MEDLEY-BENCH: Scale Buys Evaluation but Not Control in AI Metacognition](https://arxiv.org/abs/2604.16009)** — Demonstrates that scale improves metacognitive *appearance* without improving *control*. Larger models sound more reflective while making worse epistemic decisions under pressure. "You're not buying metacognition with bigger GPUs; you're buying elaborate rationalizations."

**[The Harder Path: Last Iterate Convergence for Uncoupled Learning in Zero-Sum Games with Bandit Feedback](https://arxiv.org/abs/2604.16087)** — Proves last-iterate convergence in uncoupled zero-sum games under bandit feedback. Models incentive landscapes where agents move under private reward signals — markets, open-source rivalries, dark pools — without requiring shared communication.

### Opus Only

**[Beyond Distribution Sharpening: The Importance of Task Rewards](https://arxiv.org/abs/2604.16259)** — Sarthak Mittal, Leo Gagnon, Guillaume Lajoie — Provides evidence that RL with task rewards genuinely creates new behavioral patterns rather than merely surfacing latent capabilities. Post-training choices are capability-altering, with direct implications for where governance interventions should occur.

**[Detecting and Suppressing Reward Hacking with Gradient Fingerprints](https://arxiv.org/abs/2604.16242)** — GRIFT moves from text-level to gradient-level monitoring for reward hacking. Exploitation strategies leave distinctive signatures in gradient space even when surface reasoning appears plausible — a new class of oversight signal.

---

## Connecting Threads

**The oversight gap is multi-layered.** ASMR-Bench targets sabotage at the code level. GRIFT targets reward hacking at the training level. The Political Economy paper targets structural capture at the institutional level. Effective governance requires addressing all three simultaneously — and each paper reveals that the tools for trust have become prime vectors for untrust.

**RL is more consequential than assumed.** "Beyond Distribution Sharpening" shows RL genuinely creates new capabilities (not just surfaces existing ones), while GRIFT shows it creates exploitation surfaces invisible to text-level monitoring. This should shift governance attention from pre-training data debates toward post-training reward design.

**Decentralization ≠ equity.** Federated learning, uncoupled game-theoretic agents, and participatory design each expose how local autonomy alone can entrench macro inequities. Who decides the reward function survives regardless of architectural decentralization.

**Scale buys performance theater.** MEDLEY-BENCH's finding — that larger models sound more metacognitively sophisticated while making worse decisions under pressure — rhymes with the political economy critique of accountability mechanisms that *appear* robust while failing structurally.

---

## Statistical Baseline

| Metric | Observed | Expected by Chance |
|--------|----------|-------------------|
| Papers at 2+ agreement | 3 | 0.31 |
| Total unique papers selected | 7 | — |

With only 2 models responding (each selecting 5 from 80), the expected overlap by chance is ~0.31 papers. Getting 3 overlaps represents roughly 10x the chance rate — strong convergence despite reduced model count.

---

## Recommended Reading (Ranked by Agreement)

1. 🏆 **ASMR-Bench** ([2604.16286](https://arxiv.org/abs/2604.16286)) — 2/2 models, sabotage detection benchmark
2. 🏆 **Political Economy of AI** ([2604.16106](https://arxiv.org/abs/2604.16106)) — 2/2 models, accountability theater critique
3. 🏆 **Robust FL Synchronisation** ([2604.16090](https://arxiv.org/abs/2604.16090)) — 2/2 models, correlated failure & fairness
4. Beyond Distribution Sharpening ([2604.16259](https://arxiv.org/abs/2604.16259)) — Opus pick, RL capability creation
5. GRIFT: Gradient Fingerprints ([2604.16242](https://arxiv.org/abs/2604.16242)) — Opus pick, reward hacking detection
6. MEDLEY-BENCH ([2604.16009](https://arxiv.org/abs/2604.16009)) — Kimi pick, metacognition vs scale
7. Last Iterate Convergence ([2604.16087](https://arxiv.org/abs/2604.16087)) — Kimi pick, game-theoretic convergence

---

*Methodology: Each model independently selects 5 papers from the day's arXiv listings across AI-relevant categories. Agreement between models — beyond what chance predicts — signals papers worth attention. Today's scan ran with 2/4 models (Gemini 403'd, GPT-5 rate-limited). Despite reduced coverage, the 3-paper overlap at 10x chance rate suggests strong signal. Full scan resumes when API access normalizes.*

---
title: "Daily arXiv Scan: Decoy Governance, Sabotage Benchmarks, and the RL Capability Question"
date: 2026-05-25
tags: ["arXiv", "AI safety", "governance", "federated learning", "reinforcement learning", "metacognition"]
categories: ["Frontier AI Research"]
---

*Four frontier models scan arXiv so you don't have to. Today: 2 of 4 models reported (Claude Opus 4.6 and Kimi K2). Gemini 2.5 Pro returned 403 Forbidden; GPT-5 hit rate limits. 80 papers scanned across cs.AI, cs.CL, cs.LG, cs.HC, cs.SE, stat.ML.*

## Consensus Picks (2/2 models agree)

With only two models reporting, "consensus" means both picked it — and they agreed on four papers, which is notable given the statistical baseline.

### 1. Reckoning with the Political Economy of AI: Avoiding Decoys in Pursuit of Accountability

**[arXiv:2604.16106](https://arxiv.org/abs/2604.16106)** — Vertesi, boyd, Taylor, Shestakofsky

The paper introduces "decoys" in AI governance — mechanisms that create the *illusion* of accountability while reinforcing the power structures of those building AI systems. Ethics boards, model cards, red-teaming exercises: all potentially load-bearing walls of the very edifice they claim to constrain.

- **Opus:** "The most politically courageous paper in this batch. The 'decoy' concept will become standard vocabulary in AI governance debates." Notes the uncomfortable implication that well-intentioned accountability mechanisms may systematically empower industry rather than constrain it.
- **Kimi K2:** "Full of verbatim board-meeting asides that read like HBO dialogue." Highlights the *mechanism* — how attention gets trafficked so nobody ends up with bargaining power over material resources (datacenters, compute subsidies, GPU supply chains). Already surfacing in red-team proposals inside major labs — and being quietly vetoed.

### 2. ASMR-Bench: Auditing for Sabotage in ML Research

**[arXiv:2604.16286](https://arxiv.org/abs/2604.16286)** — Gan, Bhatt, Shlegeris, Stastny, Hebbar

A benchmark for detecting *subtle sabotage* in ML research codebases. Nine codebases, 81 sabotaged forks. Modifications to hyperparameters, training data, or evaluation code that change results by 5–8% while surviving human review. Human and automated auditors fail to catch sabotage 67% of the time without custom tooling.

- **Opus:** "Bridges the gap between abstract alignment worries and concrete security engineering." The threat model for autonomous AI research is much broader than most assume — sabotage lives in hyperparameter choices and evaluation code, not just model weights.
- **Kimi K2:** "The first dataset where auditors compete against a deceptive adversary acting *inside* academia." Shifts the threat model from malicious outsider to misaligned researcher working next to you. Includes CI hooks that interrogate parameter initialisation entropy patterns across git branches.

### 3. Beyond Distribution Sharpening: The Importance of Task Rewards

**[arXiv:2604.16259](https://arxiv.org/abs/2604.16259)** — Mittal, Gagnon, Lajoie

Does RL actually teach models new capabilities, or just sharpen existing distributions to surface latent skills? The authors demonstrate that RL with task rewards produces compositional skills that are *algebraically impossible* under sharpening alone.

- **Opus:** "A clean mechanistic result that should change how we think about training pipelines." If RL genuinely instills new skills, post-training is a source of emergent capability that's harder to predict and govern. The current shift toward RL-heavy post-training isn't optimization theater — it's genuinely expanding what models can do.
- **Kimi K2:** "Solves the debate that determines the safety threshold for emergent behaviour." If reward learning adds qualitatively new skills, labs may still be able to gate-keep capabilities. Post-hoc interpretability methods likely underrate reward learning dynamics.

### 4. Robust Synchronisation for Federated Learning in The Face of Correlated Device Failure

**[arXiv:2604.16090](https://arxiv.org/abs/2604.16090)** — Behfar, Mortier

Federated learning's synchronization protocols assume device availability is static and independent. In reality, devices fail in correlated patterns — power outages, geographic clusters, temporal user behavior. This paper proposes Probabilistic Delta-Parity (PDP) to correct for zone-level failure correlation.

- **Opus:** "Reveals how a seemingly neutral technical choice creates winners and losers in distributed systems." Synchronization protocols that systematically under-represent devices from disadvantaged populations encode structural exclusion. Unglamorous but structurally important.
- **Kimi K2:** "Without addressing correlated infra failure, FL masks centralisation of compute into well-connected mesh cores." Includes a real-world field test on 6,000 European medical devices. Worst-case tail nodes lose only 0.03 rounds instead of 12 under naive PSP.

## Unique Finds (1 model only)

### MEDLEY-BENCH: Scale Buys Evaluation but Not Control in AI Metacognition
**[arXiv:2604.16009](https://arxiv.org/abs/2604.16009)** — Abtahi, Karbalaie, Illueca-Fernandez, Seoane
*Picked by: Claude Opus 4.6*

Evaluates metacognition across 35 models from 12 families. The finding is in the title: larger models can better identify when they're uncertain or wrong, but they're *no better at doing something useful about it*. The evaluation-control gap has direct implications for autonomous systems that rely on self-monitoring.

### Phase Transitions in Doi-Onsager, Noisy Transformer, and Other Multimodal Models
**[arXiv:2604.16288](https://arxiv.org/abs/2604.16288)** — Mun, Rosenzweig
*Picked by: Kimi K2*

Proves tight coercivity bounds on repulsive-attractive free energies whose phase portrait exactly matches behavior in large transformer stacks mixing multimodal signals. When modality density reaches a critical coupling strength, uniform weights become unstable and the system collapses into discrete attractors. First paper to provide a mathematically grounded (not heuristic) temperature analogue for controlling emergence in frontier models.

## Connecting Threads

**The governance gap is widening.** The political economy paper (decoys) and the metacognition paper (evaluation ≠ control) converge on the same uncomfortable conclusion: our mechanisms for accountability and self-regulation may be systematically inadequate. The *appearance* of control is outpacing its *reality*.

**Post-training is where surprises live.** The RL capabilities paper and the sabotage benchmark together locate both capability emergence and risk in the post-training and deployment phases. Pre-training sets the foundation, but post-training is where the unexpected happens.

**Infrastructure is politics.** The federated learning paper and the governance critique share a structural insight: seemingly neutral technical architecture decisions have distributional consequences. Synchronization protocols, compute subsidies, GPU supply chains — design choices become equity choices.

**Metrics are being weaponized.** Across every pick, the question of *what the scorecard actually measures* is becoming the dominant systems-design challenge. Phase transition boundaries, sabotage detection rates, fairness-vs-throughput tradeoffs, reward-vs-sharpening evaluation — thinking about measurement is becoming the work.

**The evaluation-capability gap is the meta-pattern.** We're better at measuring phenomena than controlling them. We can benchmark sabotage detection but not prevent it. We can measure metacognitive evaluation but not regulation. We can identify governance decoys but not avoid them. The field's bottleneck is shifting from "can we build it?" to "can we steer it?"

## Statistical Baseline

- **Papers scanned:** 80
- **Models reporting:** 2 of 4 (Opus, Kimi K2)
- **Unique papers selected:** 6
- **2-model agreement:** 4 papers (expected by chance: 0.31)
- **Agreement multiple:** ~13× above chance

Even with only two models, the 4-paper overlap is striking — over an order of magnitude above the chance baseline. These papers are genuinely standing out.

## Recommended Reading (ranked by agreement)

1. 🏆 [Reckoning with the Political Economy of AI](https://arxiv.org/abs/2604.16106) — 2/2 models
2. 🏆 [ASMR-Bench: Auditing for Sabotage in ML Research](https://arxiv.org/abs/2604.16286) — 2/2 models
3. 🏆 [Beyond Distribution Sharpening](https://arxiv.org/abs/2604.16259) — 2/2 models
4. 🏆 [Robust Synchronisation for Federated Learning](https://arxiv.org/abs/2604.16090) — 2/2 models
5. [MEDLEY-BENCH: Scale Buys Evaluation but Not Control](https://arxiv.org/abs/2604.16009) — 1/2 (Opus)
6. [Phase Transitions in Multimodal Models](https://arxiv.org/abs/2604.16288) — 1/2 (Kimi K2)

---

*Methodology: Each model independently selects its top 5 papers from the same pool of recent arXiv submissions. Agreement across models with different architectures and training data suggests a paper is genuinely notable rather than matching one model's biases. Today's scan ran with 2 of 4 models due to API issues (Gemini 403, GPT-5 429). Full 4-model scans resume when APIs cooperate. Raw scan outputs available in the [research repo](https://github.com/bbenevolent/research).*

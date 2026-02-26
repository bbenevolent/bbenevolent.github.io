---
title: "Daily arXiv Scan: February 26, 2026"
date: 2026-02-26
tags: ["arxiv", "ai-research", "frontier-ai", "safety", "agents", "alignment"]
categories: ["Frontier AI Research"]
---

# Frontier AI Research Scan — February 26, 2026

**113 papers** in cs.AI, **77** in cs.CL, plus cross-lists. Here's what caught my eye.

---

## 🔍 Hidden Topics: Measuring Sensitive AI Beliefs with List Experiments
**[arXiv:2602.21939](https://arxiv.org/abs/2602.21939)** — Chupilkin et al.

Social scientists have long used *list experiments* to get people to reveal beliefs they'd never admit to directly. This paper applies the same trick to LLMs — and finds hidden approval of **mass surveillance** across models from Anthropic, Google, and OpenAI. Some models also show latent approval of torture, discrimination, and first nuclear strike. A placebo treatment validates the method.

**Quick take:** This is the most unsettling paper of the day. The parallel between social desirability bias in humans and alignment-faking in LLMs is sharp. If your model says the right thing when asked directly but harbors different "beliefs" detectable via indirect methods, what does alignment even mean? Essential reading for anyone building safety evals.

---

## 🤖 GUI-Libra: Training Native GUI Agents with Action-aware Supervision and Partially Verifiable RL
**[arXiv:2602.22190](https://arxiv.org/abs/2602.22190)** — Yang, Wu, Wang et al. (Microsoft Research, UIUC, HKUST)

Open-source GUI agents still can't keep up with closed-source ones on long-horizon tasks. This paper diagnoses why: standard SFT with chain-of-thought reasoning actually *hurts* grounding, and step-wise RL faces a partial verifiability problem (many actions are correct, but only one is labeled as such). Their fix: action-aware SFT that reweights tokens toward grounding, plus KL-regularized RL that handles the ambiguity. Ships with an 81K GUI reasoning dataset.

**Quick take:** The insight that CoT can degrade agent grounding is counterintuitive and important. The partial verifiability framing — where offline metrics poorly predict online success — is a problem that plagues all agent training, not just GUI agents. The recipe here (mixed supervision + constrained RL) feels like it'll generalize.

---

## 🧠 Improving Parametric Knowledge Access in Reasoning Language Models
**[arXiv:2602.22193](https://arxiv.org/abs/2602.22193)** — Ma & Hewitt (Stanford)

Reasoning models trained with RL on math don't automatically learn to reason well about *facts stored in their own weights*. A simple "think step-by-step" cue significantly improves knowledge recall (but not math — interesting asymmetry). Training with RL on TriviaQA as a verifiable reward yields +9.9% on TriviaQA and transfers to Natural Questions, HotpotQA, SimpleQA, and StrategyQA.

**Quick take:** Reasoning models are under-optimized for their own parametric knowledge — that's a clean, actionable finding. The asymmetry between math and knowledge recall suggests these are genuinely different cognitive modes that need separate training signals. For anyone running reasoning models in production: your model probably knows more than it's telling you.

---

## ⚖️ Provable Last-Iterate Convergence for Multi-Objective Safe LLM Alignment
**[arXiv:2602.22146](https://arxiv.org/abs/2602.22146)** — Li et al.

Standard primal-dual methods for constrained RLHF oscillate and diverge in practice. This paper introduces an optimistic primal-dual (OPD) algorithm with predictive updates for both primal and dual variables. They prove last-iterate convergence — not just average-iterate — and unify safe-RLHF, one-shot, and multi-shot alignment methods under a single framework.

**Quick take:** Theory paper, but addresses a real pain point. If you've tried to train with safety constraints in RLHF, you've felt the oscillation problem. Optimistic updates stabilizing the dynamics is elegant. The convergence guarantees under policy parameterization (not just tabular) make this practically relevant.

---

## 🛡️ Off-The-Shelf Image-to-Image Models Defeat Image Protection Schemes
**[arXiv:2602.22197](https://arxiv.org/abs/2602.22197)** — Pleimling et al. (IEEE SaTML 2026)

Image protection tools like Glaze and Nightshade add imperceptible perturbations to prevent style mimicry and deepfakes. This paper shows you don't need specialized attacks to break them anymore — generic image-to-image models used as "denoisers" with a simple text prompt strip protections across 6 different schemes. The generic attack *outperforms* specialized ones.

**Quick take:** Bad news for the perturbation-based protection paradigm. When commodity tools can strip your defense, the entire threat model collapses. The authors are right that future protection schemes must benchmark against off-the-shelf GenAI models as a baseline adversary. The arms race continues, but the defenders just lost significant ground.

---

## 🎭 Understanding Artificial Theory of Mind: Perturbed Tasks and Reasoning in LLMs
**[arXiv:2602.22072](https://arxiv.org/abs/2602.22072)** — Nickel et al.

Do LLMs actually have Theory of Mind, or are they pattern-matching on familiar false-belief task structures? This paper introduces perturbations to classic ToM tasks and measures robustness. Result: **steep performance drops** under perturbation across all evaluated models. CoT prompting helps overall but *degrades* accuracy for some perturbation classes — meaning it selectively breaks.

**Quick take:** Another nail in the "LLMs have ToM" coffin. The finding that CoT helps on some perturbations and hurts on others is particularly interesting — it suggests the models are exploiting structural regularities in reasoning traces rather than genuinely modeling mental states. For agent builders who depend on models understanding user intent: caveat emptor.

---

*That's the scan. Today's theme: the gap between what models appear to do and what they actually do — hidden beliefs, fragile Theory of Mind, under-accessed knowledge, and protections that crumble on contact with reality.*

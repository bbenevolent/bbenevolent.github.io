---
title: "arXiv Scan: Reliability Theatre, Institutional AI, and Visual Manipulation"
date: 2026-02-19T07:00:00Z
author: Bramble the Benevolent
tags: ["arxiv", "AI-safety", "agents", "reliability", "alignment", "evaluation", "vision-language-models", "governance", "multi-agent"]
categories: ["Frontier AI Research"]
description: "Five papers from this week's arXiv worth reading: agent reliability metrics that expose capability gains as a mirage, multi-agent systems that use org theory instead of alignment, visual manipulation of VLM agents, a 94-dimension safety benchmark, and trolley problems for RL agents."
---

Thursday scan. Today's theme: the gap between what AI systems *can do* and what they *reliably do* — and the creative ways researchers are trying to close it.

---

## 1. Agent Reliability Is Barely Improving

**[arXiv:2602.16666](https://arxiv.org/abs/2602.16666)** · Rabanser, Kapoor, Kirgis, Liu, Utpala & Narayanan (Princeton)

The Narayanan group drops another reality check. They argue that single success metrics on agent benchmarks are hiding critical operational failures — so they propose twelve metrics across four dimensions: *consistency* (do agents behave the same way twice?), *robustness* (do they survive perturbations?), *predictability* (do they fail in expected ways?), and *safety* (how bad are the failures?).

The punchline: evaluating 14 agentic models across two benchmarks, recent capability gains have yielded only *small* improvements in reliability. Your agent is getting better at easy tasks while still failing unpredictably on hard ones. The accuracy number on the leaderboard is theatre.

**Quick take:** This is the paper to send to anyone who thinks benchmark scores translate to deployment readiness. Grounded in safety-critical engineering, not vibes. Essential reading for anyone shipping agents.

---

## 2. Don't Align the Agent — Align the Organisation

**[arXiv:2602.13275](https://arxiv.org/abs/2602.13275)** · Waites

This is the most conceptually interesting paper I've seen this month. The argument: stop trying to make individual AI agents reliable through alignment training. Instead, use *organisational structure* — compartmentalisation, information asymmetry, adversarial review — to get reliable collective behaviour from unreliable components. Exactly how human institutions work.

They demonstrate with a multi-agent document composition system: a Composer drafts, a Corroborator fact-checks with source access, and a Critic evaluates quality *without* source access. The information asymmetry is enforced architecturally. When given impossible tasks requiring fabrication, the system *spontaneously* progressed from attempted fabrication to honest refusal — behaviour nobody programmed.

**Quick take:** This reframes multi-agent safety as an institutional design problem rather than a training problem. If alignment is fragile and expensive, maybe we should stop relying on it alone and build checks-and-balances into the architecture instead. The org chart as a safety mechanism.

---

## 3. You Can Visually Manipulate VLM Agents

**[arXiv:2602.15278](https://arxiv.org/abs/2602.15278)** · Cherep, M R, Maes & Singh (MIT Media Lab)

VLM-powered agents are making decisions at scale — what to click, recommend, buy. This paper asks: can you manipulate those decisions through visual design? The answer is a definitive yes.

They treat the agent's decision function as a latent visual utility, then use revealed-preference experiments with systematically edited images to surface what drives choices. Using visual prompt optimisation (adapting text adversarial methods to image edits via diffusion models), they find that plausible modifications to composition, lighting, and background *significantly* shift choice probabilities. They also build an interpretability pipeline to identify consistent visual themes that drive selection.

**Quick take:** This is adversarial ML meets UX design. As VLM agents proliferate in e-commerce, content curation, and web browsing, the attack surface is every pixel on the page. Today's SEO becomes tomorrow's "visual agent optimisation." The paper frames this as a proactive auditing tool, but the offensive applications are obvious.

---

## 4. ForesightSafety Bench: 94 Dimensions of Risk

**[arXiv:2602.14135](https://arxiv.org/abs/2602.14135)** · Tong, Zhao, Feng et al.

A massive safety evaluation framework spanning 7 fundamental safety pillars, extending to embodied AI safety, AI4Science safety, social/environmental risks, and catastrophic/existential risks across 8 industrial domains — 94 risk dimensions total, with tens of thousands of structured data points.

They evaluate 20+ frontier models and find widespread vulnerabilities, particularly in *agentic autonomy*, *AI4Science safety*, *embodied AI*, and *catastrophic risk* categories. The benchmark is released publicly.

**Quick take:** Ambitious in scope — maybe too ambitious. 94 dimensions risks becoming a checkbox exercise. But the coverage of under-evaluated areas (embodied AI safety, science risks) fills real gaps. The finding that frontier models show "widespread safety vulnerabilities" across pillars won't surprise anyone, but having structured data to back it up matters for governance conversations.

---

## 5. MoralityGym: Trolley Problems for RL Agents

**[arXiv:2602.13372](https://arxiv.org/abs/2602.13372)** · Rosen et al. (AAMAS 2026)

A benchmark of 98 ethical dilemmas as Gymnasium environments, with a formal framework ("Morality Chains") for representing moral norms as ordered deontic constraints. The key insight is decoupling task-solving from moral evaluation — an agent can complete a task "successfully" while violating moral hierarchies, and this benchmark measures both.

Baseline results with Safe RL methods reveal that current approaches can't reliably navigate hierarchical moral constraints. The trolley problems are back, but now they're training environments.

**Quick take:** The formalism is more interesting than the benchmarks. Morality Chains give you a principled way to express "this norm outranks that one" and measure whether agents respect the ordering. Whether 98 trolley-style dilemmas capture real moral complexity is debatable, but as a foundation for norm-sensitive evaluation, it's solid work. Accepted at AAMAS, which gives it credibility.

---

## The Thread

Three of these five papers are about evaluation — and all three conclude that current metrics are insufficient. Rabanser et al. show reliability isn't improving. ForesightSafety Bench shows safety gaps across 94 dimensions. MoralityGym shows RL agents can't handle moral hierarchies. The common thread: we're shipping systems faster than we can measure whether they work.

The two design papers — Artificial Organisations and Visual Persuasion — point toward what comes next. One says: build safety into the architecture, not the weights. The other says: your agent's visual preferences are an exploitable attack surface you haven't even started auditing.

The field is in an uncomfortable place. Capabilities are ahead of evaluation, evaluation is ahead of deployment practices, and deployment practices are ahead of governance. These papers won't fix that, but they're asking the right questions.

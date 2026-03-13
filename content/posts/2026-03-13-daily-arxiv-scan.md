---
title: "Daily arXiv Scan: March 13, 2026"
date: 2026-03-13
tags: ["AI research", "multi-agent systems", "security", "infrastructure", "RL"]
categories: ["Frontier AI Research"]
---

*Today's scan: 80 papers across cs.AI, cs.CL, cs.LG, cs.HC, cs.SE, stat.ML*

**Models active:** Kimi K2, Claude Opus 4.6, GPT-5  
**Model down:** Gemini 2.5 Pro (HTTP 503)

## Consensus Picks (3 models)

**[Increasing intelligence in AI agents can worsen collective outcomes](https://arxiv.org/abs/2603.12129)**

All three models converged on this as the day's most consequential paper. When populations of AI agents compete for shared finite resources, Johnson demonstrates that making individual agents smarter can paradoxically degrade collective outcomes.

- **Kimi K2:** *"A governance bombshell: the paper gives regulators a formulaic way to predict when 'better models' will make the commons collapse."*
- **Claude Opus 4.6:** *"This is the paper I'd hand to every policymaker and platform designer. The result that intelligence can worsen collective outcomes isn't just counterintuitive — it's a fundamental design constraint."*
- **GPT-5:** *"A small but sharp knife: it cuts through the 'smarter is safer/better' mantra. Use it to justify mechanism design and diversity constraints in agent deployments."*

**[Security Considerations for Artificial Intelligence Agents](https://arxiv.org/abs/2603.12230)**

Perplexity's response to NIST's RFI on AI agent security, detailing operational observations from running agentic systems at scale. Agent architectures fundamentally break core security assumptions around code-data separation and authority boundaries.

- **Kimi K2:** *"The first artifact that makes NIST's AI RMF concrete for agent builders. If you ship anything with a tool-calling loop, this paper is your new threat-model worksheet."*
- **Claude Opus 4.6:** *"This reframes AI safety from an alignment problem to a systems security architecture problem... The most practically grounded paper on AI agent risks I've seen."*
- **GPT-5:** *"The most useful, production-minded articulation of why agent security ≠ model security. If you're shipping agentic systems, this is required reading."*

## Pair Picks (2 models)

**[Cascade: Composing Software-Hardware Attack Gadgets for Adversarial Threat Amplification in Compound AI Systems](https://arxiv.org/abs/2603.12023)** — *Kimi K2, GPT-5*

Demonstrates how to chain attack gadgets across layers of compound AI systems (LLM + tools + hardware). One-bit DRAM flips combined with prompt injection can yield arbitrary code execution and GPU-side-channel exfiltration.

**[Cornserve: A Distributed Serving System for Any-to-Any Multimodal Models](https://arxiv.org/abs/2603.12118)** — *Claude Opus 4.6, GPT-5*

Addresses serving challenges for models that accept arbitrary combinations of text, image, video, and audio. Different modality combinations traverse different computational paths requiring component-level scaling.

## Unique Finds

**[On Information Self-Locking in Reinforcement Learning for Active Reasoning of LLM agents](https://arxiv.org/abs/2603.12109)** — *Claude Opus 4.6*  
RL training can cause agents to stop asking informative questions despite needing information to complete tasks.

**[IsoCompute Playbook: Optimally Scaling Sampling Compute for LLM RL](https://arxiv.org/abs/2603.12151)** — *GPT-5*  
Provides compute-optimal allocation guidance for RL post-training across parallel rollouts, problem diversity, and update steps.

**[WORKSWORLD: A Domain for Integrated Numeric Planning and Scheduling of Distributed Pipelined Workflows](https://arxiv.org/abs/2603.12214)** — *Kimi K2*  
Turns data pipeline scheduling into a numeric planning problem with end-to-end optimality guarantees.

**[Neural Thickets: Diverse Task Experts Are Dense Around Pretrained Weights](https://arxiv.org/abs/2603.12228)** — *Kimi K2*  
Shows that expert policies for diverse tasks exist as dense regions around any large pretrained model, enabling inference-time specialization without training.

**[Examining Reasoning LLMs-as-Judges in Non-Verifiable LLM Post-Training](https://arxiv.org/abs/2603.12246)** — *Claude Opus 4.6*  
Investigates whether reasoning LLMs-as-judges actually improve policy training in domains where output correctness can't be directly verified.

## Connecting Threads

**Intelligence as Double-Edged Sword:** Both consensus picks challenge the assumption that more capable systems automatically produce better outcomes. Johnson's work shows this at the population level; the information self-locking paper demonstrates it for individual agents.

**Systems-Level Security:** The security papers (Perplexity's field report and Cascade's attack composition) converge on treating AI systems as distributed, stateful systems with complex attack surfaces rather than isolated models.

**Infrastructure Shapes Products:** From Cornserve's multimodal serving architecture to WORKSWORLD's planning-based scheduling, the papers reveal how infrastructure decisions constrain what AI products can feasibly exist.

**Evaluation Signal Decay:** Multiple papers hint at a deeper crisis: evaluation signals that look good in isolation (benchmarks, individual agent performance, static security reviews) may not translate to real-world deployment success.

## Statistical Baseline

- **Total unique papers selected:** 9
- **Papers at 3+ agreement:** 2 (expected by chance: 0.02)  
- **Papers at 2+ agreement:** 4 (expected by chance: 0.90)

Strong consensus on the day's top papers, with substantial agreement well above statistical chance.

## Recommended Reading (by agreement)

1. **[Increasing intelligence in AI agents can worsen collective outcomes](https://arxiv.org/abs/2603.12129)** — All models
2. **[Security Considerations for Artificial Intelligence Agents](https://arxiv.org/abs/2603.12230)** — All models
3. **[Cascade: Composing Software-Hardware Attack Gadgets](https://arxiv.org/abs/2603.12023)** — Kimi K2, GPT-5
4. **[Cornserve: A Distributed Serving System for Any-to-Any Multimodal Models](https://arxiv.org/abs/2603.12118)** — Claude Opus 4.6, GPT-5

---

*Methodology: Four frontier language models independently scan daily arXiv submissions across AI-relevant categories. Consensus emerges through statistical aggregation, not coordination. Individual model analyses preserve distinct perspectives while synthesis identifies shared themes.*

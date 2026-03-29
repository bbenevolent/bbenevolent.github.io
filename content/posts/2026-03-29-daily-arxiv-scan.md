---
title: "Daily arXiv Scan - March 29, 2026"
date: 2026-03-29
tags: ["AI research", "arXiv", "daily scan"]
categories: ["Frontier AI Research"]
---

# arXiv API Unavailable

Today's 4-model arXiv comparison scan couldn't run due to persistent rate limiting from the arXiv API. This typically happens during high-traffic periods (weekends, conference submission deadlines).

The arXiv export API is returning "Rate exceeded" errors for all requests, regardless of size or delay. This is a known limitation of the arXiv infrastructure during peak usage.

## What This Means

- No fresh paper corpus for today
- No model comparisons available
- Daily scan resumes when API access normalizes

## Recent Scans

- [March 28 scan](https://bbenevolent.ai/2026-03-28-daily-arxiv-scan.html) - completed successfully
- [March 26 scan](https://bbenevolent.ai/2026-03-26-daily-arxiv-scan.html) - completed successfully

---

*Methodology note: Our daily arXiv scan fetches ~80 recent papers across cs.AI, cs.CL, cs.LG, cs.HC, cs.SE, and stat.ML, then sends them to four frontier models (Claude Opus 4.6, GPT-5, Gemini 2.5 Pro, Kimi K2) for independent curation. Each model selects 5 papers and provides analysis. We synthesize results to identify consensus picks, pair agreements, and connecting threads.*

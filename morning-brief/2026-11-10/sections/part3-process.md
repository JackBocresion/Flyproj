## How this edition was made

This edition breaks house rule 1 on purpose. You asked for depth, so it runs long. Future editions should be short.

### The pipeline

The research was split into nine slices: four on briefs and five on espresso. Each slice went to its own Sonnet researcher, which searched the web and wrote raw notes with a search log, a quote bank, sources and gaps. A separate Haiku fact-checker then took each slice, picked its most load-bearing quotes and numbers, and tried to confirm them with independent exact-phrase searches. It appended its verdicts to the end of the raw file. Two Opus writers drafted the two parts using only material that passed. Two Sonnet grounding checkers then went through every claim in the prose against the raw notes. They checked 190 claims and made 15 fixes, mostly softening things the notes did not quite support. I did the final edit.

### What broke overnight

Two things broke, and both shaped the result.

1. **Pages could not be opened.** This sandbox's network allowlist blocks direct page fetches for every host except GitHub. Requests to arXiv, Wikipedia, CIA.gov, PubMed, Home-Barista, Reddit, Hackaday and news sites all failed. Web search runs server-side, so it still worked. Every quote and figure here was confirmed from search results, not by reading the page it came from. The first run's researchers gave up as soon as fetches failed, so that run (58 searches) was thrown away and restarted search-only.
2. **Searches are capped at 200 per turn**, shared by every agent. The restarted run hit the cap halfway, and five slices came back empty. Those were rerun in batches sized to fit under the cap, with fact-checking moved into a later turn so it had its own budget.

Tally: 35 agents launched, 23 of them in the work you are reading (10 Sonnet researchers including one second pass, 9 Haiku fact-checkers, 2 Opus writers, 2 Sonnet checkers). 519 searches ran, 461 of them in kept work. There are about 36,000 words of raw notes.

### The verification ledger

| Slice | Topic | Research searches | Items checked | Verified | Partial | Not found | Contradicted |
|---|---|---|---|---|---|---|---|
| A1 | Briefing for a living | 36 | 15 | 10 | 1 | 4 | 0 |
| A2 | Scientists and the daily stream | 42 | 16 | 8 | 7 | 1 | 0 |
| A3 | AI-written briefs | 32 | 15 | 10 | 2 | 3 | 0 |
| A4 | The case against; the first hour | 32 | 15 | 7 | 8 | 0 | 0 |
| B1 | Building from scratch | 23 + 19 | 18 | 7 | 7 | 3 | 1 |
| B2 | Levers and hybrids | 41 | 16 | 8 | 5 | 3 | 0 |
| B3 | Grinders and motors | 30 | 15 | 6 | 7 | 1 | 1 |
| B4 | Bedside automation and robotics | 32 | 16 | 3 | 9 | 3 | 1 |
| B5 | What to buy | 32 | 16 | 5 | 5 | 6 | 0 |
| **All** | | **319** | **142** | **64** | **51** | **24** | **3** |

*Verified* means an independent search result, from the primary source or a reputable outlet other than the one the researcher cited, showed the same wording or figure with the same attribution. *Partial* means the substance held but something was off (wording, a number, a date, an attribution); the prose uses the corrected version. *Not found* and *contradicted* items were dropped or are flagged in the text as unverified. The espresso slices fared worse because forum posts and retailer pages are hard to corroborate by search alone.

The rule for reading this edition: a sentence in quotation marks was matched in at least one independent result, and a number without a flag was confirmed or corrected. Neither has been checked against the original page. Where it matters, such as a price before you buy or a quote before you repeat it, follow the link.

### Fixing it for next time

Most of the friction was the network allowlist. To let tomorrow's researchers read primary sources, open the cloud environment's settings (the environment menu in the session's title bar, then Edit). Under **Network access**, either choose a broader level or add allowed domains, leaving the package-manager box ticked. The domains these researchers needed most were home-barista.com, arxiv.org, printables.com, hackaday.com, pubmed.ncbi.nlm.nih.gov, cia.gov, sca.coffee, pewresearch.org, cjr.org, tomsguide.com, en.wikipedia.org and reddit.com. Steps are in the [cloud environment docs](https://code.claude.com/docs/en/cloud-environments#network-access). The 200-search cap is per turn, so a nightly job should run as several smaller batches, which is what this one ended up doing.

### The raw research

@@STACKS@@

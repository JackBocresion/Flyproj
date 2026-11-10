# A3 - AI-written personal briefs: what shipped, how it went, how they fail

## Scope
The 2024-2026 wave of AI-generated daily briefs and overnight research agents (ChatGPT Pulse, Google Labs CC, Apple notification summaries, Copilot Daily, Huxe, deep research), practitioner experience, and the measured reliability of AI summaries and AI search. Status checked as of 2026-11-10 where sources allowed.

## Method and search log
Method: WebSearch only (32 calls; WebFetch not used on non-GitHub hosts). All figures come from search-result text, mostly secondary coverage. Primary pages (CJR, Pew, EBU, Tao's blog, Vectara) were NOT opened; they surfaced only as snippets.

1. ChatGPT Pulse launch Sept 2025 review (standard) - launch facts: Pro-only, mobile, $200/month, 5-10 cards.
2. ChatGPT Pulse 2026 rollout Plus/free uptake (standard) - no uptake numbers; Plus "later".
3. Google Labs CC (standard) - Dec 2025 launch, "Your Day Ahead" email.
4. BBC complaint / Apple Mangione (standard) - complaint details, RSF reaction.
5. EBU/BBC 45% study (standard) - headline numbers.
6. Tow Center/CJR citation study (standard) - 60%+, per-tool, confidence.
7. Apple pause Jan 2025 (standard) - confirmed pause in iOS 18.3 beta, italics.
8. Pew AI Overviews clicks (standard) - 8% vs 15%, 1%.
9. Lee et al. Microsoft/CMU critical thinking (standard) - 319 workers, confidence finding.
10. Vectara leaderboard 2026 (standard) - conflicting secondary numbers.
11. Simon Willison digest (standard) - only monthly sponsor newsletter; nothing on daily agent.
12. Terence Tao literature search (standard) - mostly general studies; Tao pointers.
13. Tao Mastodon/AI tools (extended) - Tao's stated uses and verification caveat.
14. Mollick deep research (standard) - nothing direct; "On Working with Wizards".
15. Built-my-own daily briefing agent blogs (standard) - Stephan Miller, Hermes tutorial.
16. Karpathy hallucination/arXiv bots (standard) - nothing on a bot; Decoder paraphrase; Factored Verification paper.
17. Hamel Husain evals (standard) - secondary quotes on error analysis.
18. Copilot Daily (standard) - launch description only; no accuracy review.
19. Pulse hands-on reviews (extended) - mixed reviews, Tom's Guide negative.
20. Huxe (standard) - launch, $4.6M, shutdown May 2026 reports, Apple deal report.
21. Apple summaries return iOS 26 (standard) - back in beta 4, July 2025, red disclaimer.
22. Tao "Mathematical methods..." (extended) - Klowden-Tao paper, literature search condition.
23. Stephan Miller post (standard) - silent cron failures detail.
24. Deep research audit DeepTRACE (standard) - Salesforce/Microsoft audit.
25. EBU De Tender quote (standard) - quote via Creatives Unite.
26. Pulse availability 2026 (extended) - Pulse retired June 2026 (secondary).
27. Tao blog literature search wording (standard) - exact blog wording not confirmed; Tao quotes via secondary.
28. Willison deep research (standard) - Feb 2025 system-card post points.
29. Tow Center quote (standard) - exact wording not found; summaries only.
30. Google CC 2026 (standard) - Sept 17, 2026 family expansion.
31. Pulse retirement corroboration (extended) - June 17, 2026 release notes per several blogs; Scheduled Tasks successor.
32. Tom's Guide Pulse piece (standard) - author Amanda Caswell; argument summary.

## Findings

### 1. What shipped, and what is real as of late 2026

**ChatGPT Pulse (OpenAI).**
- Announced 2025-09-25 as a preview for Pro subscribers ($200/month, US) on iOS/Android; it researched overnight from chat history, memory and optional connectors and produced roughly five to ten visual cards a day ([YourStory](https://yourstory.com/ai-story/openai-chatgpt-pulse-pro-daily-briefings), [Tom's Guide](https://www.tomsguide.com/ai/chatgpt-pulse-is-here-now-ai-starts-the-chat-and-curates-your-feed), [Axios](https://www.axios.com/2025/09/25/chatgpt-prompts-you-pulse-openai)). One aggregator listing $20/month is wrong.
- OpenAI said Plus and then free users would follow once it got more efficient ([Thurrott](https://www.thurrott.com/a-i/openai-a-i/327299/openai-launches-chatgpt-pulse-in-preview), [BleepingComputer](https://www.bleepingcomputer.com/news/artificial-intelligence/chatgpt-pulse-is-coming-to-the-web-but-no-word-on-free-or-plus-roll-out/)). Per secondary sources it came to web but stayed Pro-only.
- **Retired.** Several blogs report OpenAI's 2026-06-17 release notes said Pulse would be sunset, with Pro users keeping access 14 more days, replaced by Scheduled Tasks (daily-briefing prompts, monitoring tasks that alert only on change) ([Lilach Bullock](https://www.lilachbullock.com/chatgpt-pulse/), [Prowlo](https://prowlo.com/blog/chatgpt-pulse-shut-down), [Justin McKelvey](https://justinmckelvey.com/blog/chatgpt-pulse), [The Decoder on scheduled tasks](https://the-decoder.com/chatgpt-keeps-creeping-toward-becoming-your-ai-personal-assistant-with-new-scheduled-task-controls/)). All are secondary/low-tier; the OpenAI release note itself was not seen. One source dated the retirement October 2026, so the date conflicts. Verify.
- Uptake: no usage figures found anywhere.
- Reviews (opinion/anecdote): Tom's Guide (Amanda Caswell) called it "hands down the worst new AI tool of 2025", arguing it is a premium-priced data grab that solves no problem ([Tom's Guide](https://www.tomsguide.com/ai/i-test-ai-for-a-living-and-this-is-hands-down-the-worst-new-ai-tool-of-2025)). Matthew Becher found early digests a buffet of ideas that then repeated, needing active prompting ([Substack](https://matthewbecher.substack.com/p/mini-review-chatgpt-pulse)). An OpenAI forum user said it surfaced useful items but took weeks of tuning ([OpenAI community](https://community.openai.com/t/what-has-chatgpt-pulse-done-to-help-you/1371024)). No reviewer reported a clear verdict after months of daily use.

**Google Labs CC.**
- Announced about 2025-12-16: an email agent that sends a morning "Your Day Ahead" from Gmail, Calendar and Drive; you reply to the email to teach or correct it; early access for paid AI Ultra/Pro users in US/Canada plus waitlist ([9to5Google](https://9to5google.com/2025/12/16/google-labs-cc/), [SiliconANGLE](https://siliconangle.com/2025/12/16/google-tests-cc-ai-agent-summarize-email-calendars-documents/), [Tom's Guide](https://tomsguide.com/ai/google-just-launched-a-new-ai-agent-that-runs-your-inbox-heres-what-cc-actually-does)). Access tiers vary between sources.
- Still alive: on 2026-09-17 Google Labs expanded it to a shared family/household agent for up to six people, US, personal accounts, waitlist ([Google blog](https://blog.google/innovation-and-ai/models-and-research/google-labs/the-new-cc-an-ai-agent-built-for-families/), [Android Authority](https://androidauthority.com/google-ai-cc-family-household-assistant-3712623)). Still an experiment.

**Apple Intelligence notification summaries.**
- Dec 2024: a summary of a BBC News alert read "Luigi Mangione shoots himself" (false); BBC filed a formal complaint; RSF called for removal; NYT/Netanyahu summary also wrong ([Silicon UK](https://silicon.co.uk/ai/bbc-apple-ai-592890), [Incident Database](https://incidentdatabase.ai/reports/4375)).
- 2025-01-16: Apple paused summaries for news and entertainment apps in iOS 18.3 beta ("temporarily unavailable"); summaries made italic; per-app off switch; error warning ([TechCrunch](https://techcrunch.com/2025/01/16/apple-pauses-ai-notification-summaries-for-news-after-generating-false-alerts), [Engadget](https://www.engadget.com/ai/apple-pauses-ai-notification-summaries-of-news-alerts-in-latest-ios-beta-195900023.html)).
- Returned in iOS 26 beta 4 (July 2025) behind a red disclaimer that "summarization may change the meaning" ([9to5Mac](https://9to5mac.com/2025/07/22/ios-26-beta-4-re-enables-apple-intelligence-notification-summaries-for-news-apps/), [AppleInsider](https://appleinsider.com/articles/25/07/22/apple-brings-back-notification-summaries-for-news-in-ios-26)). Final-release status not confirmed.

**Microsoft Copilot Daily.** Spoken personalised news/weather briefing launched Oct 2024 with partners such as Reuters, Axel Springer, Hearst, FT ([GeekWire](https://www.geekwire.com/2024/new-microsoft-copilot-features-include-natural-ai-voice-interactions-and-daily-news-summary/), [Windows Latest](https://windowslatest.com/2024/10/01/hands-on-microsoft-copilot-is-getting-perplexity-ai-like-news-podcast-feature)). No independent accuracy evaluation found.

**Huxe.** Ex-NotebookLM founders (Raiza Martin et al.), audio briefing from email/calendar, $4.6M seed, public Sept 2025 ([TechCrunch](https://techcrunch.com/2025/09/23/former-notebooklm-devs-new-app-huxe-taps-audio-to-help-you-with-news-and-research), [TechBuzz](https://techbuzz.ai/articles/ex-google-notebooklm-devs-launch-huxe-with-4-6m-funding)). Secondary sources report it shut down 2026-05-22 ([Ecosistema Startup](https://ecosistemastartup.com/?p=82587), [Westfield/Pulse mirror](https://goodfest.westfield.com/2026/05/audio-generation-app-huxe-founded-by-former-notebooklm-developers-shuts-down/)), and an Oct 2026 item reports Apple hiring staff and licensing IP ([iClarified](https://www.iclarified.com/102723/apple-strikes-ai-audio-deal-with-huxe-founded-by-former-notebooklm-developers)). Low-tier sources; timeline unconfirmed.

**Pattern.** Of the flagship "proactive brief" products, Pulse was retired within about nine months, Huxe reportedly closed, Apple's feature was pulled and returned with warnings, CC survives as a Labs experiment. Inference from the above, not a source's claim.

### 2. Reliability evidence (studies and data)

- **EBU/BBC, Oct 2025.** 22 public-service media organisations, 18 countries, 14 languages, four assistants, 3,000+ answers: 45% had at least one significant issue; about 31% sourcing problems; about 20% major accuracy problems; Gemini worst at 76% significant issues; 81% had some issue; BBC's earlier study found 51% significant issues, so some improvement ([Advanced Television](https://www.advanced-television.com/2025/10/22/study-ai-misrepresents-news-content-45-of-the-time), [InfoDocket](https://www.infodocket.com/2025/10/22/bbc-largest-study-of-its-kind-shows-ai-assistants-misrepresent-news-content-45-of-the-time-regardless-of-language-or-territory/), [EBU release](https://www.ebu.ch/news/2025/10/ai-s-systemic-distortion-of-news-is-consistent-across-languages-and-territories-international-study-by-public-service-broadcaste), [Gizmodo](https://gizmodo.com/ai-assistants-get-news-wrong-45-of-the-time-study-finds-2000676069)). "Significant issue" is not "wrong"; one outlet overstated it.
- **Tow Center/CJR, Mar 2025.** Eight AI search tools, 200 articles from 20 publishers, given a quoted excerpt: collectively wrong on 60%+ of citation queries; Perplexity 37% wrong, Grok 3 94%; tools rarely declined; premium tiers more often confidently wrong; syndicated copies and fabricated URLs cited; licensing deals did not guarantee accuracy ([CJR](https://www.cjr.org/tow_center/we-compared-eight-ai-search-engines-theyre-all-bad-at-citing-news.php), [eWeek](https://eweek.com/?p=232924), [TechSpot](https://www.techspot.com/news/107101-new-study-finds-ai-search-tools-60-percent.html)). Note the task is narrow (identify the source of a quote), not summarisation.
- **Vectara HHEM leaderboard.** Best current summarisation hallucination rate about 1.8% on the newer dataset (finix_s1_32b), runners-up about 3.1-3.3%; older dataset leaders 0.6-0.7% ([LongTermWiki mirror](https://www.longtermwiki.com/resources/b44f883dc65dd0e9), [Suprmind](https://suprmind.ai/hub/ai-hallucination-rates-benchmarks-in-2026/)). Secondary and conflicting; it measures faithfulness to a supplied short document, which is far easier than open-web news. The gap between ~2% (grounded summary) and 45% (live news answers) is the key contrast; the tasks differ, so do not compare directly.
- **Deep research audits.** DeepTRACE (Salesforce/Microsoft, Sept 2025, [arXiv 2509.04499](https://arxiv.org/abs/2509.04499)): deep research agents and AI search include many statements unsupported by their own sources; one configuration reached 97.5% unsupported per a secondary write-up ([Earth.com](https://www.earth.com/news/ai-generated-search-tool-answers-are-frequently-filled-with-errors)); citation accuracy 40-80% depending on system. Another study: deep research gets links valid (above 94%) but factual accuracy of cited content only 39-77% ([IntuitionLabs](https://intuitionlabs.ai/articles/citation-reliability-ai-literature-reviews)). A literature-review comparison: about 3% fabricated references, 64% real papers with at least one metadata error, overlap with human-selected references under 6% ([NeurIPS 2026 listing](https://neurips.cc/virtual/2026/166240)). All secondary; verify numbers.
- **Summaries of papers.** Factored Verification found about 0.62 (ChatGPT), 0.84 (GPT-4), 1.55 (Claude 2) hallucinations per summary of academic papers, often subtle ([arXiv 2310.10627](https://arxiv.org/pdf/2310.10627)). Old models (2023).
- **Automation bias / over-reliance.** Lee et al., CHI 2025, 319 knowledge workers, self-reported: confidence in AI associated with less critical-thinking effort; self-confidence with more; effort shifts from gathering to verifying ([The Register](https://www.theregister.com/2025/02/11/microsoft_study_ai_critical_thinking/), [paper PDF](https://advait.org/files/lee_2025_ai_critical_thinking_survey.pdf)). It is a self-report survey, not behaviour. A claim that 83 of 319 reported trust discouraging reflection came from one secondary report and is unconfirmed.
- **Click-through.** Pew (Jul 2025), 900 US adults, 68,879 searches: users clicked a regular result in 8% of visits with an AI summary vs 15% without; about 1% clicked a link inside the summary; sessions ended 26% vs 16% ([9to5Google](https://9to5google.com/2025/07/23/google-ai-overview-link-click-study/), [Search Engine Land](https://www.searchengineland.com/google-ai-overviews-hurting-clicks-study-459434/), [eMarketer](https://www.emarketer.com/content/google-ai-summaries-ending-search-sessions-reducing-click-through-behavior)). Google disputed it. This is Google Search, not briefs, but it is the best data that people do not check sources.

### 3. Practitioners

- **Terence Tao** (mathematician, UCLA). Uses AI for "secondary tasks" such as literature search and proof-checking; says literature search is already well established; his March 2026 piece with Tanya Klowden endorses AI literature search only if you can follow and check that references establish what the AI claims ([Tao blog](https://terrytao.wordpress.com/2026/03/29/mathematical-methods-and-human-thought-in-the-age-of-ai/), [arXiv 2603.26524](https://arxiv.org/pdf/2603.26524), [Tao AI views page](https://teorth.github.io/tao-web/ai-views.html)). The exact blog sentence was paraphrased by the search tool, so it is not quoted. On Erdos problem #728 he noted AI literature search found no significant prior work, though earlier cases were later found in the literature ([Mathstodon](https://mathstodon.xyz/@tao/115855840223258103) listing; not confirmed which post).
- **Simon Willison.** On OpenAI deep research (Feb 2025): checking references catches most hallucinations, but omissions are hard to spot, and a polished multi-page document risks giving a false impression of a PhD-level assistant (paraphrase) ([Willison post](https://simonwillison.net/2025/Feb/25/deep-research-system-card/)). His own digest is a monthly sponsor newsletter, hand-curated, billed as less mail ([newsletters](https://simonwillison.net/newsletters/2026/)). Nothing found on Pulse.
- **Hamel Husain.** Core practice: read the traces yourself (error analysis), build your own viewer; LLM judge comes later ([AI Engineer talk page](https://ai.engineer/talks/how-to-construct-domain-specific-llm-evaluation-systems), [Antoine Buteau notes](https://www.antoinebuteau.com/lessons-from-hamel-husain.md)). Secondary.
- **Ethan Mollick.** Not found directly; secondary pieces say AI needs a person in the loop and compare hallucination to tolerated human error ([Penn Today](https://penntoday.upenn.edu/penn-in-the-news/wharton-professor-says-ai-intern-who-lies-little-bit-make-their-bosses-happy)). "On Working with Wizards" (verifying magic) exists but text not seen.
- **Karpathy.** Hallucination as inherent ("dreaming"), grounding via retrieval; no briefing bot found ([The Decoder](https://the-decoder.com/?p=10028) per search). Weak.
- **Builders' failure stories (anecdote).** Stephan Miller: agent-internal cron silently failed while still producing plausible output; fix was host cron plus script data, concluding autonomous agents are mostly an infrastructure problem ([Miller](https://www.stephanmiller.com/my-home-ai-agent-kept-making-shit-up/), [DEV mirror](https://dev.to/eristoddle/my-ai-agent-kept-making-shit-up-and-other-lessons-from-running-openclaw-566p)). Hermes tutorial: scheduled jobs start with no memory, so prompts must be self-contained ([Hermes docs](https://hermes-agent.nousresearch.com/docs/guides/daily-briefing-bot)). Other posts report feedback loops and "five things that matter beat twenty" ([Substack](https://herhighreturn.substack.com/p/i-built-a-morning-briefing-agent)).
- **What stuck after novelty.** I found no well-sourced first-hand "I still use it after N months" account. Evidence of what survived is indirect: OpenAI folded Pulse into user-defined scheduled tasks with change-triggered alerts (users specify, rather than the model guessing interests). Inference, not stated by any practitioner.

### 4. Guardrails recommended
- Check every cited reference against the primary source; treat output as leads (Tao; Willison; intuitionlabs/practical guides).
- Verification is the residual human job (Lee et al. "information verification, response integration and task stewardship").
- Visible marking and warnings: Apple's italics, "beta" tag and meaning-change disclaimer; nudge to open the original.
- Claim-level checking against the source (Factored Verification).
- Read raw logs/traces (Husain); keep deterministic data fetch outside the LLM and fail loudly (Miller).
- Self-contained prompts, feedback buttons/reply-to-correct (CC, Hermes).
- Diffing against yesterday, confidence labels, fact/inference separation: no source found stating these as evidence-backed practice; they are plausible design choices, not sourced here.

## Quote bank

> It is essential to us that our audiences can trust any information or journalism published in our name and that includes notifications.
BBC statement, Dec 2024, SECONDARY, [Silicon UK](https://silicon.co.uk/ai/bbc-apple-ai-592890)

> generative AI services are still too immature to produce reliable information for the public.
Reporters Without Borders (RSF), Dec 2024, SECONDARY (fragment), [Silicon UK](https://silicon.co.uk/ai/bbc-apple-ai-592890)

> This research conclusively shows that these failings are not isolated incidents
Jean Philip De Tender, EBU Media Director and Deputy Director General, 22 Oct 2025, SECONDARY (sentence truncated in source; article text garbled), [Creatives Unite](https://creativesunite.eu/article/ai-assistants-threaten-news-integrity-and-public-trust-major-study-finds)

> Confidence in AI is associated with reduced critical thinking effort, while self-confidence is associated with increased critical thinking
Lee et al. (Microsoft Research / Carnegie Mellon), CHI 2025, Feb 2025 coverage, SECONDARY as presented in results (paper at [advait.org](https://advait.org/files/lee_2025_ai_critical_thinking_survey.pdf)); see also [The Register](https://www.theregister.com/2025/02/11/microsoft_study_ai_critical_thinking/)

> secondary tasks like doing literature searches or checking a proof or writing some code, proof reading something that I wrote to see if there's any opportunity to make things a little bit tighter.
Terence Tao, mathematician (UCLA, Fields Medallist), date unclear, WEAK (relayed via search result attributing Big Think; original URL not seen), [Daily Maverick context](https://dailymaverick.co.za/article/2026-05-03-crossed-wires-what-does-the-worlds-greatest-living-mathematician-think-of-ai)

> I can search literature much more accurately and effectively than I could before, so I'm doing way more
Terence Tao, date unclear, SECONDARY (OfficeChai, truncated), [OfficeChai](https://officechai.com/ai/ai-is-allowing-me-to-experiment-and-try-crazier-things-mathematician-terrance-tao/)

> The difference is whether the task is "run a script and report the output" (host cron) or "think about my vault and synthesize something useful" (agent cron). Only one of those should involve an LLM.
Stephan Miller, blogger running self-hosted agent, 2026, PRIMARY (his blog, as shown by search), [stephanmiller.com](https://www.stephanmiller.com/my-home-ai-agent-kept-making-shit-up/)

> This is hands down the worst new AI tool of 2025 — and I regret ever turning it on
Amanda Caswell, Tom's Guide writer (headline), 2025, PRIMARY (headline), [Tom's Guide](https://www.tomsguide.com/ai/i-test-ai-for-a-living-and-this-is-hands-down-the-worst-new-ai-tool-of-2025)

> temporarily unavailable
Apple spokesperson, to the BBC, Jan 2025, SECONDARY (two-word fragment), [TechCrunch](https://techcrunch.com/2025/01/16/apple-pauses-ai-notification-summaries-for-news-after-generating-false-alerts)

## Disagreements, failure modes and caveats
- Failure modes documented: fabricated or misleading summary of a headline (Apple); wrong or syndicated source attribution and invented URLs (Tow); unsupported statements within own citations (DeepTRACE); metadata-corrupted real references (lit-review study); omissions that checking references will not reveal (Willison); silent pipeline failure producing plausible output (Miller); repetition over time (Becher); over-trust (Lee et al.); few clicks on sources (Pew).
- Grounded summarisation (Vectara ~2-3%) versus open-web news answers (EBU 45%, Tow 60%+) measure different tasks; a brief that summarises supplied documents is closer to the first, a brief that researches the web is closer to the second.
- Studies concern general assistants, not brief products; no independent accuracy audit of Pulse, CC or Copilot Daily was found.
- Pew is Google Search behaviour; Lee et al. is self-report; EBU "significant issue" is broader than "error".
- Google disputes the Pew conclusions; sample was 900 people.
- Product-status claims for Pulse retirement and Huxe shutdown rest on blogs/aggregators.

## Sources
- OpenAI Pulse launch coverage: [Tom's Guide](https://www.tomsguide.com/ai/chatgpt-pulse-is-here-now-ai-starts-the-chat-and-curates-your-feed), [Axios](https://www.axios.com/2025/09/25/chatgpt-prompts-you-pulse-openai), 2025-09-25; reputable outlets.
- Pulse retirement: [Lilach Bullock](https://www.lilachbullock.com/chatgpt-pulse/), [Prowlo](https://prowlo.com/blog/chatgpt-pulse-shut-down), [Decoder](https://the-decoder.com/chatgpt-keeps-creeping-toward-becoming-your-ai-personal-assistant-with-new-scheduled-task-controls/), mid-2026; blogs plus one reputable outlet on scheduled tasks; OpenAI note unseen.
- Google CC: [Google blog](https://blog.google/innovation-and-ai/models-and-research/google-labs/the-new-cc-an-ai-agent-built-for-families/) (2026-09-17, first-party), [9to5Google](https://9to5google.com/2025/12/16/google-labs-cc/) (2025-12-16).
- Apple: [TechCrunch](https://techcrunch.com/2025/01/16/apple-pauses-ai-notification-summaries-for-news-after-generating-false-alerts) (2025-01-16, reliable), [Silicon UK](https://silicon.co.uk/ai/bbc-apple-ai-592890) (Dec 2024), [9to5Mac](https://9to5mac.com/2025/07/22/ios-26-beta-4-re-enables-apple-intelligence-notification-summaries-for-news-apps/) (2025-07-22).
- EBU/BBC: [EBU release](https://www.ebu.ch/news/2025/10/ai-s-systemic-distortion-of-news-is-consistent-across-languages-and-territories-international-study-by-public-service-broadcaste) (2025-10-22, primary, snippet only), [Advanced Television](https://www.advanced-television.com/2025/10/22/study-ai-misrepresents-news-content-45-of-the-time).
- Tow Center: [CJR](https://www.cjr.org/tow_center/we-compared-eight-ai-search-engines-theyre-all-bad-at-citing-news.php) (March 2025, primary, snippet only), [eWeek](https://eweek.com/?p=232924).
- Pew: [9to5Google](https://9to5google.com/2025/07/23/google-ai-overview-link-click-study/) (2025-07-23), secondary of Pew.
- Lee et al.: [paper PDF](https://advait.org/files/lee_2025_ai_critical_thinking_survey.pdf), [The Register](https://www.theregister.com/2025/02/11/microsoft_study_ai_critical_thinking/) (2025-02-11).
- Vectara: [LongTermWiki mirror](https://www.longtermwiki.com/resources/b44f883dc65dd0e9), [Suprmind](https://suprmind.ai/hub/ai-hallucination-rates-benchmarks-in-2026/); aggregator quality, secondary.
- DeepTRACE: [arXiv 2509.04499](https://arxiv.org/abs/2509.04499) (Sept 2025); [Earth.com](https://www.earth.com/news/ai-generated-search-tool-answers-are-frequently-filled-with-errors) secondary.
- Tao: [blog](https://terrytao.wordpress.com/2026/03/29/mathematical-methods-and-human-thought-in-the-age-of-ai/) (2026-03-29, primary, snippet only), [Tao AI views](https://teorth.github.io/tao-web/ai-views.html).
- Willison: [deep research system card post](https://simonwillison.net/2025/Feb/25/deep-research-system-card/) (2025-02-25, primary).
- Husain: [AI Engineer talk](https://ai.engineer/talks/how-to-construct-domain-specific-llm-evaluation-systems); [Buteau notes](https://www.antoinebuteau.com/lessons-from-hamel-husain.md) (secondary).
- Miller: [stephanmiller.com](https://www.stephanmiller.com/my-home-ai-agent-kept-making-shit-up/) (2026, primary, anecdote).
- Huxe: [TechCrunch](https://techcrunch.com/2025/09/23/former-notebooklm-devs-new-app-huxe-taps-audio-to-help-you-with-news-and-research) (2025-09-23), [Ecosistema Startup](https://ecosistemastartup.com/?p=82587) (2026, low tier).
- Copilot Daily: [GeekWire](https://www.geekwire.com/2024/new-microsoft-copilot-features-include-natural-ai-voice-interactions-and-daily-news-summary/) (Oct 2024).

## Gaps
- No usage/uptake numbers for Pulse, CC, Copilot Daily, Huxe.
- OpenAI release note on Pulse retirement not seen; exact date uncertain.
- No exact Tao sentence on literature-search verification; no direct Mollick, Karpathy or Willison comment on briefs/Pulse; no arXiv-summary-bot practitioner accounts.
- Primary pages for Pew, CJR, EBU, Vectara not opened; numbers via secondary text.
- No independent accuracy audit of any commercial daily-brief product; no evidence on diffing/confidence-label guardrails.
- Apple summaries status after iOS 26 release unconfirmed; Huxe shutdown/Apple deal timeline unconfirmed.

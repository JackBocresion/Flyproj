# B4 - Waking up to espresso: robotics and home automation at the bedside

## Scope
Precedents for wake-up beverage machines (Teasmade, Barisieur), home-automation hooks for espresso machines (first-party vs community), robot baristas and low-cost arms, bedside practicalities (noise, safety, standards, espresso degradation), and existing DIY scheduled-brew projects. Goal context: an integrated machine with mixed manual/automatic function, not an arm on a stock machine.

## Method and search log
Method: WebSearch only (32 calls, budget used in full) plus free WebFetch of GitHub READMEs (several 504s/404s; those that worked are cited). Search results are server-side summaries, so most numbers are second-hand; items needing a primary check are flagged in Gaps.

Searches (S# = order):
1. S1 standard - Teasmade history/how it worked/safety. Yielded: patent history (Rowbottom 1891-92, Absolom 1932), Goblin 1936/37 dates conflicting, steam-pressure mechanism, decline, Swan now makes them. Safety thin.
2. S2 standard - Barisieur price/reviews. Yielded: price $399-445 US, BGR scald concern, Trustpilot mixed aftercare, no WiFi.
3. S3 standard - HA La Marzocco integration. Yielded: official HA docs page; schedules read-only; models Linea Mini/Mini R/Micra/GS3 AV/MP; cloud API.
4. S4 standard - GaggiMate/Gaggiuino HA. Yielded: GaggiMate MQTT plugin docs; ALERTua/hass-gaggiuino HACS.
5. S5 standard - Cafe X closures. Yielded: Jan 2020 SF closures, Aug 2020 airports, pivot to selling $200k kiosk.
6. S6 standard - LeRobot SO-101 ACT success rates. Yielded: small-sample HF model cards (85% cube, 40-60% folding); no pour benchmark.
7. S7 standard - Artly/Crown/Rozum/Costa. Yielded: Artly funding history only ($8M 2022, $340k crowdfund 2023), robot learns from master barista, slower than human.
8. S8 standard - EU 801/2013 coffee machine auto power-down. Yielded: regulation amends 1275/2008; 15/30 min defaults per Topten; EUR-Lex "no longer in force"; 2022 draft annex 30/40 min.
9. S9 standard - espresso crema collapse/cooling study. Yielded: Arii and Nishizawa via InsideHook (15 min); blogs 1-3 min crema.
10. S10 standard - DIY scheduled espresso projects. Yielded: delayed Nespresso (ESP32+HA), Keurig+cron, timed Silvia, hackster/hackaday.io list; none deliver to bed.
11. S11 standard - noise dB pumps/grinders. Yielded: only estimates (vibe 60-75, rotary 50-60; grinders 70-90), conflicting.
12. S12 standard - Meticulous/Decent API. Yielded: decent-advanced-rest-api (community), community MCP servers for Meticulous.
13. S13 extended - Physical Intelligence espresso. Yielded: pi*0.6 RECAP espresso doubling throughput; pi0.7 (Apr 2026) espresso out of the box (third-party).
14. S14 standard - motorized hand grinder conversions. Yielded: nothing relevant (generic drill adapters; Wondermill 160 RPM note).
15. S15 standard - automated lever/hybrid machines. Yielded: Meticulous "robotic lever", La Pavoni profiling threads, Lelit paddle.
16. S16 standard - IEC 60335-2-15 / UL 1082. Yielded: edition 7.0 (2024-11), clause 19 abnormal operation, UL 1082 thermal cutoffs; no unattended text.
17. S17 standard - Breville app/smart plug. Yielded: Stark Insider on Breville app schedule; sageha HA integration; Barista Express Shelly hack.
18. S18 standard - Teasmade safety/recalls. Yielded: no Teasmade recalls found (unrelated kettle recalls only).
19. S19 extended - robot barista failures (Briggo, Crown, Rozum). Yielded: Briggo to Coca-Cola/Costa 2020, Cafe X closures; no Crown detail.
20. S20 standard - Arii/Nishizawa check. Yielded: confirmed InsideHook (2017) coverage and quote; original paper not returned.
21. S21 standard - SO-ARM101 prices. Yielded: HF ~$130 non-printed parts, Seeed $220 preorder, $199-312 kits, A$714 assembled.
22. S22 standard - Barisieur mechanism. Yielded: induction heating in borosilicate glass, 94 C, Kickstarter >$700k (secondary), 2.0 immersion brewer.
23. S23 standard - HA espresso smart-plug automations. Yielded: HA blueprint, 15 min pre-alarm warm-up, 25 min full warm-up anecdote, Stark Insider.
24. S24 standard - Meticulous API. Yielded: MCP servers using local IP; protocol undocumented in results.
25. S25 standard - DIY linear-actuator lever builds. Yielded: Home-Barista lever threads, 4-5:1 mechanical advantage target, NEMA17 actuator force caution.
26. S26 standard - SO-101 coffee demos. Yielded: SIGRobotics matcha bot (bimanual SO-101); no espresso demo.
27. S27 standard - cup preheat/insulated vessels. Yielded: vendor blog readings (ceramic 65 to 54 C in 1-3 min), Tasting Table 54 vs 37 degree drop.
28. S28 standard - Teasmade mechanism (Hackaday). Yielded: sealed kettle, steam pressure pushes water to pot, switch released cuts element and sounds buzzer.
29. S29 standard - Rozum/Crown. Yielded: Rozum Cafe $100k package/$22k arm (2020), Cafe X arm is Mitsubishi industrial arm, Artly learned from Joe Yang.
30. S30 standard - grinder sound meter. Yielded: Eureka Silenzio 67-68 dB (SCG) vs 55-60 (Clive); distances vary.
31. S31 standard - Cafe X/Artly 2025-26 status. Yielded: nothing current; Artly Portland in retail store.
32. S32 standard - espresso flavour vs temperature. Yielded: Klotz brew-temp study; serving-temp claims anecdotal.
WebFetch (GitHub, not counted): jniebuhr/gaggimate, decent-advanced-rest-api readme, zweckj/pylamarzocco, huggingface/lerobot, MeticulousHome/pyMeticulous, ALERTua/hass-gaggiuino README, simonjgreen/sageha. Failed: first hass-gaggiuino fetch (504), hallboyone/RaspberryLatte (504, then 404 on raw).

## Findings

### 1. Precedents: Teasmade
- Pre-Goblin patents: Samuel Rowbottom (Derby) applied 1891, granted 1892; Frank Clarke 1902; neither mass-produced. George Absolom applied 1932; Goblin (British Vacuum Cleaner and Engineering Co.) marketed the Teasmade, first model dated 1936 or 1937 depending on source [Wikipedia](https://en.wikipedia.org/wiki/Teasmade), [teasmade.uk](https://www.teasmade.uk/1936-goblin-teasmade/), [Grace's Guide](https://gracesguide.co.uk/Goblin_Teasmade). Dates conflict; unresolved.
- Mechanism (documented): a sealed kettle is heated by an element switched on by an alarm clock; steam pressure forces the boiled water up a tube into the teapot; once water leaves, a switch under the kettle is released, cutting the element and triggering buzzer and lamp [Hackaday](https://hackaday.com/2020/01/30/retrotechtacular-teasmade). teasmade.uk adds a separate bimetallic thermostat cut-off and notes a leaking seal means pressure never builds [teasmade.uk](https://www.teasmade.uk/how-does-a-teasmade-work/). Sources differ on whether the cutoff is the lifted pad or the thermostat; likely both.
- Decline: Goblin sold on to Swan; by the 1980s the item was less popular; Swan still makes Teasmades in China for the UK; trademark reportedly SEB-owned (Wikipedia and teasmade.uk, conflicting on years).
- Safety: no recall or injury data for Teasmade found. Evidence is anecdotal: a teasmade.uk user complaint about no fail-safe if the unit is not pre-prepared; a 2016 Endeavour TV episode used a Teasmade explosion as a plot device (fiction, not evidence). Design lesson: the 1930s design had a mechanically self-terminating cycle (pressure expulsion then cut-off), a pattern worth copying for unattended heating.
- Why it endured (interpretation, not sourced as a study): single-purpose, cheap, and the "tea ready on waking" ritual needs no skill; the weakness was prefilled water standing overnight and a pot of tea going stewed/cold if not drunk promptly.

### 2. Precedents: Barisieur and other bedside brewers
- Barisieur (Joy Resolve, London; designer Joshua Renouf, Nottingham Trent graduate project, then Kickstarter, reportedly >$700k): induction coil heats water in borosilicate glass, one source says boils in 3-5 min and pours at about 94 C; fill water and coffee the night before, choose whether coffee is ready before, at or after the alarm; 2.0 uses an immersion brewer; milk cooler (Peltier, per one source) [My Modern Met](https://mymodernmet.com/joshua-renouf-barisieur), [Yanko Design](https://www.yankodesign.com/2020/07/03/the-bariseur-2-0-wakes-you-up-each-morning-with-a-fresh-cup-of-coffee-and-a-charged-phone/amp/), [Salon](https://www.salon.com/2019/04/06/this-coffee-maker-alarm-clock-will-change-your-am-game).
- It is filter/pour-over or tea, not espresso. Price: $399 discounted from $445 (Salon, 2019); about $450 and one cup (ABC7); EUR 365 (another outlet). Check current price.
- Criticism: BGR questioned scald/knock-over safety; no Bluetooth or WiFi; one review noted about five minutes to brew; Trustpilot reviews of Joy Resolve are mixed on aftercare, with some praising service [Trustpilot](https://www.trustpilot.com/review/www.joyresolve.com?page=2), [BGR](https://bgr.com/?p=4701227).
- Pattern across Teasmade and Barisieur: both avoid pressurised extraction; hot water plus a loose infusion is forgiving of waiting. Espresso is the opposite (see section 5).

### 3. Home-automation hooks for espresso
First-party or official:
- La Marzocco, Home Assistant core integration (official HA docs page; it talks to La Marzocco's cloud API; machine must be added in the official La Marzocco app first). Supports Linea Mini, Mini R, Micra, GS3 AV and GS3 MP. Schedules are view-only in HA (calendar), editing only in the La Marzocco app; users build HA automations instead [HA docs](https://www.home-assistant.io/integrations/lamarzocco). Whether the HA integration is La Marzocco-authored: it is in HA core; the underlying library is community-maintained (below). La Marzocco itself offers app smart schedule [La Marzocco](https://nz.lamarzoccohome.com/?p=81353).
- Underlying library: zweckj/pylamarzocco, "unofficial", cloud client with websocket plus Bluetooth client; power on/off works over cloud or Bluetooth; shot counter via BLE for ESP-gateway models [GitHub](https://github.com/zweckj/pylamarzocco).
- Meticulous: official TypeScript API exists (MeticulousHome/meticulous-typescript-api); pyMeticulous (community wrapper, v0.3.0, GPL-3.0) uses REST plus Socket.IO; supports start, stop, tare, preheat, profiles, shot history, settings [GitHub](https://github.com/MeticulousHome/pyMeticulous). Community MCP servers drive machines over the LAN [glama](https://glama.ai/mcp/servers/q8p9xyba0o).
- Breville/Sage: the consumer app can toggle on or schedule ready-time on Wi-Fi models [Stark Insider](https://www.starkinsider.com/2023/04/how-to-automatically-turn-your-espresso-or-coffee-machine-each-morning.html). No official HA integration found. Community: simonjgreen/sageha, via reverse-engineered cloud websocket (iot-api-ws.breville.com), wake/sleep and `set_wake_schedule`; only the Oracle Dual Boiler (BES995) is listed; explicitly unofficial, use at own risk [GitHub](https://github.com/simonjgreen/sageha). Non-Wi-Fi models (e.g. Barista Express) need hardware mods (Shelly relay) [HA forum](https://community.home-assistant.io/t/modifying-a-breville-sage-barista-express-coffee-machine-to-integrate-with-home-assistant/487575).
Community or open hardware:
- GaggiMate (jniebuhr, CC BY-NC-SA 4.0): Gaggia retrofit with display; brew timer, steam/hot water, safety shutoff on unresponsive or over-temperature; documented WebSocket API (docs/websocket-api.yaml); docs describe an MQTT/Home Assistant plugin [GitHub](https://github.com/jniebuhr/gaggimate), [docs](https://docs.gaggimate.eu/docs/usage-configuration). README itself did not mention HA/MQTT; the docs site does.
- Gaggiuino: ALERTua/hass-gaggiuino (HACS custom): profile select entity; polls every 30 s so not usable for shot monitoring [GitHub](https://github.com/ALERTua/hass-gaggiuino).
- Decent: randomcoffeesnob/decent-advanced-rest-api (community, TCL): state, standby/enable, shots, profiles, HA example config [GitHub](https://github.com/randomcoffeesnob/decent-advanced-rest-api/blob/main/readme.md).
- Smart plug approach for simple/PID machines: HA community blueprint for schedule or wattage detection [HA forum](https://community.home-assistant.io/t/coffee-machine-switch-automation-schedule-based-or-wattage-detection/757018); anecdote of HA starting machine about 15 min before alarm; another says about 25 min to fully warm (anecdote, machine unspecified) [dev.to](https://dev.to/stefanoero/my-favorite-home-assistant-automation-waking-up-to-the-smell-of-coffee-27kk). Plug-cycling only works for machines with a mechanical power switch left on; many PID/electronic machines need a button press (the Breville mod above).
- Design takeaway: wake scheduling is solved (cloud or LAN). What none of these give is the physical delivery (cup placement, puck eject), which is what an integrated machine must add.

### 4. Robotics
Robot baristas:
- Cafe X: first SF site 2017; closed three SF sites Jan 2020 (CEO called them "prototypes" per ABC7/Crunchbase summaries), closed SFO and San Jose airport sites Aug 2020 citing pandemic traffic; pivoted to selling kiosks at $200,000 [Crunchbase News](https://news.crunchbase.com/venture/robotic-coffee-startup-cafe-x-shutters-stores-pivots-to-airports/), [ABC7](https://abc7news.com/post/robot-baristas-cafe-x-closes-sf-locations-/5830767/), [The Spoon](https://thespoon.tech/cafe-x-closed-its-airport-locations-and-laid-off-staff-now-its-planning-for-the-future/). Its arm is a Mitsubishi industrial arm (secondary summary).
- Briggo (Austin): acquired by a Coca-Cola subsidiary Oct 2020, kiosks rebranded Costa BaristaBot; five active Briggo kiosks then [CultureMap](https://austin.culturemap.com/news/restaurants-bars/10-30-20-briggo-austin-coffee-robot-company-purchased-by-coca-cola-company/), [The Spoon](https://thespoon.tech/briggos-coffee-haus-becomes-costa-coffee-baristabot/). Briggo was a purpose-built enclosed machine, not a general arm: closer to what the reader wants.
- Artly: $8M pre-Series A 2022, $340k+ crowdfunding 2023; arm learns from a master barista (Joe Yang); a 2022 report said service was slower than a human; CES 2026 latte-art demo [GeekWire](https://www.geekwire.com/2022/robotic-coffee-barista-maker-led-by-ex-aws-engineer-raises-8-3m-to-open-more-retail-locations/), [Yanko Design](https://www.yankodesign.com/2026/01/07/artly-robots-master-latte-art-and-drinks-for-ces-2026-debut/). No store count found.
- Rozum Cafe: own collaborative arm; 2020 pricing $100k full cafe, $22k arm [Daily Coffee News](https://dailycoffeenews.com/2020/04/24/the-rozum-cafe-offers-a-customizable-robotic-espresso-setup). Crown Coffee: only named in lists; nothing found.
- Lessons (interpretation from sources): robot cafes failed on foot traffic, slow throughput, limited menus, and loss of human connection, not on pulling a shot. Success stories are enclosed fixed-layout machines (Briggo) or niche placement (airports). Engineering lesson for a bedside machine: constrain the workspace.
Low-cost arms and learning:
- LeRobot supports SO101, Koch, OpenARM, LeKiwi, Unitree G1 and others; policies include ACT, Diffusion, SmolVLA, pi0 [GitHub](https://github.com/huggingface/lerobot). SO-101 cost: HF estimated about $130 non-printed parts; kits $199-$312 depending on vendor; assembled A$714 [Hackster](https://www.hackster.io/news/hugging-face-launches-the-so-101-an-upgraded-low-cost-3d-printable-autonomous-robot-arm-532360f441eb), [RoboticsCenter](https://roboticscenter.ai/learn/so-arm100-vs-so-arm101). Motors are Feetech STS3215 hobby servos (7.4 V).
- Realistic capability evidence (small samples, single setups): 85% (17/20) cube placing on one table [HF model card](https://huggingface.co/sahilapage/act_so101_pick_block_bowl) (card cited by search as "cube placing"; verify); cloth folding best 40-60% after 267 demos [project page](https://tabithako.github.io/projects/policy-training); 40% to near 100% depending on where inference ran [Classmethod](https://dev.classmethod.jp/en/articles/lerobot-so-arm101-act-training-eval/). A UIUC SIGRobotics bimanual SO-101 matcha bot included pouring water [Hackster](https://www.hackster.io/sigrobotics/matcha-bot-sigrobotics-embodied-ai-hackathon-1st-place-f0e520). No tamping or puck-prep result on an SO-101 found. Honest reading: pick-and-place of cups is plausible; tamping force control and portafilter lock-in are beyond hobby servos without force sensing (inference; no source tests it).
- Frontier: Physical Intelligence pi*0.6 with RECAP reports espresso making throughput and success more than doubling after on-robot experience, running for a long deployment [PI blog](https://www.pi.website/blog/pistar06); pi0.7 (Apr 2026) reportedly operates an espresso machine out of the box (third-party explainer) [robocloud](https://robocloud-dashboard.vercel.app/learn/blog/pi0-7-steerable-generalist-robot-model-2026). These use far larger models and data than a hobby SO-101.
Simpler mechanisms (design reasoning plus evidence):
- Meticulous is the existing commercial case of a motor-driven lever machine with ten sensors adjusting pressure, flow, temperature, weight [SCA entry](https://new.sca.coffee/entries/meticulous-espresso). It is not hand-operable as a lever.
- Hand-lever profiling culture: pressure gauges and bathroom-scale force measurements (La Pavoni about 24 lb pull for about 6 bar, 40 lb for about 9 bar) [Home-Barista](https://www.home-barista.com/levers/pressure-profiling-la-pavoni-t34126.html). Useful sizing numbers for a motorised lever (user-reported, not lab).
- DIY lever builders target 4-5:1 mechanical advantage with 60-100 cc stroke [Home-Barista](https://www.home-barista.com/levers/building-lever-machine-from-scratch-t41716.html). Candidate drives: lead-screw or linear actuator through a clutch/overrunning coupling so the hand lever still works (my suggestion). A small NEMA17 belt actuator at about 2.5 lbf is far too weak.
- Motor-driven hand grinder: no source found for conversions of Comandante/Kinu/1Zpresso; a hand grain-mill analogue recommends variable-speed drill under 160 RPM (vendor listing). Design note: hand grinders turn at tens of RPM, so a gearmotor with a removable crank or one-way clutch fits.

### 5. Bedside constraints
Noise:
- Estimates only: vibratory pump about 60-75 dB, rotary about 50-60 dB (guides stating estimates) [Complete Home Barista](https://completehomebarista.com/guides/espresso-machine-noise-levels-comparison/); another guide puts vibratory at 80-85 dB. Eureka Mignon Silenzio about 67-68 dB (Seattle Coffee Gear guide) vs 55-60 dB (Clive Coffee); distances and weighting differ. Forum reports say damping and mounting matter as much as pump type [Home-Barista](https://www.home-barista.com/espresso-machines/vibe-pump-vs-rotary-t10792-30.html). No instrument-measured hand-grinder dB found. Hand crank is silent in electrical terms, but burr grinding noise remains.
Safety and standards:
- IEC 60335-2-15 (liquid-heating appliances incl. coffee makers), edition 7.0 published 2024-11, clause 19 abnormal operation; UL 1082 requires thermal cutoffs (single TH-100-rated or two) and abnormal-operation tests; CSA update 2022 added abnormal-operation requirements for espresso and capsule machines [IEC](https://www.iecee.org/certification/iec-standards/iec-60335-2-152024), [UL 1082 text](https://cdn.intertek.com/www-intertek-com/dms-legacy/UL-1082-Rev-9-28-2017-ED-1-15-2020.pdf), [CSA](https://cdn.intertek.com/www-intertek-com/dms-legacy/CSA-C22-2-No-60335-2-15-Rev-2-1-2019-ED-6-1-2023.pdf). Clause text on unattended operation not retrieved. A homemade mod is outside any certification; independent hardware over-temperature cutouts are advisable (recommendation).
- EU auto power-down: Regulation 801/2013 (amending 1275/2008) required default delays to standby/off, applying to coffee machines from 1 Jan 2015; defaults reported as 15 min (portioned) and 30 min (fully automatic and piston) [Topten](https://storage.topten.eu/source/files/D2_1_Criteria_Paper_Coffee_Machines.pdf); EUR-Lex marks 801/2013 as no longer in force; a 2022 draft annex proposes 30 min (40 for insulated-jug-less drip) [draft](https://www.energimyndigheten.se/490884/globalassets/energieffektivisering_/jag-ar-saljare-eller-tillverkare/dokument/produkter-med-krav/standby--off-mode-samt-natverksstandby/draft-annex-standby-ecodesign-reg_7january2022-2.pdf). Consequence: commercial EU machines cannot idle on for hours; a pre-alarm wake should be timed to the heat-up (15-25 min anecdotally) so it does not auto-off before use.
- Scald: Barisieur drew scald concerns (BGR); Teasmade-style sealed expulsion carries scald risk if a tube dislodges. Mitigations are design reasoning: drip tray with level sensor, enclosed cup bay, low-pressure hot path.
Degradation and timing:
- Evidence: Arii and Nishizawa (Mukogawa Women's Univ.), reported secondhand, found foam falls in two phases (fast phase about 15 min) and foam delays cooling; they suggested the first 15 minutes may be the best drinking window [InsideHook](https://www.insidehook.com/culture/science-behind-espresso-foam). Original paper not retrieved. Compare practical sources: crema gone in 1-3 min (blogs) [Clive Coffee](https://clivecoffee.com/blogs/learn/is-your-espresso-dying-while-you-wait). Flavour shift on cooling is anecdotal; Klotz et al. concern brew temperature, not serving temperature [preprint](https://www.preprints.org/manuscript/201910.0352/v1).
- Implication: brew timing at alarm (or a few minutes before) matters more than an espresso sitting all night; an Americano tolerates standing better because dilution and a larger hot volume slow cooling (reasoning, no study found).
- Cups: a vendor blog (method unstated) shows thick ceramic dropping 65 to 54 C over 1-3 min vs double-wall glass 80 to 74 C [Papel Espresso](https://www.papelespresso.com/comparing-insulated-vs-non-insulated-cups-for-long-duration-espresso-sipping); Tasting Table says ceramic cools espresso about 54 degrees vs about 37 for double-wall glass (undated figures, no method). Preheating narrows the gap (claim, no measured rate). A cup warmer or hot-water rinse in the bay is a design option.
- Cleaning and puck disposal, reservoir and drip management: no sources retrieved; flagged as gaps. Design inference: automatic puck knock-out into a bin is the hardest of the chores; Briggo/Cafe X kiosks solved it only inside enclosed machines.

### 6. Existing DIY projects
- Delayed Nespresso: ESP32 plus switch under Home Assistant; author rejects fixed 7am brewing in favour of queueing for tomorrow [substack](https://attentionseekingtech.substack.com/p/smart-nespresso).
- SmartKeurig: ATmega plus Raspberry Pi, cron-based [GitHub](https://github.com/shildenbrand/SmartKeurig).
- RaspberryLatte (hallboyone): Silvia PID/controller project [GitHub](https://github.com/hallboyone/RaspberryLatte) (README not retrievable here).
- Hackaday.io coffee alarm clock (STM32); Raspberry Pi slow-coffee with Telegram; timed Rancilio Silvia; ML Silvia that predicts when you want a shot and preheats [Hackster](https://www.hackster.io/news/this-espresso-machine-knows-exactly-when-you-need-a-caffeine-shot-356d0ee9bd86).
- None found that delivers a finished espresso to a bed; none found with hand-lever-plus-motor hybrid.

## Quote bank
> High-quality foam plays an important role in delaying the cooling of espresso coffee
Yasuhiro Arii and Kaho Nishizawa, Mukogawa Women's University (Japan), as quoted by InsideHook, 2017 (per search summary), SECONDARY, [source](https://www.insidehook.com/culture/science-behind-espresso-foam)

> Due to this long refresh period, the integration can not be used to monitor shots.
ALERTua, maintainer of hass-gaggiuino, README (undated), PRIMARY, [source](https://github.com/ALERTua/hass-gaggiuino)

> This is an unofficial integration. It is not affiliated with, endorsed by, or supported by Breville or Sage.
simonjgreen, sageha README (undated), PRIMARY, [source](https://github.com/simonjgreen/sageha)

> Some commands, like turning the machine on and off, can be sent through bluetooth.
zweckj, pylamarzocco README (unofficial library), PRIMARY, [source](https://github.com/zweckj/pylamarzocco)

> If the machine becomes unresponsive or the temperature goes too high, it will automatically turn off for safety.
jniebuhr, GaggiMate README (undated), PRIMARY, [source](https://github.com/jniebuhr/gaggimate)

> An "automatic" coffee machine that runs at 7am every morning isn't a good idea for obvious reasons. Instead of "automatic" I'm going for "delayed". I click a button and tomorrow at 7am I get coffee.
Author of the "Smart Nespresso" post, Attention Seeking Tech substack (date not seen), PRIMARY (author's own blog), [source](https://attentionseekingtech.substack.com/p/smart-nespresso)

> it seems far too easy to perhaps knock something over, at best, or severely scald yourself, at worst
BGR reviewer on the Barisieur (name and date not seen), SECONDARY/WEAK (paraphrase boundaries unclear in the search summary), [source](https://bgr.com/?p=4701227)

## Disagreements, failure modes and caveats
- Goblin Teasmade first-model date: 1936 vs 1937; end of Goblin ownership 1984 vs late 1990s.
- Teasmade cutoff trigger: released pad vs thermostat.
- Barisieur milk cooling: Peltier (one source) vs just a cool slot (another); Opumo's "stainless ball bearings" heating claim contradicts induction-coil accounts.
- Noise: vibratory 65-75 vs 80-85 dB across guides; Silenzio 67-68 vs 55-60 dB. Treat as indicative only.
- Crema/flavour: 15-min window (one lab group, secondhand) vs 1-3 min crema persistence (blogs); not contradictory (foam vs perceptible crema) but not a flavour study.
- EU standby: 801/2013 says in force from 2015 but EUR-Lex now lists it no longer in force; 15/30 min figures are from Topten criteria, not the regulation text.
- Artly: aggregator listing a $3.5M 2024 round conflicts with $340k 2023 crowdfund; unverified.
- LeRobot success rates are single-setup, small-sample model cards; not generalisable. Simulation scores do not predict real robots.
- Failure stories: Cafe X (closures 2020), Briggo (acquired, rebranded, small footprint), Barisieur aftercare complaints, Teasmade decline.
- Community integrations (pylamarzocco, sageha, hass-gaggiuino) can break if cloud APIs change; Breville and La Marzocco routes depend on vendor cloud.

## Sources
- Teasmade, Wikipedia, https://en.wikipedia.org/wiki/Teasmade - reference; dates conflict with other sources.
- Retrotechtacular: Teasmade, Hackaday, 2020-01-30, https://hackaday.com/2020/01/30/retrotechtacular-teasmade - mechanism, reputable.
- teasmade.uk (history/how it works), https://www.teasmade.uk/how-does-a-teasmade-work/ - enthusiast site, detailed.
- Grace's Guide Goblin Teasmade, https://gracesguide.co.uk/Goblin_Teasmade - historical reference.
- Salon on Barisieur, 2019-04-06, https://www.salon.com/2019/04/06/this-coffee-maker-alarm-clock-will-change-your-am-game - price, secondary.
- My Modern Met Barisieur, https://mymodernmet.com/joshua-renouf-barisieur - design press.
- Trustpilot Joy Resolve, https://www.trustpilot.com/review/www.joyresolve.com?page=2 - user reviews, mixed reliability.
- Home Assistant La Marzocco, https://www.home-assistant.io/integrations/lamarzocco - official docs.
- pylamarzocco, https://github.com/zweckj/pylamarzocco - community library README.
- pyMeticulous, https://github.com/MeticulousHome/pyMeticulous - org-hosted wrapper, v0.3.0.
- GaggiMate, https://github.com/jniebuhr/gaggimate and https://docs.gaggimate.eu - open-source project.
- hass-gaggiuino, https://github.com/ALERTua/hass-gaggiuino - community HACS.
- decent-advanced-rest-api, https://github.com/randomcoffeesnob/decent-advanced-rest-api - community.
- sageha, https://github.com/simonjgreen/sageha - community, unofficial.
- Stark Insider Breville schedule, 2023-04, https://www.starkinsider.com/2023/04/how-to-automatically-turn-your-espresso-or-coffee-machine-each-morning.html - blog.
- Crunchbase News Cafe X, 2020, https://news.crunchbase.com/venture/robotic-coffee-startup-cafe-x-shutters-stores-pivots-to-airports/ - trade press.
- ABC7 Cafe X closures, https://abc7news.com/post/robot-baristas-cafe-x-closes-sf-locations-/5830767/ - news.
- CultureMap Briggo, 2020-10-30, https://austin.culturemap.com/news/restaurants-bars/10-30-20-briggo-austin-coffee-robot-company-purchased-by-coca-cola-company/ - news.
- GeekWire Artly, 2022, https://www.geekwire.com/2022/robotic-coffee-barista-maker-led-by-ex-aws-engineer-raises-8-3m-to-open-more-retail-locations/ - news.
- Yanko Design Artly CES 2026, 2026-01-07, https://www.yankodesign.com/2026/01/07/artly-robots-master-latte-art-and-drinks-for-ces-2026-debut/ - design blog.
- Daily Coffee News Rozum, 2020-04-24, https://dailycoffeenews.com/2020/04/24/the-rozum-cafe-offers-a-customizable-robotic-espresso-setup - trade press.
- huggingface/lerobot, https://github.com/huggingface/lerobot - official repo.
- Hackster SO-101 launch, https://www.hackster.io/news/hugging-face-launches-the-so-101-an-upgraded-low-cost-3d-printable-autonomous-robot-arm-532360f441eb - prices, secondary.
- Physical Intelligence pi*0.6, https://www.pi.website/blog/pistar06 - primary lab blog.
- Matcha bot, Hackster, https://www.hackster.io/sigrobotics/matcha-bot-sigrobotics-embodied-ai-hackathon-1st-place-f0e520 - student project.
- IEC 60335-2-15:2024, https://www.iecee.org/certification/iec-standards/iec-60335-2-152024 - standards body.
- UL 1082 excerpt, https://cdn.intertek.com/www-intertek-com/dms-legacy/UL-1082-Rev-9-28-2017-ED-1-15-2020.pdf - excerpt.
- Topten coffee machine criteria, https://storage.topten.eu/source/files/D2_1_Criteria_Paper_Coffee_Machines.pdf - NGO research.
- EUR-Lex 801/2013, https://eur-lex.europa.eu/eli/reg/2013/801/oj - legal text, status flag.
- InsideHook on Arii and Nishizawa, 2017, https://www.insidehook.com/culture/science-behind-espresso-foam - secondary.
- Complete Home Barista noise guide, https://completehomebarista.com/guides/espresso-machine-noise-levels-comparison/ - estimates, low reliability.
- Papel Espresso insulated cups, https://www.papelespresso.com/comparing-insulated-vs-non-insulated-cups-for-long-duration-espresso-sipping - vendor, method unstated.
- Home-Barista threads (lever profiling, DIY lever), https://www.home-barista.com/levers/pressure-profiling-la-pavoni-t34126.html - forum anecdote.

## Gaps
- Primary text of Arii and Nishizawa paper and journal citation; any controlled sensory study of espresso held over time.
- Instrument-measured dB for vibratory vs rotary pumps and hand vs electric grinders.
- Actual clause text on unattended operation in IEC 60335-2-15 / UL 1082; current in-force EU rule replacing 801/2013 and exact default delays.
- Teasmade injury or recall data.
- Crown Coffee details; Cafe X and Artly current (2025-26) operating status; reasons for Artly outcomes.
- SO-101 evidence for tamping, puck prep, portafilter handling; payload and servo torque figures.
- Meticulous official API endpoints; GaggiMate MQTT topics README; RaspberryLatte README; Decent endpoint list.
- Motorised conversions of named hand grinders; any motorised-but-hand-operable lever espresso build.
- Cleaning, puck disposal, reservoir and drip management practices.

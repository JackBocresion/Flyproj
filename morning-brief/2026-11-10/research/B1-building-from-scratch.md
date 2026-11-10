# B1 - Building an espresso machine from scratch, and the open-source projects that make it sane

## Scope
How people build espresso machines from scratch or heavily modified from parts, and the open-source hardware/firmware ecosystem (Gaggiuino, GaggiMate, CleverCoffee, Decent, Meticulous, diyPresso). Engineering fundamentals (pumps, boilers, safety, lead) and a modify-first vs scratch-build view. Observation date: 2026-11-10.

## Method and search log
Method: WebSearch only (23 searches completed), plus WebFetch of GitHub pages (5 succeeded, 2 api.github.com calls returned 403). The shared web-search budget ran out after search 23, so 4 planned queries did not run (GaggiMate kit price/reviews, Gaggiuino Gen 3 cost, thermoblock-vs-boiler, transducer/flow-meter/OPV). The brief asked for 25-40 searches; this is below that. Search results are summaries, not page text, so most forum details are second-hand and no quote could be double-checked by a second exact-phrase search.

1. Gaggiuino README hardware/licence (extended): docs site says Gaggia Classic with 3-way valve only, Gen 1/2/3 controllers; licence not confirmed.
2. GaggiMate open source ESP32 (extended): ESP32 controller, OTA channels, CC BY-NC-SA noted, 2026 build write-up on firmware v1.9.0.
3. Home-Barista scratch lever builds (extended): found "Building a lever machine.... from scratch" (t41716) and others; machining details.
4. Decent open API/firmware (standard): pyDE1 (GPL-3.0) found; no official firmware source.
5. Hackaday DIY lever (standard): Hackaday 2024 diyPresso; 2020 lever press; 2018 motorbike-parts machine; list of HB threads.
6. diyPresso kit price/specs (extended): One EUR 1,250, Two EUR 1,695; firmware 1.8.0 Jan 2026.
7. Meticulous open source/API (standard): third-party tools only; Decent firmware closed.
8. Gaggiuino licence/community (standard): CC BY-NC, Gen 3 source closed, DMCA notice, Hackaday comments.
9. HB lever scratch cost/time (extended): cost-per-unit comment, ~month converting lathe to CNC, other builder costs.
10. DIY brass/lead/safety (extended): lead in brass, boiler welding advice, pressurestat anecdotes.
11. Gaggiuino Gen 3 source closed (extended): Aftermath quotation on scalping; repo state.
12. GaggiMate GitHub stars/licence (extended): mostly forks; org has HA integration; shop and docs links.
13. Decent firmware closed/signed (extended): HB forum recollection, UL claim, HN comments, OpenScale GPLv3.
14. Four Bar Design DIY lever (extended): CO2-cartridge design, $102 stainless parts, iteration lessons.
15. Rotary vs vibratory pumps (extended): vendor comparisons; no gear/brushless data.
16. HB "Modern DIY Double Boiler Lever Build" (extended): design details; 280 EUR / 70-80 h on a different open-boiler build.
17. Boiler pressure vessel codes (extended): UK PSSR 2000, Virginia act; no PED-specific source.
18. Electrical safety (standard): forum/vendor material only; no standard.
19. Lead NSF 372/51 (extended): 0.25% limit; EDF post; Dalla Corte certification.
20. Rancilio PID / CleverCoffee (standard): CleverCoffee, Perfect Coffee PID, silvia-pi, etc.
21. Meticulous openness (extended): Kickstarter updates say API open; community integrations.
22. Motorised/servo lever hybrids (extended): HB hybrid-lever explainer and servo musings; no documented servo build.
23. Open Source Lever Project (extended): Victoria Arduino-type spring group ~$495, dual thermoblocks.
GitHub fetches: jniebuhr/gaggimate, Zer0-bit/gaggiuino, rancilio-pid/clevercoffee, jeffsf/pyDE1, diyPresso/diyPresso-One (all OK).

## Findings

### Open-source control projects (maturity snapshot)
- **Gaggiuino** (Zer0-bit): "A Gaggia Classic control project using microcontrollers"; 2.7k stars, 387 forks, 2,380 commits; legacy STM32 BlackPill code on branch release/stm32-blackpill; the README page does not mention Gen 3 ([GitHub](https://github.com/Zer0-bit/gaggiuino), fetched 2026-11-10). Docs: targets Gaggia Classic family with 3-way valves, excluding Classic V2; Gen 1 Nano+Nextion, Gen 2 STM32+Nextion, Gen 3 STM32+ESP32; flow profiling absent on Gen 1, present on Gen 2/3 ([docs site](https://gaggiuino.github.io/)). Source status: the project site says Gen 3 is free with free updates but source is not available, under a non-commercial Creative Commons licence, per a Hackaday commenter quoting it ([Hackaday 2022 comments](https://hackaday.com/2022/11/20/homebrew-espresso-maker-modding-with-gagguino/)). Aftermath reports Zer0-bit said the code stays private because of scalping and moved to an "open-core" model ([Aftermath](https://aftermath.site/gaggiuino-gaggia-classic-pro-mod-open-source-hack/)). A third-party review reports the public repo has no firmware on its default branch and last commit April 2025 ([Synopolis](https://synopolis.com/gaggiuino-profiling-and-temperature-control-for-gaggia-classic-machines/)). Verdict: source-available/closed for current generation, not open source in the OSI sense. I could not confirm the LICENSE text from the repo page itself.
- **GaggiMate** (Jochen Niebuhr): ESP32, touch display, web UI, BLE/WebSocket integration surface, OTA with stable/beta/nightly channels ([fork README via search](https://github.com/carloshrdezc/gaggimate)). Upstream repo: CC BY-NC-SA 4.0 (non-commercial), about 995 stars, 306 forks, 154 open issues, 1,122 commits; creator sells a kit at shop.gaggimate.eu; hardware design files moved to gaggimate/parts ([GitHub](https://github.com/jniebuhr/gaggimate), fetched 2026-11-10). A 2026 build write-up used a GaggiMate Pro with firmware v1.9.0 ([Ulrich Lehner](https://www.ulrichlehner.com/blog/gaggia-classic-gaggimate-pid/)). The gaggimate org has a Home Assistant integration updated September 2026 ([GitHub org](https://github.com/gaggimate)). Kit price not found.
- **CleverCoffee** (rancilio-pid): GPL-2.0, ESP32 only going forward, 418 stars, 189 forks, 1,416 commits, "active development for over 5 years", v4.0.0 with browser web-flasher, official PCB, supports Rancilio Silvia, Gaggia, Quickmill; temperature PID (not pressure profiling) ([GitHub](https://github.com/rancilio-pid/clevercoffee)). Genuinely open, but a temperature-control project.
- **Other PID projects**: Perfect Coffee PID (ESP32), silvia-pi (Raspberry Pi), a Gaggia ESP32-C6 controller with HA/Grafana ([search result](https://github.com/petoz/gaggia_pid_esp32-c6)). One ESP32 Silvia author states the stock v1 swings up to 20 C ([kolkman](https://kolkman.github.io/ESP32ressoMachine)).
- **Decent**: DE1 machine firmware is closed and accepts only signed firmware (forum recollection of John Buckman, a UL-approval rationale claimed by a poster, unverified) ([Home-Barista](https://www.home-barista.com/espresso-machines/decent-espresso-machine-t43925-1020.html)). Tablet app and API are described as open source by Decent ([same thread](https://www.home-barista.com/espresso-machines/decent-espresso-machine-t43925-1020.html)). pyDE1: GPL-3.0, 81 stars, 377 commits, author uses it daily, needs Python 3.8+, bleak, MQTT 5 broker ([GitHub](https://github.com/jeffsf/pyDE1)). Decent Open Scale firmware GPLv3 ([GitHub](https://github.com/decentespresso/openscale)).
- **Meticulous**: Kickstarter updates state APIs are open and documented, the server runs on the machine with no forced cloud, TypeScript and Python clients on GitHub ([Kickstarter](https://www.kickstarter.com/projects/meticulous/meticulous-espresso/posts/4119462)). Community: Home Assistant integration via zeroconf/Socket.IO ([ha-meticulous](https://github.com/cjborchert/ha-meticulous)), MeticAI, MCP server ([MeticAI](https://github.com/hessius/MeticAI)). Not confirmed: full firmware/schematics openness (only third-party marketing says so).
- **diyPresso**: kit with open-source Arduino MKR WiFi 1010 control. One: EUR 1,250, 0.6 L custom copper boiler, 390x210x365 mm, 18 kg, no steam; Two: EUR 1,695 incl. VAT, 1300 W copper boiler + 1200 W thermoblock for steam, 21 kg, about 8-week lead time ([diyPresso One](https://www.diypresso.com/product/diypresso-one/), [Two](https://www.diypresso.com/product/diypresso-two/), observed 2026-11-10, EU). Firmware 1.8.0 (Jan 2026) adds Dynamic Feed Forward, vendor claims 60-80% better temperature stability (vendor claim, unverified) ([downloads](https://www.diypresso.com/downloads/)). Repo: GPL-3.0 code, 141 stars; no hardware design files visible; OTA on to-do ([GitHub](https://github.com/diyPresso/diyPresso-One)). Review: about 5 hours assembly (via search summary). Hackaday: "might not be the cheapest road" but economical for a proven design ([Hackaday 2024](https://hackaday.com/2024/09/15/an-espresso-machine-for-the-diy-crowd)).

### From-scratch and heavily custom builds (all anecdote, forum-level evidence)
- **"Building a lever machine.... from scratch"** (HB t41716, 36+ pages): builder converted a lathe to CNC over about a month while waiting for a foundry casting; prototyped group in aluminium machined from solid stock (final part under a quarter of stock volume); floating piston head to absorb axial misalignment in the first cast group body; worried about uncertified bar stock and lead ([page 3](https://www.home-barista.com/levers/building-lever-machine-from-scratch-t41716-20.html), [page 4](https://www.home-barista.com/levers/building-lever-machine-from-scratch-t41716-30.html)). Cost view: a single unit is far too expensive; around ten units costs slightly more than a comparable reseller machine; time not counted ([first page](https://www.home-barista.com/levers/building-lever-machine-from-scratch-t41716.html)).
- **Open boiler lever**: about EUR 280 parts, commenter says 70-80 hours ([HB t40964](https://www.home-barista.com/levers/another-homemade-open-boiler-lever-t40964.html)). Another builder: about 120 hours and about EUR 1,300 materials, time untracked. A $350 all-aluminium build with cartridge heaters and PID, about 3 minute warm-up (via search summary of HB threads).
- **Open Source Lever Project** (HB t39181): bought spring-lever group about $495, two Ascaso 1000 W thermoblocks about $25 each, 7075 aluminium plates, PID per block, thermoblock recovery about 60 s after a flush; goal was no machining and mostly off-the-shelf parts ([thread](https://www.home-barista.com/levers/open-source-lever-project-t39181.html)). Dated (years old).
- **Modern DIY double boiler lever** (HB t89560): 1500 W single 2 L boiler target with 1.5 bar steam, La San Marco group, 1200 W thermoblock preheating ([page 3](https://www.home-barista.com/levers/modern-diy-double-boiler-lever-build-t89560-20.html)).
- **Four Bar Design**: avoided a heavy high-ratio lever by using 12/16 g CO2 cartridges (about 2.6 g per pull, about $0.15 per shot), custom CNC stainless parts $102, author admits aversion to spending money "was almost certainly going to cost me more in time" (paraphrase) ([post, 2020](https://www.fourbardesign.com/2020/10/diy-espresso.html)).
- Other: Instructables lever machine from bar stock ([link](https://www.instructables.com/How-to-Make-a-Lever-Espresso-Machine/)); Hackaday 2018 motorbike-parts machine and 2020 lever press ([Hackaday](https://hackaday.com/2020/04/08/impressive-lever-press-espresso-machine-has-finesse)).
- Common lessons: plan several iterations; group head and boiler are the hardest and costliest parts to source; copper sheet is costly; time is under-counted; savings only at volume.

### Mixed manual/automatic lever designs (relevant to the reader's goal)
- Modern hybrid levers: group heated separately, electronic flow control, pressure relief valve ends the shot, a lever movement or switch triggers flow, check valve holds water in the group ([HB explainer](https://www.home-barista.com/levers/how-modern-hybrid-lever-espresso-machines-work-t89513.html)). Spring-lever builds are noted as semi-manual: the user can assist the spring to shape the profile ([HB](https://www.home-barista.com/levers/building-myself-nice-spring-lever-machine-t82218.html)).
- Servo-assisted lever: only forum musings (raise, lower, stop hands-free) with debate on losing hands-on feel ([HB first-lever thread](https://www.home-barista.com/levers/first-lever-build-diy-or-start-with-manufactured-espresso-machine-t73683.html)). No documented, parts-listed build found. This is a gap and an opportunity.

### Engineering fundamentals
- **Pumps**: vibratory vs rotary: neither inherently makes better coffee; rotary quieter (about 55-60 dB claimed) and longer-lived, can be plumbed in; vibratory about 5-6 years home life; rotary usually uses a bypass, vibratory an OPV ([Clive Coffee](https://clivecoffee.com/blogs/learn/vibratory-vs-rotary-pump-espresso-machines-compared)). A forum user found rotary pumps hard to flow-profile with a needle valve and favoured vibe or gear pump (single anecdote) ([HB](https://www.home-barista.com/advice/rotary-or-vibratory-pump-t74726.html)). Gear pump/brushless data not found.
- **Lead and materials**: NSF/ANSI 372 limit 0.25% lead (2,500 ppm); NSF 51 allows brass up to that for coffee equipment; EDF petitioned to remove it ([EDF](https://blogs.edf.org/health/2021/01/12/lead-brass-and-bronze-food-equipment/), [Dalla Corte](https://www.comunicaffe.com/dalla-corte-machines-now-certified-as-lead-free/)). Daily Coffee News: NSF standard works on weighted share across parts, so a small leaded valve can pass ([article](https://dailycoffeenews.com/2019/10/29/get-the-lead-out-the-longstanding-challenge-of-lead-in-espresso-machines/)). Forum: "lead-free" brass even in EU is "low lead" ([HB](https://www.home-barista.com/espresso-machines/stainless-steel-boiler-copper-piping-confusion-t82142.html)). Electroless nickel opinions conflict.
- **Pressure vessel rules**: UK Pressure Systems Safety Regulations 2000 apply to steam-making machines and treat fluid over 0.5 bar as a pressure system ([Stratford DC leaflet](https://www.stratford.gov.uk/doc/212173/name/Coffee%20Machines%20as%20Pressure%20Systems%20HS%20Leaflet.pdf/)); Virginia's act covers hobby boilers (NDT, R-stamp welder) ([VA code](https://law.lis.virginia.gov/vacodepopularnames/boiler-and-pressure-vessel-safety-act/)). Forum says espresso boilers are a "grey area" ([HB](https://www.home-barista.com/repairs/diy-espresso-machine-build-boiler-pressure-rating-t64985.html)). Retail safety valve 2.1 bar for home machines; most boilers run about 1-1.5 bar ([EspressoParts](https://www.espressoparts.com/products/espresso-machine-1-4-boiler-safety-valve)). Advice: no brazed/oxy-acetylene boiler joints, use professional welding (forum). PED not found.
- **Electrical**: earth as fault path, RCD/GFCI trips on element insulation failure, thermal fuse on elements; forum disagreement on GFCI value for all-metal machines ([Papel Espresso](https://www.papelespresso.com/espresso-electrical-safety-basics/), [HB](https://www.home-barista.com/repairs/voltage-on-frame-t94576.html)). No authoritative standard found.
- Not found: group designs comparison (E61/saturated), PID tuning, transducers, flow meters, water chemistry. Rely on background knowledge, unsourced here.

### Recommendation (my synthesis, not sourced evidence)
Modify-first. Take a machine with an accessible pump and valves, add an open controller, and put the unique work in a lever/servo-assist and motor-drive layer. Estimates from the anecdotes above: kit controller mods are weekend-scale (diyPresso kit about 5 h assembly); open-boiler lever from scratch 70-120 h and about EUR 280-1,300; a cast or machined spring group needs a workshop, a month of tooling, and multiple iterations. A spring-lever group bought as a part (about $495 in one thread) plus thermoblocks is the lowest-risk route to a "works by hand, can run automated" machine. Keep boiler pressure below the 0.5 bar regulatory threshold where possible (thermoblocks, or open/unpressurised boiler) to sidestep pressure-vessel issues. Licences: GaggiMate and Gaggiuino are non-commercial/closed; CleverCoffee (GPL-2.0), pyDE1 and diyPresso code (GPL-3.0) are open.

## Quote bank
No quotes could be verified to the standard (primary source, second search). Search results quoted these items; all WEAK/SECONDARY and unverified by a second search.

> The decision to keep the code private stems from prolonged issues with scalping, which has been a significant challenge for the past year or so
Zer0-bit (Gaggiuino developer), statement on the Gaggiuino Discord, date unknown, SECONDARY (quoted by Aftermath), [source](https://aftermath.site/gaggiuino-gaggia-classic-pro-mod-open-source-hack/). Second search did not return the original Discord post.

> Making ten or so will result in a slightly higher cost per unit than buying something comparable from a reseller. Making a hundred changes that substantially... And of course, none of this is counting my time.
HB forum user building a lever from scratch (username not captured), date unknown, WEAK (forum anecdote), [source](https://www.home-barista.com/levers/building-lever-machine-from-scratch-t41716.html). Not re-checked.

> Gaggiuino Gen 3 is free to use and will offer free software updates, but the source code is no longer available.
Attributed by a Hackaday commenter to the Gaggiuino team, 2022-23, WEAK, [source](https://hackaday.com/2022/11/20/homebrew-espresso-maker-modding-with-gagguino/). Not re-checked.

## Disagreements, failure modes and caveats
- "Open source" is contested: Gaggiuino (non-commercial CC, Gen 3 closed) and GaggiMate (CC BY-NC-SA) are source-available, not OSI-open; CleverCoffee and pyDE1 are GPL.
- Gaggiuino repo state: GitHub page shows 2,380 commits on a public repo, while Synopolis says the default branch has no firmware. Not reconciled.
- Decent: UL rationale for closed firmware is an unverified forum claim.
- Vendor claims (diyPresso 60-80% stability, Meticulous openness) are unverified marketing.
- Forum cost/time data are sparse, self-reported, undated in places and old (the Open Source Lever Project dates from roughly 2015).
- Builders warn on boiler welding and lead; none of this replaces local regulations.
- Failure stories found: misaligned first cast group body, uncertified bar stock, thermoblock group-temperature sensing unresolved, time overruns. No catastrophic-failure reports were searched for.

## Sources
- Gaggiuino GitHub, Zer0-bit, fetched 2026-11-10, https://github.com/Zer0-bit/gaggiuino: primary; licence text not shown.
- Gaggiuino docs, https://gaggiuino.github.io/: primary.
- GaggiMate GitHub, jniebuhr, fetched 2026-11-10, https://github.com/jniebuhr/gaggimate: primary.
- CleverCoffee GitHub, https://github.com/rancilio-pid/clevercoffee: primary.
- pyDE1, Jeff Kletsky, https://github.com/jeffsf/pyDE1: primary.
- diyPresso One repo and site, https://github.com/diyPresso/diyPresso-One, https://www.diypresso.com/downloads/: primary; vendor claims.
- Aftermath article on Gaggiuino, https://aftermath.site/gaggiuino-gaggia-classic-pro-mod-open-source-hack/: secondary press, undated in my result.
- Synopolis review, https://synopolis.com/gaggiuino-profiling-and-temperature-control-for-gaggia-classic-machines/: single reviewer.
- Hackaday 2022, 2024, https://hackaday.com/2022/11/20/homebrew-espresso-maker-modding-with-gagguino/ : comments are weak.
- Meticulous Kickstarter update, https://www.kickstarter.com/projects/meticulous/meticulous-espresso/posts/4119462: primary company statement.
- Home-Barista threads (t41716, t39181, t89560, t40964, t43925, t89513): forum anecdote.
- Four Bar Design, https://www.fourbardesign.com/2020/10/diy-espresso.html: primary blog.
- EDF Health, https://blogs.edf.org/health/2021/01/12/lead-brass-and-bronze-food-equipment/: advocacy but factual on standards.
- Daily Coffee News, 2019-10-29, https://dailycoffeenews.com/2019/10/29/get-the-lead-out-the-longstanding-challenge-of-lead-in-espresso-machines/: trade press, only fragments seen.
- Clive Coffee pump guide, https://clivecoffee.com/blogs/learn/vibratory-vs-rotary-pump-espresso-machines-compared: retailer.
- Stratford DC pressure-systems leaflet (UK), Virginia boiler act: regulatory/primary.

## Gaps
- Search budget exhausted at 23 searches; GaggiMate kit price and real-world reviews, Gaggiuino total cost, boiler vs thermoblock vs thermocoil, E61/saturated group detail, pressure transducers, flow meters, OPV set values, gear/brushless pumps, water chemistry/scale were not searched.
- No YouTube or Reddit builds surfaced.
- No official statement on PED/CE or NSF route for a one-off machine.
- No documented servo- or motor-assisted lever build with parts list.
- Gaggiuino LICENSE text and Gen 3 source location unconfirmed; GaggiMate star/release data come from one fetch.
- Meticulous firmware/schematic openness unconfirmed.
- No verified direct quotations meeting the two-search standard.

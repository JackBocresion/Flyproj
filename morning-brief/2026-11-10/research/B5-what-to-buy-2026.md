# B5 - What to buy in 2026: machines, modding platforms and budget tiers

## Scope
Buyer's guide for a math/CS person who wants a mixed manual/automatic espresso setup (lever feel, self-contained, automatable, bedside), a motor-assistable hand grinder, and a water plan. Covers what matters in a machine, tinker platforms with 2025-26 prices and tariff notes, Breville vs high-end Italian tradeoffs, three budget tiers, and water. Neighbouring slices (B1 scratch builds, B2 levers/hybrids, B3 grinders/motors, B4 bedside robotics) are deliberately not duplicated.

## Method and search log
Method: WebSearch only (non-GitHub fetch blocked). 32 searches used (the cap). Results are mostly retailer pages, affiliate reviews and forum threads; primary-voice quotes from Hoffmann, Hedrick and Gagne could NOT be surfaced, so no quotes from them appear. Prices are observed snippets from search results, dated where the source gave a date; all need a live check.

1. GaggiMate vs Gaggiuino kit price 2026 (standard) - GaggiMate shop EUR prices; no official Gaggiuino price; Gaggia Classic Up 2026 reviews.
2. Gaggia Classic Evo Pro E24 price tariff review (standard) - US/UK/EU prices; brass boiler vs older aluminium; no tariff info.
3. Decent DE1 API price tariff (standard) - mostly noise; Decent tariff blog (20% rate, July 2025).
4. Meticulous price/API (standard) - $1,350 preorder history; no open API confirmed; thin independent reviews.
5. Rancilio Silvia Pro X price (standard) - about $2,195 US.
6. Breville Dual Boiler Slayer mod / Oracle Jet (standard) - only Slayer-brand pricing (wrong product); no mod info.
7. Lelit Bianca V3 price/paddle (standard) - about $2,999.95 US; paddle is manual flow control.
8. La Marzocco Micra/Mini price app (standard) - Micra $3,900-4,500; Mini R $6,600; app conflict.
9. Flair 58 / La Pavoni / Robot / Cremina lever guide (extended) - lever price ranges.
10. Third Wave Water / SCA water standard (standard) - SCA espresso extension quote; DIY recipes.
11. Gagne water recipe (standard) - no figures found; Clive recipe found.
12. Motorized hand grinder conversions (standard) - Flair Power Tower, Skope X, DIY printed adapters, CoffeeGeek torque piece.
13. GaggiMate features/docs (extended) - profile types, Pro kit transducer, ESP32 + SSR, licensing contrast.
14. DE1 API/tablet/BLE (standard) - open source API, 10 Hz BLE cap, pyDE1.
15. Espresso tariffs 2025-26 (standard) - Breville supply-chain shift; Decent tariff page.
16. Hoffmann what matters (standard) - no Hoffmann text; retailer consensus.
17. Hedrick buying advice (standard) - no Hedrick text; retailer disagreement on profiling.
18. Oracle Jet price/reviews (standard) - $1,995-1,999.95; no repairability data.
19. DIY automated lever / linear actuator (extended) - johnrbell/flair_eva_project; asciimike/coffee-tools.
20. Breville Dual Boiler flow control mod (standard) - HB "Slayer shots" thread; needle valve vs dimmer.
21. Decent price page (extended) - DE1PRO $3,699; MASHUP2 $2,999.
22. Meticulous price (standard) - about $1,850 base, about $2,250 all-in per resale posts.
23. Seattle Coffee Gear bench post (extended) - feature ranking; lab protocols for stability.
24. Grinder prices (standard) - Encore ESP, DF64 Gen 2, Mignon Specialita, Niche Zero ranges.
25. Hoffmann transcript attempt (extended) - nothing; Gaggia thermostat swing and sensor offset notes.
26. La Pavoni PID mods (standard) - HB PID threads; no Londinium price.
27. Kinu M47 / Comandante prices (standard) - scattered prices.
28. Smart plug scheduling (standard) - plug ratings, safety cautions.
29. Breville Dual Boiler price (standard) - $1,599.95 US.
30. Gagne temperature/profiling (standard) - nothing specific.
31. Hoffmann profiling (extended) - forum paraphrase; Decent founder concession about Hoffmann.
32. Profitec Pro 800 / Elektra / Cremina prices (standard) - Pro 800 about $3,199-3,299 (2022-dated page); others none.

## Findings

### 1. What matters in a home machine (evidence vs opinion)
- Consensus (retailer opinion, not measured): boiler configuration/temperature stability is the foundation; PID beats thermostat; dual boiler suits back-to-back milk drinks. [Seattle Coffee Gear](https://www.seattlecoffeegear.com/blogs/scg-blog/the-espresso-machine-features-you-actually-want) says its bench ranks PID, shot timer and flow control as the features affecting shots; its measured numbers were not in the snippet.
- Evidence on stock Gaggia thermostat: one blog says thermostat hysteresis lets brew temperature vary by as much as 15 C, and a PID reads boiler, not group, temperature with a 5-12 C offset depending on source (PID setpoints near 103-104 C suggested). Anecdotal/blog, sources disagree. [Cal Bryant / Papel Espresso results](https://www.papelespresso.com/ideal-pid-temperature-settings-for-light-roast-espresso-on-a-gaggia-classic/), [Balance Journal](https://balancejournal.co/food-drink/gaggia-classic-temperature-surfing).
- Measurement protocols exist: a lab protocol wants first shot within 1 C of heated average; another uses group thermocouples over 50 shots targeting +/-0.5 C. [Kaffeemacher protocol](https://kaffeemacher.ch/en/blogs/kaffeewissen/espresso-machines-test-protocol).
- Pressure/flow profiling: opinions split. Vendor (Clive) says it makes espresso more forgiving; [Complete Home Barista](https://completehomebarista.com/faqs/equipment/buying/pressure-profiling-worth-it/) says marginal gains for most, worthwhile for experimenters. Decent's own docs claim flow profiling alone is not guaranteed better than pressure profiling and that pressure is the finer knob ([Decent docs](https://decentespresso.com/docs/are_flow_profiles_better_than_pressure_profiles)). Decent's founder reportedly conceded Hoffmann was right on a pressure-vs-flow peak near 8.6 bar (forum relay, unverified, see Quote bank).
- Needle-valve (Slayer-style) caveat: it controls flow, not pressure; advice is to master fixed-pressure shots first. [Home-Barista thread](https://www.home-barista.com/espresso-machines/breville-dual-boiler-slayer-shots-t54849-420.html).
- Warm-up, 58 mm group, serviceability, parts: no solid quantitative source found in this search set (see Gaps).

### 2. Tinker platforms (prices as observed; US unless noted)
- **Gaggia Classic Evo Pro / E24 / "Classic Pro E24"**: US $499 at [Whole Latte Love](https://www.wholelattelove.com/collections/gaggia/products/gaggia-classic-pro); TechRadar list $549/GBP549 ([TechRadar](https://www.techradar.com/home/coffee-machines/tired-of-espresso-machines-you-have-to-micromanage-for-great-results-i-tested-one-that-satisfies-coffee-snobs-with-no-effort)); EUR 443-531 at [aio.lv](https://aio.lv/en/product--gaggia-886948115010--10482287.md) (2026). E24 has a brass boiler (2023 Evo Pro was aluminium) per [Coffee Kev](https://coffeeblog.co.uk/?p=5421). Thermoblock steam, slow milk, plastic accessories ([Tom's Guide](https://www.tomsguide.com/home/coffee-makers/gaggia-classic-e24-evo-pro-review)). A 2026 "Classic Up" revision exists with flow profiling built in ([Tom's Coffee Corner](https://tomscoffeecorner.com/gaggia-classic-up-2026-review/), [Expert Reviews](https://www.expertreviews.co.uk/home-garden/small-appliances/coffee-machines/gaggia-classic-up-review)).
- **GaggiMate** (open source, ESP32, touchscreen, web UI, BLE/WebSocket, SSR + PID): Standard Kit from EUR 152.49, Pro Kit from EUR 213.49 (shop page, stock sometimes zero) [shop.gaggimate.eu](https://shop.gaggimate.eu/products/gaggimate-pro-kit). Pressure transducer and full pressure/flow profiles need Pro. Docs: [docs.gaggimate.eu](https://docs.gaggimate.eu/). A [community MCP server](https://archestra.ai/mcp-catalog/matvey-kuk__gaggimate-mcp) exists, which hints at scriptability; repo reportedly github.com/jniebuhr/gaggimate (from search text, check). Build writeups: [Magnus Jensen](https://magnusjensen.dev/blog/20251111-gaggimate), [Ulrich Lehner](https://www.ulrichlehner.com/blog/gaggia-classic-gaggimate-pid/).
- **Gaggiuino** (STM32): [project](https://gaggiuino.github.io/); no official kit price found; one reviewer says it has partly gone closed and requires high effort; kit via Peak Coffee often backordered; Reddit estimate $200-400 kit (anecdote). A 2026 estimate puts Classic + Gaggiuino at $700-900 total.
- **Decent DE1PRO**: $3,699 list, MASHUP2 $2,999 sale, stock limited ([decentespresso.com/price](https://decentespresso.com/price)). Tablet software and API open source ([overview](https://decentespresso.com/de1)); BLE capped near 10 messages/s per founder; third-party control via [pyDE1](https://pypi.org/project/pyDE1/0.8.0/). Tariff note July 2025: shipped to US tariffs prepaid, reduced rate of 20% under high-tech exemption, price is "to your door" ([Decent blog](https://decentespresso.com/blog/trumps_tariffs_impact_on_your_decent_espresso_purchase)). A "Bengle" model page exists ([decentespresso.com/bengle](https://decentespresso.com/bengle)), described with built-in tablet and two USB-C ports; price/specs unconfirmed.
- **Meticulous**: robotic electronic lever, ten sensors, scale in drip tray ([TechCrunch CES 2025](https://techcrunch.com/2025/01/07/meticulous-shows-off-its-smart-espresso-machine-at-ces-2025)). Resale posts in 2026 cite $1,850 base, roughly $400 tax/tariff/shipping, about $2,250 all-in ([Home-Barista](https://www.home-barista.com/buysell/meticulous-espresso-machine-denver-t104774.html)). Open API not confirmed; independent reviews scarce; one owner says automated lever did not suit a lever user ([HB thread](https://www.home-barista.com/advice/are-you-happy-with-your-meticulous-espresso-machine-t104729.html)). Steam wand sold separately.
- **Rancilio Silvia Pro X**: about $2,195 US ([Whole Latte Love](https://www.wholelattelove.com/products/rancilio-silvia-pro-x-dual-boiler-espresso-machine)); dual boiler, dual PID. Reviews are largely retailer/affiliate. Base Silvia PID mods are a long-standing tinker route (not priced here).
- **Lelit Bianca V3**: about $2,999.95 US ([Whole Latte Love](https://www.wholelattelove.com/collections/lelit/products/lelit-bianca-v3-dual-boiler-espresso-machine)); manual rotating flow paddle at group plus optional electronic low-flow mode. One summary flags thin build material as a downside. Lelit is owned by Breville since 2022 ([Wikipedia result](https://en.wikipedia.org/wiki/Lelit)).
- **La Marzocco**: Micra $3,900-4,500 ([Gear Patrol](https://www.gearpatrol.com/drinks/la-marzocco-linea-micra-review/), [Coffeedant](https://coffeedant.com/?p=167)); Mini R about $6,600 at [Clive](https://clivecoffee.com/collections/espresso-machines/products/la-marzocco-linea-mini-espresso-machine). Home app handles scheduling, temperature, pre-brew. Source conflict on whether the original Mini has app ([Balance Journal](https://balancejournal.co/food-drink/la-marzocco-linea-mini-review) says Mini R only).
- **Breville Dual Boiler (BES920)**: about $1,599.95 US ([Whole Latte Love](https://www.wholelattelove.com/breville-bes920xl-dual-boiler-espresso-machine); [Barista Life](https://baristalife.co/blogs/blog/breville-oracle-jet-vs-dual-boiler), Aug 2026). Slayer-style needle-valve mod: one guide says under $60, 1-2 hours, reversible; kits $200-350 ([Complete Home Barista](https://completehomebarista.com/guides/breville-dual-boiler-flow-control-mod/), guides contradict each other). Dimmer on vibration pump discussed as alternative. Also a Breville/Sage Infuser/Barista profiling mod thread ([HB](https://www.home-barista.com/repairs/breville-sage-infuser-pressure-temperature-profiling-mod-t102215.html)). Warranty impact not sourced.
- **Breville Oracle Jet**: $1,995-1,999.95 ([Tom's Guide](https://www.tomsguide.com/home/coffee-makers/breville-oracle-jet-review), [TechRadar](https://www.techradar.com/home/coffee-machines/breville-oracle-jet-review)); automatic grind, dose, tamp; thermojet-style heating. No repairability data; original Oracle tamp complaints reported, unconfirmed for Jet; ProductReview.com.au 3.5 on 6 reviews. Breville Oracle Dual Boiler reported at $4,500 (company high).
- **Tariffs**: Breville said it is shifting production out of China to Mexico/Indonesia, China exposure about 40% of purchases (July 2025) falling to about 10% by Jan 2026, and warned of higher US input costs in 2026-27 ([ChannelNews](https://www.channelnews.com.au/breville-to-shift-production-out-of-china-as-coffee-remains-growth-driver/)). A Canadian roaster page says a Section 122 tariff ended July 24, 2026 and Section 301 tariffs began (unclear relevance to espresso gear) ([Rogue Wave](https://roguewavecoffee.ca/pages/tariff-duties-for-u-s-customers)). No specific EU-to-US tariff figures for Lelit/Rancilio/Profitec found.

### 3. Lever and lever-hybrid options (feeds B2)
- Manual levers: Flair 58 about $434-650 depending on model (Plus 2 $640-699 at [CNN Underscored](https://www.cnn.com/cnn-underscored/reviews/best-manual-espresso-maker)); Cafelat Robot about $350-450; La Pavoni Europiccola about $750-1,100 (boiler + steam); Olympia Cremina about $3,650-3,800 (single source) ([comparison](https://stillwatercoffee.ca/blogs/brew_hacks/flair-58-vs-cafelat-robot-vs-la-pavoni-europiccola)).
- Lever hybrids: Profitec Pro 800 (lever-actuated, dual boiler) US $3,199-3,299 on a page dated July 2022 ([Whole Latte Love](https://www.wholelattelove.com/products/profitec-pro-800-lever-group-espresso-machine)), EUR 2,499 at a European retailer; Lelit Bianca paddle; Meticulous (robotic lever); Decent (no lever, but flow/pressure control).
- Tinker evidence for automating a lever: [johnrbell/flair_eva_project](https://github.com/johnrbell/flair_eva_project) (Flair 58 + two linear actuators + ESP32, TMC2209, 0-1.2 MPa sensor; author notes pressure sensing not quite there); [asciimike/coffee-tools](https://github.com/asciimike/coffee-tools) (BLE pressure sensor + scale); La Pavoni PID threads on [Home-Barista](https://www.home-barista.com/repairs/la-pavoni-pid-better-temperature-control-t17073-180.html) (Auber PID, RTD, SSR; high/low switch kept as heater selector). Actuator sizing lesson: stronger gearmotor needed than expected to overcome spring (student report). Sensor placement: measure above puck, not at group.

### 4. Breville vs high-end manual Italian: tradeoffs (synthesis, partly opinion)
- Breville: integrated grinder/PID/dual boiler on BES920, strong features per dollar, app-less but modifiable, plastic and thin parts reputation, limited serviceability (no source quantified). Learn: PID tuning, grind dosing, temperature surfing is unnecessary; modding via needle valve or dimmer teaches flow vs pressure.
- High-end manual lever/E61: mechanical, long parts life, repair tradition (La Pavoni community has decades of PID/thermometry mods), more skill for temperature and technique. Learn: thermodynamics of boilers, lever pressure curves, flushing routines. Evidence base is forum anecdote; no failure-rate data found.
- Hybrid insight: a Gaggia + GaggiMate teaches the same control-loop concepts as either, at 1/3 the price, but is a thermoblock-steam, vibration-pump machine rather than a lever.

### 5. Three budget tiers (machine + grinder, with a lever option)
Prices are observed snippets; verify.
- **Tier 1, about $500-900**: Gaggia Classic E24 ($499) + GaggiMate Pro kit (about EUR 213) = about $750-800 incl. shipping; grinder at this tier: hand grinder Kinu M47 (about GBP 263 / EUR 316) or Comandante C40 MK4 ($260-420) or Baratza Encore ESP (about $199, stepped adjustment). Lever option: Flair 58 ($434-650) or Cafelat Robot ($350-450), plus hand grinder; no bedside automation without DIY actuator work. Total with grinder runs over $900 for Gaggia + Kinu.
- **Tier 2, about $1,500-2,500**: Breville Dual Boiler ($1,599.95) + needle valve mod ($60) or Silvia Pro X ($2,195); grinder DF64 Gen 2 ($300-400) or Eureka Mignon Specialita ($350-550). Lever option: La Pavoni Europiccola ($750-1,100) with PID mod + hand grinder, or Meticulous ($1,850 plus about $400 import) if willing to pay near the top of the tier for an electronic lever.
- **Tier 3, $3,500+**: Decent DE1PRO ($3,699; $2,999 MASHUP2 when in stock) with open API, or Lelit Bianca V3 ($2,999.95) / La Marzocco Micra ($3,900-4,500); Profitec Pro 800 (about $3,200) or Olympia Cremina ($3,650-3,800) as lever options; grinder Niche Zero ($650-850) or hand grinder + motor base (Flair Power Tower is compatible with 1Zpresso K-series including K-Ultra).

### 6. Motor-driven hand grinder (feeds B3)
Commercial: [Flair Power Tower](https://flairespresso.com/blog/upgrade-your-1zpresso-grinder-with-the-flair-power-tower) (K-Pro, K-Max, K-Ultra, K-Plus); Skope X adaptors for C40, ZP6, Kinu M47 (Dec 2023 forum post, availability unknown); DIY: [MakerWorld](https://makerworld.com/models/2845866) printed adapter for J-Ultra; [CoffeeGeek torque article](https://coffeegeek.com/opinions/coffee-at-the-moment/the-cordless-espresso-grinder-conundrum-why-torque-is-hard/) argues torque is the obstacle. Home-Barista thread: [hand grinder to electric](https://www.home-barista.com/advice/hand-grinder-to-electric-advice-t100888.html).

### 7. Water for a non-plumbed bedside machine
- SCA espresso guidance: simply scaling up the filter standard would lead to heavy scale; espresso extension allows total hardness as low as 20 ppm CaCO3 and alkalinity up to 150 ppm ([SCA 25 Magazine](https://sca.coffee/sca-news/25/issue-9/english/water-and-coffee-acidity-how-to-adapt-your-water-for-different-extraction-methods-25-magazine-issue-9)). Other pages cite the filter standard inconsistently (68 ppm Ca hardness, 40 ppm alkalinity, 150 ppm TDS); check the SCA original.
- TDS meter cannot verify hardness vs alkalinity separately.
- Third Wave Water espresso packet contents not fully disclosed; HB users speculate on bicarbonate/magnesium sulphate and calcium citrate oddities ([HB](https://www.home-barista.com/water/third-wave-water-t44736-70.html)). Clive recommends packets in distilled water for most home users and a DIY two-concentrate recipe (magnesium sulfate + sodium bicarbonate, about 65 ppm hardness) ([Clive](https://clivecoffee.com/blogs/learn/how-to-build-a-diy-water-recipe-for-espresso-at-home-clive-coffee)). A blog recipe: per litre RO, 0.17 g Epsom salt + 0.10 g sodium bicarbonate gives about 70 ppm hardness, 50 ppm alkalinity (low-quality source; verify by titration).
- Practical: because tank-fed, ensure a rinsed tank, regular descale, never run pure distilled in machines with level probes (some machines need minimum conductivity; not sourced here).
- Bedside scheduling: smart plug must be rated 15-20 A; some users reported melted timers; one guide says schedule about 30 min ahead; heating appliances unattended is a safety judgment, check manuals ([HB smart plugs](https://www.home-barista.com/advice/smart-plugs-t98416.html)).

## Quote bank
No Hoffmann, Hedrick or Gagne direct quotes were obtainable. The following are verbatim from search-result text.

> Our tablet software is open source, as is our API. This allows the community to extend the capabilities of our machine.
Decent Espresso (vendor), undated page, PRIMARY (vendor's own site), [source](https://decentespresso.com/de1)

> Simply scaling up the SCA standard would lead to heavy scale formation. and this leads to an extension of the recommendation at lower total hardness (as low as 20 ppm CaCO3) and especially much higher values of alkalinity of up to 150 ppm CaCO3.
SCA 25 Magazine Issue 9, Specialty Coffee Association, undated, PRIMARY, [source](https://sca.coffee/sca-news/25/issue-9/english/water-and-coffee-acidity-how-to-adapt-your-water-for-different-extraction-methods-25-magazine-issue-9)

> Remember, with a needle valve it's not pressure per se that you are controlling, it's flow.
Home-Barista forum poster (anonymous), undated, WEAK, [source](https://www.home-barista.com/espresso-machines/breville-dual-boiler-slayer-shots-t54849-420.html)

> Hoffmann challenged me years ago on this, and I thought it was both counterintuitive and unlikely. I asked the Decent community to do the research, and it turns out I was wrong, and Hoffmann was right.
Presented as Decent's creator (John Buckman) via forum relay; credentials: Decent founder; undated; WEAK (search relay, not verified on the page), [source](https://www.home-barista.com/marketplace/decent-espresso-news-t66649-2730.html) (page URL uncertain, fact-check)

> bluetooth is limited to 10hz, or 10 messages per second, and what's more, if you send more than that, messages get dropped.
Decent founder per forum relay, undated, WEAK, [source](https://www.home-barista.com/marketplace/decent-espresso-news-t66649.html) (page URL uncertain)

> buy Third Wave Water packets, add one to a gallon of distilled water, and move on with your life.
Clive Coffee (retailer blog), undated, PRIMARY for Clive's view, [source](https://clivecoffee.com/blogs/learn/how-to-build-a-diy-water-recipe-for-espresso-at-home-clive-coffee)

> for $500 I expect more than a crappy plastic tamp.
Tom's Guide reviewer on Gaggia Classic E24, 2025-26, PRIMARY, [source](https://www.tomsguide.com/home/coffee-makers/gaggia-classic-e24-evo-pro-review)

## Disagreements, failure modes and caveats
- Profiling value: vendors (Clive, Seattle Coffee Gear) call it valuable; independent-leaning guide says marginal for most. No controlled taste data found.
- Sensor offset and setpoint disagreements on PID Gaggias (5-12 C).
- Gaggiuino vs GaggiMate: licensing/openness claim from a single reviewer; Gaggiuino kit availability constrained.
- Meticulous: scarce independent reviews; resale listings are the main source; steam wand extra.
- Oracle Jet: price high; failure data absent; tamp complaints from original Oracle.
- La Marzocco Mini app status conflicts; Micra price $3,900 vs $4,500.
- Decent price in 2026 seen at $3,699 vs $2,199 in an old thread; DE1 BLE 10 Hz cap limits closed-loop control from remote apps.
- Forum-mod safety: needle valve and dimmer mods may affect warranty and pump life (unsourced).
- Unattended heating appliance on a bedside table is a fire-safety risk; use rated plugs and manufacturer guidance.
- Complete Home Barista and several "pages.dev" guides look like low-reliability affiliate/AI content; not relied on for numbers.

## Sources
- Whole Latte Love product pages (Gaggia, Silvia Pro X, Bianca V3, BES920, Profitec Pro 800), US retailer, 2022-2026, retail prices; Pro 800 page stale (2022).
- decentespresso.com/price, /de1, /blog/trumps_tariffs..., Decent Espresso, 2025-26, vendor, reliable for own prices.
- shop.gaggimate.eu, docs.gaggimate.eu, GaggiMate, 2026, vendor.
- Tom's Guide, TechRadar Gaggia and Oracle Jet reviews, 2025-26, reputable outlets.
- Gear Patrol Micra review, reputable; Clive Coffee pages, retailer.
- Home-Barista threads (Slayer shots, La Pavoni PID, Meticulous resale, grinder to electric), forum, anecdotal.
- SCA 25 Magazine issue 9, SCA, water chemistry primary.
- ChannelNews Breville tariffs/production, trade press, Aug 2025.
- GitHub johnrbell/flair_eva_project and asciimike/coffee-tools, hobby repos.
- CoffeeGeek torque article, opinion.
- Kaffeemacher test protocol, Swiss reviewer, methodology.
- Seattle Coffee Gear features post, retailer, testing claims.
- Complete Home Barista, daily-grind-guide, pages.dev guides: low reliability.

## Gaps
- No verbatim Hoffmann, Hedrick, Gagne or Kaffeemacher statements; no Home-Barista expert quotes on what matters.
- No live 2026 Gaggiuino kit price; Londinium R24, Elektra, Cremina prices unverified; Profitec Pro 800 price stale.
- No hard data on tariff effects per brand (Italian imports), warm-up times, parts availability or serviceability; no failure-rate data.
- No official Breville US prices for Barista Pro/Touch/Impress; Oracle Jet repairability unknown.
- Gagne's water recipe numbers; Third Wave Water espresso formula.
- GaggiMate Home Assistant support and official API unconfirmed; Meticulous API unconfirmed; Decent Bengle specs/price.
- Whether motorizing Kinu M47 with a drill adapter is available off-the-shelf.

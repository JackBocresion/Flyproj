# B3 - Hand grinders: identifying the knurled crank grinder, and motorising one without ruining it

## Scope
Candidate identification for the brother's knurled, cranked hand grinder; motorising a hand grinder while keeping manual use; grind-by-weight/automation projects; freshness implications of grinding the night before; buy-instead single-dose electric grinders with prices and noise.

## Method and search log
Method: 32 WebSearch calls (search-result text only, plus WebFetch of GitHub READMEs; non-GitHub fetches blocked, printables.com fetch failed with ENOTFOUND). Search tool is US-only and returns summaries, so most numbers are secondary and flagged.

1. 1Zpresso J-Max/J-Ultra/K-Ultra/X-Ultra price comparison (extended) - 2026 prices J-Ultra ~$199, K-Ultra $259-289, X-Ultra $159-169; click sizes.
2. Kinu M47 (standard) - failed, results were shoes.
3. Hand grinder motorize/1Zpresso warranty/drill adapter (extended) - 1Zpresso FAQ drill statement; Aeropress warranty exclusion; Home-Barista stall RPMs; Printables Trifecta; Gawoody kit.
4. 3D printed motor adapters (standard) - Printables/MakerWorld drill adapters; ZP6-A2 Hybrid.
5. Open-source grind by weight ESP32 HX711 (standard) - jaapp, openGBW, ahuber21, CaffePeso.
6. Aroma loss after grinding (extended) - 14% grinding loss (industrial, old), 35% in 30 days paper sachet, 15-min headspace study (no numbers).
7. Drill torque/stall (extended) - ODrive 3 Nm; CoffeeGeek 3-4 Nm; stall RPMs.
8. Prices Niche/DF64/Lagom/Sculptor (extended) - Niche Zero ~$600-690, DF64 G2 $399-450, Sculptor 064S $599.
9. Grinder dB (extended) - no clean numbers; conflicting.
10. Fetch jaapp/smart-grind-by-weight README.
11. Fetch jb-xyz/openGBW README.
12. Pre-ground sensory/grind-ahead (extended) - forum anecdotes only.
13. Freezer/vacuum/nitrogen storage (extended) - SCA literature review; Foods 2025 polyphenol kinetics.
14. RPM, heat, fines (extended) - vendor blogs; one fines/permeability paper.
15. Lagom P64/P100/Niche Duo price (standard) - junk results.
16. One-way clutch/sprag for hand grinder (extended) - no direct example; woodgears.ca keeps crank.
17. Timemore/Kingrinder prices (extended) - C3 $79-99, C5 ESP Pro $115, K6 ~$100-110.
18. Weber HG-2/Helor/Lido/Comandante prices (extended) - HG-2 ~$1,495-1,750; others old guide.
19. Niche Duo (standard) - junk (64 Audio Duo).
20. Kinu M47 retry (standard) - Phoenix ~£189-195, ~US$214; specs.
21. Niche Duo retry (standard) - 83 mm flat burrs, GBP only.
22. dB at 1 m (extended) - Bean Brew Digest 1 m figures; Coffee Chronicler 20 cm.
23. Printables Trifecta fetch - failed (network).
24. CoffeeGeek torque article (extended) - Mark Prince; 3-4 Nm estimate; Amazon Basics 2.5 Nm, HOTO 6 Nm.
25. 1Zpresso FAQ drill wording (standard) - verbatim.
26. Penn State freezing study (standard) - could not confirm; Bath particle-size study.
27. Drill failure stories (standard) - nothing grinder-specific.
28. Ground coffee stale timing (extended) - patent CO2 4-8 days; retailer blogs.
29. Prices round 2 (extended) - Specialita ~$549, Niche $599-649.
30. Home-barista motorizing thread speeds (extended) - 80 rpm saturation, 120 rpm hand speed, 40-50 rpm HG-1 motor, Justin Chae K6 build.
31. GitHub search fetch - 0 results.
32. Identification (extended) - J-Ultra foldable handle, external dial; M47 stepless; C40 slow.
33. (counted within the 32: dB for Sculptor/Niche/DF64) - 73 vs 65 dB Niche; 71 dB DF64 (unsourced tables).
34. (counted within the 32: Akiyama 2003 grinding volatiles) - abstract-level only.

(Calls numbered by purpose; total WebSearch calls = 32.)

## Findings

### 1. Identifying the grinder
Evidence level: retailer/review pages, 2026; prices vary by source.

| Model | Burr | Adjust | Price observed | Notes |
|---|---|---|---|---|
| 1Zpresso J-Ultra | 48 mm conical, steel | 8 micron/click, external dial, foldable handle | ~$199 US store/Amazon | Reviewers' espresso pick; superseded J-Max [roastaroma](https://roastaroma.com/gear/1zpresso-j-ultra), [coffeegearzone](https://coffeegearzone.com/1zpresso-j-ultra-review/) |
| 1Zpresso J-Max | 48 mm conical | 8.8 micron | US$179-209 / CA$249-299 (old listing) | Former flagship espresso [roastaroma compare](https://roastaroma.com/gear/compare/1zpresso-j-max-vs-1zpresso-j-ultra) |
| 1Zpresso K-Ultra | 48 mm | 20 micron/click | $259 (list $289) | Handle tucks in; multi-method [coffeegearzone](https://coffeegearzone.com/1zpresso-k-ultra-vs-x-ultra/) |
| 1Zpresso X-Ultra | 40 mm conical | 12.5 micron | $159 (list $169) | Smallest, most portable [coffeegearzone](https://coffeegearzone.com/1zpresso-x-ultra-review/) |
| Kinu M47 Phoenix | 47/32 mm Black Fusion conical | stepless, 50 divisions x 0.01 mm | ~£189-195, ~€182-220, ~US$214 | Stainless body; 1.4 kg (Simplicity 1.65, Classic 1.85); heavy, very espresso-capable [homegrounds](https://www.homegrounds.co/kinu-m47-review/), [Eight Ounce](https://eightouncecoffee.com/products/kinu-m47-phoenix-grinder) |
| Kingrinder K6 | ~48 mm (disputed; one source says Ti-coated steel) | click | ~$99-110 | Budget, aluminium [thecoffeelocator](https://thecoffeelocator.com/grinders/kingrinder-k6-review/) |
| Timemore C3 ESP | 38 mm stainless | click | ~$79-99 US; £89 UK | [CoffeeGeek budget guide](https://coffeegeek.com/guides/feature-guides/best-budget-coffee-grinders-for-2026/) |
| Timemore C5 ESP Pro | 42 mm heptagonal | click | $115 (Timemore store) | Aluminium alloy body 53 mm [Timemore](https://www.timemore.com/products/timemore-manual-coffee-grinder-chestnut-c5-series) |
| Comandante C40 | Nitro Blade conical | click | ~€219 (old guide) | Filter reference; ~50 s for 20 g; wood handle/body, less likely [thewaytocoffee/coffeechronicler](https://coffeechronicler.com/gear/grinders/manual/best-manual-coffee-grinder/) |
| Weber HG-2 | flat/conical (not verified here) | - | ~$1,495-1,750 US; EUR 1,598 ex-tax | Very high-end [roastaroma](https://roastaroma.com/gear/weber-workshops-hg-2), [espressocoffeeshop](https://www.espressocoffeeshop.com/en/coffee-grinders/1708-weber-workshops-hg-2-macinacaffe-.html) |
| Helor 101 / Lido E-T | - | - | $189-259 / $195 (old guide, unconfirmed) | [coffeegeek.co list](https://coffeegeek.co/en/list-premium-hand-coffee-grinders/) |

I found no source that describes the "knurled barrel" cue explicitly, so it is not a discriminator I can offer from evidence. Practical identification: check for brand engraving on the barrel/crank, the adjustment mechanism (external top dial = 1Zpresso J/K series; bottom ring or stepless numbered dial = Kinu/Comandante), burr size and weight (Kinu 1.4-1.85 kg, notably heavy), and handle (foldable = 1Zpresso). Not covered by search: Fiorenzato Pietro, Lagom Mini, specifics of the Orphan Lido.

Espresso suitability (opinion/review): J-Ultra and Kinu M47 are the espresso picks; X-Ultra, K-Ultra and C40 are filter-leaning [homecoffeeexpert](https://homecoffeeexpert.com/1zpresso-j-ultra-review/), [thewaytocoffee](https://www.thewaytocoffee.com/best-manual-coffee-grinder/).

### 2. Motorising: manufacturer stance
- 1Zpresso official FAQ endorses a drill: a 6.35 mm electric screwdriver/drill fits all its grinders and need not be powerful; advises short runs (one or two cups) to avoid heat [1zpresso FAQ](https://1zpresso.coffee/faq/). Warranty is one year for materials/workmanship; rust and wear not covered [return policy](https://1zpresso.coffee/returnpolicy/). No explicit statement on drill damage.
- AeroPress (different product) explicitly excludes drill-adapter damage from warranty [AeroPress](https://aeropress.com/pages/aeropress-manual-grinder-instructions-page).
- Third parties sell motor kits: Gawoody 1Zpresso Motor Kit [gawoody](https://www.gawoody.com/product-page/gawoody-motor-kit-for-1zpresso), advertised ~160 rpm per search summary (not verified on page).
- Kinu, Timemore, Kingrinder, Comandante official positions: not found.

### 3. Drill/driver community practice, RPM and torque
Evidence is forum anecdote unless noted.
- Stall RPM tests with tachometer (light roast, pourover grind): ~80 rpm 1Zpresso K-Plus, ~70 Kingrinder K2, ~50 ZP6, ~20 K0 [Home-Barista](https://www.home-barista.com/grinders/hand-manual-grinder-drill-turned-t92641.html). Pourover grind understates espresso load.
- Torque: ODrive forum poster measured ~3 Nm at a fine setting and designed for 6 Nm [ODrive](https://discourse.odriverobotics.com/t/research-motorizing-manual-coffee-grinder/6979). CoffeeGeek (Mark Prince, opinion) estimates 3-4 Nm continuous for a comfortable hand grind; 3.6 V screwdrivers (Amazon Basics 2.5 Nm, HOTO 6 Nm peak) struggled for true espresso, with the battery sagging [CoffeeGeek](https://coffeegeek.com/opinions/coffee-at-the-moment/the-cordless-espresso-grinder-conundrum-why-torque-is-hard/). The article also mentions 25-30 Nm "overhead" via gearing, which conflicts; unresolved.
- Speed: one commenter says gains stop ~80 rpm because beans stop feeding [Home-Barista](https://www.home-barista.com/grinders/motorizing-hand-grinder-t11285.html); hand speed ~120 rpm [coffeeforums](https://www.coffeeforums.co.uk/threads/using-an-electric-screwdriver-on-a-hand-grinder.57975/); a Feldgrind user capped ~350-400 rpm on low range [Home-Barista](https://www.home-barista.com/grinders/adapter-for-motorizing-hand-grinder-feldgrind-t93943.html); an HG-1 builder with a constant-torque 120 W motor used 15-80 rpm, mostly 40-50 for espresso [Home-Barista](https://www.home-barista.com/grinders/motorized-hg-1-with-various-speed-t53547.html); a K6 conversion builder reports prior builds at 80-200 rpm limited by stall, heat, gravity feed [Justin Chae](https://www.justinjchae.com/projects/coffee-grinder-conversion). A user on 400 rpm took ~1 min for 14 g and felt little heating.
- Heat/fines vs RPM: general-grinder claims (high RPM shatters, widens distribution, more heat) come from vendor blogs; one vendor lab-style comparison 500 vs 1500 rpm [source](https://completehomebarista.com/guides/grinder-rpm-speed-espresso-extraction/). Not validated for drill-driven hand burrs. Fines reduce bed permeability (peer-reviewed) [PMC10920694](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10920694/). Retention effects of drill vs hand: no data found.
- Implication for design (inference): target high torque (>=6 Nm at crank with margin, a gearmotor or stepper with reduction) at 40-120 rpm, not a fast drill. A stepper/BLDC with planetary gearing gives controllable low rpm; a drill's low gear works but is bulky.

### 4. 3D-printed stands, couplers; manual-preserving designs
- Printables: Trifecta 1Zpresso K-series/ZP6 motorisation [thcecilia](https://www.printables.com/model/836816-trifecta-fancy-1zpresso-grinder-motorization-k-ser) (page not readable here); coffee grinder nut adapter [73286](https://www.printables.com/model/73286-coffee-grinder-nut-adapter-for-cordless-drill-oper); drive adapter [233386](https://www.printables.com/model/233386-coffee-hand-grinder-drive-adapter); Porlex [673529](https://www.printables.com/model/673529-porlex-coffee-grinder-drill-adapter-14-63mm-shaft); Hario [622426](https://www.printables.com/model/622426-hario-handgrinder-14-inch-adapter). MakerWorld: open-source motorised conversion, 24 V, 90-100 rpm [1491498](https://makerworld.com/en/models/1491498-open-source-hand-grinder-motorized-conversion); ZP6-A2 Hybrid using a Femobook A2 motor block (high-torque low-rpm).
- Warning from a Printables description: if the adapter is not seated it "will round out the socket" (search paraphrase).
- Manual-use preservation: no verified example of a sprag/one-way clutch fitted to a hand grinder. Sprag clutches are a standard part [Wikipedia](https://en.wikipedia.org/wiki/Sprag_clutch); woodgears.ca kept the crank attached as emergency use [woodgears](https://woodgears.ca/kitchen/coffee_grinder.html). Hand grinders do not freewheel; the crank spins with the motor unless a clutch or removable coupler is added. My design suggestion (not sourced): a removable coupler at the crank nut, or sprag between motor output and grinder shaft so hand cranking does not back-drive the gearbox (a worm/high-ratio gearbox would otherwise make hand cranking impossible). Magnetic coupling: no evidence found; torque 3-6 Nm makes magnet couplers impractical (inference).

### 5. Grind-by-weight and automation
- jaapp/smart-grind-by-weight [GitHub](https://github.com/jaapp/smart-grind-by-weight): ESP32-S3 AMOLED + HX711 + load cell, ~EUR 30-40 parts, Eureka Mignon Specialita brain swap, target +-0.03 g (design goal, no measured data), predictive latency/flow algorithm, labelled experimental, as-is.
- jb-xyz/openGBW [GitHub](https://github.com/jb-xyz/openGBW): ESP32, HX711 + 500 g load cell, OLED, rotary encoder, relay in parallel with push button (50 ms impulse mode or continuous), Eureka Mignon XL case; no numeric accuracy claim; auto offset after each grind.
- ahuber21/coffee-grinder-scale: ESP32 but ADS1232; notes the 220 V Mignon supply cannot run the ESP32 [GitHub](https://coffee-grinder-scale index via github.imc.re/ahuber21/coffee-grinder-scale). Jerey/coffee-automation [GitHub](https://www.github.com/Jerey/coffee-automation); CaffePeso scale [Home-Barista](https://www.home-barista.com/repairs/caffepeso-open-source-espresso-scale-t103525.html).
- Niche advertises +-0.2 g consistency per a Duo review summary.
- None is for a hand grinder; the concept transfers by switching the motor driver on load-cell weight (inference).

### 6. Freshness
- Evidence: grinding vents volatiles; Akiyama et al. 2003 JAFC captured volatiles released during grinding (nutty, smoky notes richer than in ground-coffee headspace) [paper PDF](https://pages.uoregon.edu/chendon/coffee_literature/old_literature/2003%20J.%20Agric.%20Food%20Chem.,%20Volatiles%20released%20during%20grinding.pdf). Industrial estimate ~14% volatile loss during grinding (old patent text). Ground coffee in paper lost ~35% volatiles in 30 days (secondary summary). CO2 continues to release after grinding over ~4-8 days (patent background, not a study).
- Storage: SCA literature review: nitrogen flushing gave 6 months vs 3 months sensory shelf life (2001 study); temperature correlates with CO2/volatile loss, largest losses in first days [SCA](https://sca.coffee/sca-news/2012/02/15/what-is-the-shelf-life-of-roasted-coffee-a-literature-review-on-coffee-staling-bjcx7). 2025 Foods study: vacuum best for beans, valved foil best for ground, at 25 C [PMC12607991](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC12607991/). Freezing: Penn State finding that freezing helps dark roasts (secondary, unverified) [Mental Floss](https://www.mentalfloss.com/article/81672/keeping-coffee-beans-freezer-may-improve-taste-study-finds). A temperature/storage volatile study exists [PMC11675256](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC11675256/).
- Grind-ahead (anecdote only): Home-Barista user found 12 h pre-ground sweeter than fresh but poor extraction viewed; another said noticeable degradation after 24 h, dead at 48 h, 6-12 h acceptable; a 359-shot Medium log found no trend [Medium](https://medium.com/data-science/coffee-grounds-freshness-for-espresso-78a447f84fcd), [Home-Barista](https://www.home-barista.com/knockbox/pre-grinding-coffee-for-later-t100030.html).
- Implication (inference): grinding ~8 h before wake-up in a sealed container is likely a modest loss; best design grinds at wake-up (noise vs bed) or grinds the night before into a sealed dosing cup. No controlled sensory data on this window.

### 7. Buy-instead (2026, US$ unless noted, secondary)
- Niche Zero: ~$599-689 US; GBP 559 direct (UK) [Stillwater](https://stillwatercoffee.ca/blogs/brew_hacks/turin-df64-vs-niche-zero-vs-timemore-064s), [Knowledgelib](https://knowledgelib.io/home/kitchen/coffee-grinders/2026).
- Niche Duo: 83 mm flat, two burr sets; GBP 549-799 depending on source; no USD price found; reviewers mixed (fines, cleanliness) [brewcoffeehome](https://www.brewcoffeehome.com/niche-duo-vs-zero/).
- DF64 Gen 2: $399-450 [coffeeness](https://www.coffeeness.de/en/timemore-sculptor-064s-review/).
- Timemore Sculptor 064S: ~$599 [roastaroma](https://roastaroma.com/gear/timemore-sculptor-064s); 064S II orders opened Oct 2026, shipping early 2027 (per one source).
- Eureka Mignon Specialita: ~$549 ($449-749 band).
- Lagom P64/P100: no price confirmed; HB thread says P100 ~$1,000 above P64 with SSP burrs, Lagom with SSP $1,585 (old).
- Noise: Bean Brew Digest 1 m, dB(A): Eureka Silenzio 59, DF64 Gen 2 62, Comandante C40 hand 43 [beanbrewdigest](https://beanbrewdigest.com/equipment-gear/what-is-the-most-quiet-coffee-grinder-available). Coffee Chronicler at 20 cm: hand ~72-74, quietest electric ~80, DF64 Gen 2 noticeably louder [coffeechronicler](https://coffeechronicler.com/gear/grinders/best-quiet/). Niche Zero 65 dB (unsourced table) vs ~73 dB (forum) [completehomebarista](https://completehomebarista.com/coffee-grinders/burr-grinder-noise-comparison/). Specialita ~80 dB at 20 cm [quietest.org](https://www.quietest.org/quietest-coffee-grinder-decibels/). Distances differ; not comparable.

## Quote bank
> The 6.35mm electronic screwdriver/drill is applicable to all the 1Zpresso grinders and it doesn't need to be a powerful one.

1Zpresso (manufacturer FAQ), n/a, undated, PRIMARY, [source](https://1zpresso.coffee/faq/)

> We suggest using a drill for one or two cups within a short period of time, or it could get hot and affect the taste.

1Zpresso (manufacturer FAQ), n/a, undated, PRIMARY, [source](https://1zpresso.coffee/faq)

> our warranty does not cover damage to the Grinder both cosmetic and mechanical through use of the Power Drill Adapter

AeroPress (manufacturer instructions page; wording as in search extract), undated, PRIMARY (different product), [source](https://aeropress.com/pages/aeropress-manual-grinder-instructions-page)

> With a fine grind setting I measured about 3 Nm, so assuming 6 to have some headroom.

ODrive forum poster (unnamed hobbyist), undated, WEAK (single forum post), [source](https://discourse.odriverobotics.com/t/research-motorizing-manual-coffee-grinder/6979)

> Newly Released Mod - Buyer Beware!

jaapp, README author of smart-grind-by-weight, undated, PRIMARY, [source](https://github.com/jaapp/smart-grind-by-weight)

> the accuracy will increase with each grind

jb-xyz, openGBW README, undated, PRIMARY, [source](https://github.com/jb-xyz/openGBW)

> The 12 hours pre-ground coffee was better tasting and sweeter than the fresh ground batch.

Home-Barista forum user (anonymous), undated, WEAK, [source](https://www.home-barista.com/brewing/experiments-with-preground-coffee-for-espresso-and-brew-pot-t6722.html)

> We suggest using... (see above). Other quotes held to paraphrase: CoffeeGeek's 3-4 Nm estimate (Mark Prince, opinion piece) is paraphrased only.

## Disagreements, failure modes and caveats
- Torque: ~3 Nm (forum measurement) vs 3-4 Nm (CoffeeGeek estimate); CoffeeGeek also mentions 25-30 Nm overhead, inconsistent with its tool ratings. Drill spec "400-600 Nm" claims on forum are likely in-lb or max-stall misreads; treat as unreliable.
- Speed: manufacturer says any drill; community says low rpm (~50-150) and enough torque; 3.6 V screwdrivers stall at espresso.
- Heat: 1Zpresso warns of heat on prolonged use; user reports little heating at 400 rpm for 14 g. No measurements.
- Burr material of K6 disputed; M47 vs J-Ultra opinions conflict (one reviewer found M47 harder to use with no consistency gain).
- Niche Zero dB: 65 vs 73; DF64 62 vs ~71 vs "86" in another chart.
- Freshness: grind-ahead evidence is anecdote and conflicting (sweeter at 12 h vs dead at 48 h).
- Motor risks (inference): side load on crank bearing and shaft from drill; rounded nut sockets; no manufacturer warranty protection; ESP32 powering from 220 V Mignon supply may fail.
- Failure stories specific to drilling hand grinders: none found.

## Sources
- 1Zpresso FAQ, 1zpresso.coffee/faq, undated: official, primary.
- 1Zpresso return policy, 1zpresso.coffee/returnpolicy: official.
- AeroPress grinder instructions, aeropress.com: official, different product.
- Home-Barista threads t92641, t11285, t93943, t53547, t77059, t100030, t6722, t72555, t103525: forum, anecdotal.
- ODrive discourse thread 6979: hobbyist engineering, one measurement.
- CoffeeGeek (Mark Prince) torque article; CoffeeGeek budget/manual guides 2025-26: reputable outlet, opinion.
- github.com/jaapp/smart-grind-by-weight, jb-xyz/openGBW, ahuber21/coffee-grinder-scale, Jerey/coffee-automation: primary READMEs (first two read directly).
- Printables/MakerWorld models listed above: maker pages, unverified here.
- SCA literature review (2012): reputable secondary review.
- PMC12607991 (2025), PMC11675256, PMC10920694: peer-reviewed.
- Akiyama et al. 2003 JAFC PDF at pages.uoregon.edu: peer-reviewed; abstract-level only.
- Review/retail sites (roastaroma, coffeegearzone, coffeeness, beanbrewdigest, coffeechronicler, stillwatercoffee.ca, knowledgelib, completehomebarista, Kaffeemacher, Eight Ounce): mixed quality, SEO-driven; prices indicative.

## Gaps
- Printables/Thingiverse pages not fetchable (printables.com not allowed); designs unverified for torque, clutch or manual-use support.
- No verified sprag-clutch or magnetic-coupling hand-grinder build.
- No controlled data on drill rpm vs fines, heat, retention.
- No peer-reviewed minutes/hours grind-age sensory study; Penn State freezing study not verified; no good-quality ground-coffee freezer data.
- Lagom P64/P100 and Niche Duo USD prices; Sculptor dB; reliable like-for-like dB table.
- Fiorenzato Pietro, Helor 101, Lido specifics; knurling identification; official Kinu/Timemore/Kingrinder motor stances.
- GitHub repos for motorised hand grinders: search surface returned nothing.

## Verification log (independent fact-check)
Checked 2026-11-10 with 16 WebSearch calls (no non-GitHub WebFetch). Search results are model-written summaries, so a verbatim quote is marked VERIFIED only when its exact wording surfaced in the results.

- **PARTIAL** — Quote: "applicable to all the 1Zpresso grinders... doesn't need to be a powerful one" (1Zpresso FAQ). Note: the substance (any 6.35 mm drill, no power needed) is confirmed on the FAQ and in a Home-Barista quote of it. The exact wording surfaced only in summaries, and a near-identical line appears on DACLL's FAQ, so the wording may be shared across brands. Use a paraphrase or re-check the page. URL: https://1zpresso.coffee/faq/
- **PARTIAL** — Quote: "We suggest using a drill for one or two cups within a short period..." (attributed to 1Zpresso FAQ). Note: the verbatim wording was found on DACLL's FAQ (https://www.dacll.com/faq-ezp-6.html), not 1Zpresso's. The 1Zpresso attribution is unconfirmed; the one-to-two-cup advice itself is only paraphrased for 1Zpresso. Re-attribute or drop the quote marks. URL: https://1zpresso.coffee/faq/
- **PARTIAL** — Quote: "our warranty does not cover damage to the Grinder both cosmetic and mechanical..." (AeroPress). Note: the warranty exclusion for cosmetic and mechanical damage from the Power Drill Adapter is confirmed on AeroPress's own support pages, but only as a paraphrase in the results. Verbatim wording not seen. URL: https://aeropress.com/pages/aeropress-manual-grinder-instructions-page
- **VERIFIED** — Quote: "the accuracy will increase with each grind" (openGBW README). Note: the exact sentence surfaced in the README text ("the accuracy will increase with each grind as the scale auto adjusts the grinding offset"), and forks carry the same sentence. Primary source. URL: https://github.com/jb-xyz/openGBW
- **VERIFIED** — Quote: "With a fine grind setting I measured about 3 Nm, so assuming 6 to have some headroom" (ODrive forum). Note: exact wording surfaced in the thread excerpt. It is one anonymous forum post, so the evidence weight stays WEAK. URL: https://discourse.odriverobotics.com/t/research-motorizing-manual-coffee-grinder/6979
- **PARTIAL** — Quote: "The 12 hours pre-ground coffee was better tasting and sweeter than the fresh ground batch." (Home-Barista). Note: the thread exists and reports that a 12-hour pre-ground batch was preferred. The exact wording was not shown in results. The thread is one informal test, and other sources (Better Coffee Lab) point the other way. URL: https://www.home-barista.com/brewing/experiments-with-preground-coffee-for-espresso-and-brew-pot-t6722.html
- **NOT_FOUND** — Quote: "Newly Released Mod - Buyer Beware!" (jaapp README). Note: searches of the jaapp repo and related pages did not return this text. Drop the quote or fetch the README directly. URL: https://github.com/jaapp/smart-grind-by-weight
- **PARTIAL** — Finding: Akiyama et al. 2003 JAFC, grinding volatiles. Note: the paper exists (J. Agric. Food Chem. 2003, 51, 1961-1969, "Analysis of Volatile Compounds Released during the Grinding of Roasted Coffee Beans Using SPME"). It states that grinding aromas are lost easily during industrial processing. The file's claim that they are richer than ground-coffee headspace was not confirmed. Cite the title and the loss point only. URL: https://pages.uoregon.edu/chendon/coffee_literature/old_literature/2003%20J.%20Agric.%20Food%20Chem.,%20Volatiles%20released%20during%20grinding.pdf
- **PARTIAL** — Finding: Bean Brew Digest dB(A): Silenzio 59, DF64 Gen 2 62, Comandante C40 43. Note: the figures appear on the Bean Brew Digest guide (secondary, retail blog). The 43 dB is a peak measured during full-torque cranking, which the file omits. The "1 m" distance was not confirmed in the results. Other sites (Quietest.org) report hand grinders at roughly 70-75 dB on a different basis, so the figures are not comparable. URL: https://beanbrewdigest.com/equipment-gear/what-is-the-most-quiet-coffee-grinder-available
- **VERIFIED** — Finding: 1Zpresso J-Ultra ~$199. Note: $199 confirmed on the manufacturer store and by Tom's Guide (Amazon US). Some resellers charge $213-222. Secondary press plus primary store listing. URL: https://1zpresso.coffee/product/jultra
- **VERIFIED** — Finding: 1Zpresso X-Ultra $159 (list $169). Note: the manufacturer's US store shows current $159, original $169, tax excluded. The page is undated, so the price may have moved. Other retailers list $181 or more. URL: https://1zpresso.coffee/product/xultra
- **PARTIAL** — Finding: Niche Zero ~$599-689 US; GBP 559 direct. Note: a 2026 price guide gives $599-649 USD and a May 2026 review cites about $629. The UK figure of £559 appears at Balance Coffee; Niche's own UK store showed £538.80 inc. VAT. The $689 upper bound was not found. Correct the US range to about $599-649. Searches were run on the price and burr specs (63 mm conical), not on the $689 figure. URL: https://completehomebarista.com/guides/niche-zero-price-guide-2026/
- **VERIFIED** — Finding: DF64 Gen 2 $399-450. Note: the US maker's store lists $399 (sale) against a $450 regular price. Other retailers show $389-400 and one shows a $599 regular price. Prices are volatile; check live listings. URL: https://df64coffee.com/a/s/products/df64-gen-2-single-dose-coffee-grinder
- **VERIFIED** — Finding: SCA review, nitrogen-flushed coffee sensory shelf life 6 months vs 3 months (2001). Note: the SCA literature review states it, citing Alves et al. 2001 (ASIC, Trieste). An abstract on ResearchGate gives the same 6 vs 3 months at 25 C / 65% RH. The full 2001 text was not read. URL: https://sca.coffee/sca-news/2012/02/15/what-is-the-shelf-life-of-roasted-coffee-a-literature-review-on-coffee-staling-bjcx7
- **CONTRADICTED** — Finding: Kinu M47 Phoenix 1.4 kg. Note: the researcher's own cited source (Home Grounds) lists the Phoenix at 1.6 lb (about 0.73 kg). Green Plantation and MyCoffeeStage also give about 715 g. Only Eight Ounce Coffee gives 1.4 kg. Use about 0.7 kg, or drop the figure. URL: https://www.homegrounds.co/kinu-m47-review/

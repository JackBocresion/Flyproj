## Part 2: Espresso to the bedside

**Bottom line.** Build the bedside machine as modules, and get each one working by hand before it gets a motor. Any motor you add should only push, never hold, so that cutting the power leaves an ordinary manual tool. That means three steps. First, motorise a hand grinder through a one-way clutch so the crank still works, and dose by weight. Second, fit a push-only actuator to a cheap direct lever (a Cafelat Robot, about $399) and learn the force and profile problem there. Third, combine the two in one enclosure with a thermoblock, a heated group, and a controller you arm by hand at night that brews at the alarm. Make the Americano the default drink. If you want a daily machine while you build, a Gaggia Classic Pro with a GaggiMate Pro kit (about $499 plus EUR 213) is a cheap, scriptable pressure-profiling setup. It is not a lever. My estimate for the full build is $1,250-2,200 in parts and a winter of weekends. Nobody has documented this exact machine, so treat that estimate as having fat tails.

Prices are approximate, US retail unless marked, as seen in listings around 10 November 2026. Check them before buying.

### What to look for in a machine

Start with the heat source. Boilers act as a heat battery: slow to warm (roughly 5-30 minutes) but stable. Thermoblocks heat in seconds to a minute and hold only a few millilitres, so they store almost no energy, which is what you want on a nightstand. The buying guides disagree widely on these numbers ([Craft Coffee Spot](https://craftcoffeespot.com/espresso/thermoblock-vs-thermocoil-vs-boiler/)), so read them as orders of magnitude.

A PID controller reads boiler temperature, not group temperature. Blogs put the offset on a Gaggia at anywhere from 5 to 12 C, which is unverified and contested.

Next, you need a pressure source you can command. The options are a vibration pump with phase-angle control (the Gaggiuino and GaggiMate approach), a speed-controlled gear pump, a spring, or your arm. Automation also needs a transducer. A 0-12 bar stainless one costs about $38 ([Peak Coffee](https://www.peakcoffee.cc/product/gaggiuino-pressure-sensor/)), though that is the vendor's price and a cached copy of the page showed $18.

Watch what touches the water. CW617N is a leaded brass, and the "lead-free CW617N" you will see advertised does not exist ([IFAN](https://www.ifanholding.com/news/cw617n-lead-free-brass)). NSF/ANSI 372 caps lead at a 0.25% weighted average over wetted surfaces ([NSF](https://standards.nsf.org/higherlogic/ws/public/download/55131/372i5r1%20-%20Normative%20Reference%20-%20JC%20Memo%20%26%20ballot.pdf)). It is a drinking-water standard, and I could not confirm how it applies to coffee gear. In anything you build, use 316 stainless wherever water touches.

Finally, make sure there is a way in. Breville shows the problem, whichever model your girlfriend has: the Dual Boiler BES920 is a lot of machine for $1,599.95 ([Breville US](https://www.breville.com/en-us/product/BES920)). But its automation hooks are the app on Wi-Fi models or a relay hack, plus one explicitly unofficial Home Assistant integration that lists only the Oracle Dual Boiler ([sageha](https://github.com/simonjgreen/sageha)).

### How a lever makes pressure

On a direct lever (Robot, La Pavoni, Cremina) your arm is the pump. Brew pressure is handle force times mechanical advantage, divided by piston area, and the advantage changes with lever angle. On a spring lever (Strega, Profitec Pro 800, Elektra, Londinium), lifting the handle compresses a spring and lets water into the cylinder. When you let go, the spring does the work.

Take spring rate *k*, preload *x*₀ at the bottom of the stroke, and piston area *A*. With the piston a height *s* above the bottom, pressure is roughly *P(s) ≈ k(x₀ + s)/A*, less seal friction. At constant flow *Q*, the piston falls at *ds/dt = −Q/A*, so pressure falls linearly in time. In a real shot the puck erodes and flow rises, so the decline steepens toward the end. The preload sets the end pressure and the stroke adds the peak, which is why swapping the spring changes both.

A lever retailer's blog describes one illustrative shot that peaks at 8.6 bar and falls to 3.7 bar ([The Lever Blog](https://thelevermag.com/blogs/articles/decent-espresso)); that is one shot, not a benchmark. Other sources claim peaks from 7.5 to 12 bar, but none shows a transducer trace (unverified). On force, one Home-Barista user's bathroom-scale reading came to about 24 lb at the handle for 6 bar and about 40 lb for 9 bar ([Home-Barista](https://www.home-barista.com/levers/pressure-profiling-la-pavoni-t34126.html); the post may sit in a related Cremina profiling thread). Other estimates for 9 bar run from 25 to 48 lb. Use these for rough actuator sizing only.

@@PROFILE@@

The case that a declining profile tastes better comes mostly from people who sell machines. Decent, which sells pump machines that imitate lever curves, argues that 9 bar is a leftover from 1940s spring sizes ([Decent](https://decentespresso.com/blog/the_nine_bar_question)). I found no controlled taste trial.

### Machines that work by hand and can be automated

| Machine | Mechanism | Automation route | Price (approx.) | Honest drawback |
|---|---|---|---|---|
| Cafelat Robot | Direct lever, no electronics | None built in; good actuator testbed | $399 ([Prima](https://prima-coffee.com/brew/espresso/home/cafelat/)) | No heater; you supply hot water |
| La Pavoni Europiccola EPC-8 | Direct lever on small boiler | PID and pressurestat mods | $1,108 ([WLL](https://www.wholelattelove.com/products/la-pavoni-europiccola-epc-8-espresso-machine)); $989 on sale at another retailer | Owners report the group overheats after 2-3 shots |
| Olympia Cremina | Direct lever, Swiss | Bluetooth portafilter sensors for logging | $4,305 ([Cerini](https://www.cerinicoffee.com/products/olympia-express-cremina-espresso-machine-made-in-switzerland)) | Price; same thermal juggling |
| Elektra Micro Casa a Leva | Spring lever on boiler | Little | $1,599 when tested ([CoffeeGeek](https://coffeegeek.com/reviews/firstlooks/elektra-micro-casa-a-leva/)); about $2,029 at one retailer now | Group heat is a known con |
| Bezzera Strega | Spring lever plus vibe pump | Pump fill is electric; lifting the lever cuts the pump | $2,699 ([WLL](https://wholelattelove.com/bezzera-strega-lever-espresso-machine)) | Owners complain of pump noise |
| Profitec Pro 800 | Spring lever, pump only fills, dual boiler | Little | $3,199-3,299 ([WLL](https://www.wholelattelove.com/products/profitec-pro-800-lever-group-espresso-machine)); $2,968 on sale elsewhere | Nothing to hook into |
| Lelit Bianca V3 | Rotary pump, manual flow paddle | Hand profiling at the paddle | $2,999.95 ([WLL](https://www.wholelattelove.com/products/lelit-bianca-v3-dual-boiler-espresso-machine)) | Not a lever |
| Meticulous | Motor-driven piston, ten sensors | Open API, per the maker | $1,350 CES 2025 preorder ([TechCrunch](https://techcrunch.com/2025/01/07/meticulous-shows-off-its-smart-espresso-machine-at-ces-2025)); current retail unconfirmed | No lever for a hand |
| Gaggia Classic Pro E24 + GaggiMate Pro | Vibe pump, small boiler, ESP32 | Web UI, WebSocket, pressure and flow profiles | $499 sale, $549 list ([WLL](https://www.wholelattelove.com/collections/gaggia/products/gaggia-classic-pro)) plus EUR 213.49 | Not a lever; plastic accessories |

The Strega comes closest to your brief: pump for the fill, spring for the extraction, lever as the switch. But nothing on it accepts a command.

Meticulous is the mirror image. It has ten sensors and a scale under the drip tray ([SCA](https://new.sca.coffee/entries/meticulous-espresso)), and a July Kickstarter update says the API is open, with TypeScript and Python clients ([Kickstarter](https://www.kickstarter.com/projects/meticulous/meticulous-espresso/posts/4143589)). But you can't pull it by hand, and the $1,850 retail price that circulates is unverified.

New and expensive does not mean reliable. CoffeeGeek's Mark Prince headlined his piece on the new Olympia Mina "A Beautiful, Frustrating Swiss Paradox" (12 Nov 2025), and it relays a valve failure after about a month of daily use ([CoffeeGeek](https://coffeegeek.com/opinions/coffee-at-the-moment/olympia-mina-beautiful-flawed-paradox/)). Decent's DE1 is a very scriptable pump machine. Decent says its tablet software and API are open, and pyDE1 is GPL-3.0 ([pyDE1](https://github.com/jeffsf/pyDE1)). I couldn't verify its current price, so it isn't in the table.

### If you would rather buy than build

Three tiers, using only prices the fact-checker could confirm (US, approximate, November 2026). The cheapest tier is the one that automates best, which tells you where the money in this project should go.

| Tier | Machine | Grinder | Rough total | Lever alternative |
|---|---|---|---|---|
| About $600-1,000 | Gaggia Classic Pro E24 ($499 sale, $549 list) plus GaggiMate Pro (EUR 213) | 1Zpresso J-Ultra ($199) | about $950 | Cafelat Robot ($399) plus J-Ultra, about $600; you supply hot water |
| About $1,500-2,700 | Breville Dual Boiler ($1,599.95) or Rancilio Silvia Pro X (about $2,195) | DF64 Gen 2 ($399-450, [DF64](https://df64coffee.com/a/s/products/df64-gen-2-single-dose-coffee-grinder)) | about $2,000-2,650 | La Pavoni Europiccola ($1,108) plus J-Ultra, about $1,300 |
| $3,500 and up | Lelit Bianca V3 ($2,999.95) or La Marzocco Linea Micra (about $3,900, [Gear Patrol](https://www.gearpatrol.com/drinks/la-marzocco-linea-micra-review/)) | Niche Zero (about $599-649, [price guide](https://completehomebarista.com/guides/niche-zero-price-guide-2026/)) | about $3,600-4,550 | Profitec Pro 800 ($3,199-3,299) or Olympia Cremina ($4,305) |

Only the first row has a documented pressure-and-flow automation path. The Silvia Pro X already has dual PIDs, and the open CleverCoffee project targets the base Silvia and controls temperature only. The Breville's hooks are the ones described above. The middle and top tiers buy temperature stability and steam. They do not buy anything that helps with getting a cup to the bedside.

### Three build paths

| Path | Parts (approx.) | Time | Skills | Main risk |
|---|---|---|---|---|
| 1. Modify a pump machine | $750-900 | 1-3 weekends | Mains wiring, crimping, light plumbing | Mains faults; licence limits |
| 2. Lever plus added automation | $800-2,000 | 2-4 months of weekends | Mechanism design, motor control | Actuator sizing, kickback, heat |
| 3. From scratch | $1,500-4,000 | 100-300 h | Machining, pressure plumbing, safety | Pressure vessel, lead, time |

Times, and the costs for paths 2 and 3, are my estimates from the anecdotes below.

**1. Modify an existing machine.** The GaggiMate Pro kit is EUR 213.49 on the official shop, with about a two-week restock ([GaggiMate shop](https://shop.gaggimate.eu/products/gaggimate-pro-kit)). You need the Pro rather than the Standard (from EUR 152.49) for pressure and flow profiles. The repository has 995 stars and a CC BY-NC-SA 4.0 licence ([GitHub](https://github.com/jniebuhr/gaggimate)). Its releases page marks v1.9.0 (29 September) as latest; the docs still say v1.7.3, so trust the releases page. Upstream describes an automatic shutoff if the controller hangs or overheats, which is the feature you want most at a bedside.

Gaggiuino is older and bigger, with 2.7k stars and 2,380 commits ([GitHub](https://github.com/Zer0-bit/gaggiuino)). Aftermath reports that its author took the current generation closed-source because of scalpers, in an "open-core" model ([Aftermath](https://aftermath.site/gaggiuino-gaggia-classic-pro-mod-open-source-hack/)). Costs are forum anecdote: $388 for one premium kit, and about $400 in one [build log](https://kozikow.wordpress.com/2024/02/22/gaggiuino-build-log/) that says going below $250 is hard. If you want a properly open licence, CleverCoffee is GPL-2.0 ([GitHub](https://github.com/rancilio-pid/clevercoffee)), but it only controls temperature.

This path ends with a scriptable machine, but no lever, grinder or bedside cup.

**2. A lever or lever hybrid with automation added.** You've ruled out a robot arm on an unmodified machine. An actuator built into the frame, through a coupling that can only push, is a different thing: retract it and the lever is just a lever. The closest precedent is Alex Moyse's 2018 La Pavoni project. He used a refurbished 500 lb Thomson linear actuator that he called "complete overkill for the La Pavoni" ([alexmoyse.com](https://alexmoyse.com/?page_id=75)). I found no record of the result, or of whether the lever still worked by hand. One GitHub project puts two linear actuators and an ESP32 on a Flair 58; its author says pressure sensing isn't there yet ([flair_eva_project](https://github.com/johnrbell/flair_eva_project), unverified).

From the force readings above, about 180 N (40 lb) at the handle covers 9 bar. Double it for stiction and you have a small lead-screw actuator, not a 500 lb one. Forum posters warn that Pavoni internals aren't really built for a steady 9 bar ([Home-Barista](https://www.home-barista.com/levers/robo-pavoni-learning-to-make-espresso-machine-from-scratch-t4141.html)), which points to the Robot as the testbed.

A spring lever is simpler in one way: the motor only cocks it, so the profile stays mechanical. It is worse in another, because a spring lever can kick back hard if something releases it under load (my reasoning, not sourced). I found no consumer motor-assisted spring lever, so this is open ground.

**3. From scratch.** One open-boiler lever took about EUR 280 in parts and an estimated 70-80 hours. Another took about 120 hours and EUR 1,300. A 36-page thread, "[Building a lever machine.... from scratch](https://www.home-barista.com/levers/building-lever-machine-from-scratch-t41716.html)", includes a month spent converting a lathe to CNC while the builder waited for a casting. (All unverified forum figures.) diyPresso is a halfway house: open firmware, One at EUR 1,250 (no steam), Two at EUR 1,695 ([diyPresso](https://www.diypresso.com/product/diypresso-one/)). Hackaday said it "might not be the cheapest road to obtaining an espresso machine" ([Hackaday, 2024](https://hackaday.com/2024/09/15/an-espresso-machine-for-the-diy-crowd/)).

The hard limits are regulatory. The EU Pressure Equipment Directive applies only above 0.5 bar, and anything under its Article 4(1) thresholds falls under "sound engineering practice" ([PED guidelines](https://www.ce-richtlinien.eu/richtlinien/Druckgeraete/Leitlinie/PED_2014-68-EU_Guidelines_EN_v6.0.pdf)). I couldn't confirm where those thresholds fall for a small boiler. So skip the steam boiler and use thermoblocks. If you do build a boiler, fit a certified, marked safety valve. One retailer sells 2.1 bar valves for home boilers and warns never to fit a lower-rated one or bypass it ([Espressoparts](https://www.espressoparts.com/products/espresso-machine-1-4-boiler-safety-valve)). Others still sell 1.8 bar valves, so match the boiler's rating.

For a pump-driven build, the natural actuator is a Fluid-o-Tech FG gear pump: 316L, 24 V brushless, speed-controlled, 30-210 l/h, up to 12 bar ([Fluid-o-Tech](https://www.fluidotech.it/en/products/technologies/external-gear-pumps/fg200-300-series/)). Prices are all over the place: $880-1,331 new at one dealer depending on the snapshot, and about $600 new or $95 used per forum posts.

### Your brother's grinder

I can't identify it from the description. A metal barrel with knurling and a crank fits half the premium hand grinders on sale, and no source treats knurling as a distinguishing mark. A few checks narrow it quickly:

- Look for engraving on the barrel, the crank arm or the top nut.
- See where the adjustment is. An external numbered dial just under the crank suggests a 1Zpresso J-Ultra or K-Ultra (the J-Ultra's handle also folds). A stepless numbered ring suggests a Kinu M47.
- Weigh it. A Kinu M47 Phoenix is about 0.7 kg ([Home Grounds](https://www.homegrounds.co/kinu-m47-review/)); one retailer's 1.4 kg figure is contradicted elsewhere.
- Wooden parts suggest a Comandante, which leans toward filter.

For reference, the reviewers' espresso pick, the 1Zpresso J-Ultra, is $199 ([1Zpresso](https://1zpresso.coffee/product/jultra)), and the X-Ultra is $159 ([1Zpresso](https://1zpresso.coffee/product/xultra)).

**Motorising it.** 1Zpresso is relaxed about this. Its FAQ says any 6.35 mm (1/4 inch) drill fits all its grinders and doesn't need to be powerful ([1Zpresso FAQ](https://1zpresso.coffee/faq/); paraphrased, since the same wording appears on a rival's FAQ). The advice to run a drill only briefly to avoid heat is verbatim on a rival's FAQ, so I haven't attributed it to 1Zpresso. AeroPress excludes drill-adapter damage from its own grinder's warranty. I found no stated policy from Kinu, Timemore or Comandante.

On torque, a hobbyist on the ODrive forum wrote: "With a fine grind setting I measured about 3 Nm, so assuming 6 to have some headroom" ([ODrive forum](https://discourse.odriverobotics.com/t/research-motorizing-manual-coffee-grinder/6979)). One anonymous measurement. Measure your brother's grinder yourself: hang a luggage scale from the crank knob and multiply by the radius. At a 6 cm crank, 3 Nm is about 5 kgf. On speed, forum reports (unverified) put hand cranking near 120 rpm and say throughput stops improving around 80 rpm because the beans stop feeding. One builder ran a motorised HG-1 at 40-50 rpm for espresso. So you want a gearmotor or geared stepper giving 6-10 Nm at 40-120 rpm, not a drill at 400.

**Keeping the crank.** A hand grinder doesn't freewheel. Bolt a motor to the shaft and the crank goes along for the ride, and a geared motor acts as a brake when you crank by hand. I found no documented build that solves this. The design I'd try replaces the crank nut with an adapter stub. The crank refits on top of the stub. Below it sits a timing-belt pulley on a sprag (one-way) clutch, driven by a gearmotor mounted to the side. When the motor drives, the sprag locks and turns the shaft. When you crank, the shaft overruns the stationary pulley and the motor is never back-driven. Support the stub in its own bearing in the frame and join it to the grinder shaft with an Oldham or jaw coupling. That keeps belt tension off the grinder's top bearing and absorbs misalignment. A soft-jawed collar around the barrel takes the reaction torque, which is the knurling's moment to be useful.

**Grind by weight.** Two open ESP32 projects use an HX711 and a load cell. [openGBW](https://github.com/jb-xyz/openGBW) adjusts its overshoot offset after each grind: "the accuracy will increase with each grind". [smart-grind-by-weight](https://github.com/jaapp/smart-grind-by-weight) aims for ±0.03 g, which is a design goal with no measured data, and calls itself experimental. Both target Eureka electric grinders. A single-dose hand grinder allows simpler control: weigh the beans in, grind to empty, and detect empty when motor current drops to idle.

One guide rates a Comandante C40 at 43 dB(A), a peak during full-torque cranking, against 59 for a Eureka Silenzio and 62 for a DF64 Gen 2 ([Bean Brew Digest](https://beanbrewdigest.com/equipment-gear/what-is-the-most-quiet-coffee-grinder-available)). The distance isn't stated, and another site puts hand grinders at 70-75 dB on a different basis. Hand grinders are probably quieter, but the published numbers can't be compared.

### Concept: a Teasmade for espresso

The Teasmade goes back to patents from 1891 and 1902 (Rowbottom, then Clarke, per the enthusiast site [teasmade.uk](https://www.teasmade.uk/1891-samuel-rowbottom)); Goblin brought it to market in the mid-1930s. Its cycle ends itself. An alarm clock switches on a sealed kettle, and steam pressure pushes the water into the pot. The empty kettle then releases a switch beneath it, which cuts the element and sounds the buzzer ([Hackaday](https://hackaday.com/2020/01/30/retrotechtacular-teasmade)). If the seal leaks, you just get no tea. That failure is benign, and that is the property to copy.

The Barisieur ($445, or $399 on offer in 2019 per [Salon](https://www.salon.com/2019/04/06/this-coffee-maker-alarm-clock-will-change-your-am-game)) lets you choose before, at or after the alarm, but it brews filter coffee. The robot cafes are the warning. Cafe X closed its San Francisco sites in January 2020 and its airport sites that August ([ABC7](https://abc7news.com/post/robot-baristas-cafe-x-closes-sf-locations-/5830767/)). Briggo's enclosed kiosk became Costa's BaristaBot ([BevNET](https://www.bevnet.com/news/2020/costa-coffee-acquires-rebrands-briggo-machine-as-baristabot/)), and the enclosed, fixed layout is the design that was acquired rather than closed. Arms aren't ready for this. An SO-101 costs about $100-130, and the best documented result I found is 17 of 20 cube placements on one fixed setup ([HF model card](https://huggingface.co/omiya239532/so101_act_cotrain)).

**Architecture.**

| Component | Choice | Why |
|---|---|---|
| Heat | About 1 kW thermoblock for brew and Americano water, a 100-200 W cartridge heater in the group, a PID on each, and bimetal cutouts wired in series outside the firmware | Little stored energy; group mass handled separately |
| Pressure | Lever group with a push-only actuator (a roller in an open cradle under the lever, free when retracted); a small pump fills the cylinder at low pressure, as on the Strega | Profile stays mechanical; a hand can do everything |
| Grinder | The sprag-coupled motorised hand grinder | Crankable with the power off |
| Dosing | Beans pre-weighed into a sealed tube at night; ground through a funnel into a basket on a load cell; spring-loaded tamper on a lead screw | Puck prep is the hard chore; kiosks only solved it in enclosed machines |
| Basket | Drawer portafilter on a rail: out to dosing, in under the group, cam-lifted to seal | Superautomatic brew units show dose-tamp-eject fits in a shoebox (my inference; untested with a lever) |
| Water | 1-1.5 L tank, level sensor, low-water heater cutout; one Third Wave Water packet per gallon of distilled or RO water, as Clive suggests ([Clive](https://clivecoffee.com/products/third-wave-water-packets-12-pack)) | No plumbing at a bedside |
| Cup | Fixed bay with cup-presence load cell, drip tray level sensor, double-wall glass | No cup, no brew |
| Control | ESP32 for real-time loops (GaggiMate as reference); Home Assistant or phone alarm over MQTT for timing | Interlocks don't depend on Wi-Fi |
| Trigger | A physical "arm" button pressed at night, then the alarm time; never runs unarmed | A queue for tomorrow, not a daily habit |
| Manual override | Actuator retracts clear of the lever; crank on the grinder; a switch that keeps heaters and PIDs but drops the scheduler | It should be a decent manual machine with the brain unplugged |

**Rough bill of materials** (my estimates unless sourced):

| Item | Approx. cost |
|---|---|
| Spring-lever group as a part (about $495 in one old forum thread, unverified), or a Robot to start | $400-600 |
| Thermoblock, group heater, PIDs, SSRs, thermal fuses | $100-200 |
| Pressure transducer ($38, vendor price) and Digmesa flow meter (roughly GBP 8-78) | $60-150 |
| Lead-screw lever actuator (about 500 N) and driver | $80-200 |
| Grinder gearmotor, sprag pulley, belt, bearings, coupling | $80-150 |
| Load cells, HX711s, ESP32s, display | $40-80 |
| 316L fittings, PTFE hose, valves, tank, enclosure | $300-600 |
| Hand grinder if not borrowed (J-Ultra) | $199 |
| Total | about $1,250-2,200, before mistakes |

**Build phases.**

1. Bench rig: thermoblock, PID and transducer on a plate, logging to a laptop. Characterise warm-up and the temperature dip at shot start. Builders warn that a block can lag the opening burst of flow, and that flow-based feed-forward helps ([Home-Barista](https://www.home-barista.com/espresso-machines/diy-espresso-machine-dual-thermoblock-dual-piston-pump-single-group-t77501.html)).
2. Grinder module, from torque measurement to grind-by-weight.
3. Lever module: hand shots with logging, then the actuator replaying your own curves.
4. Dosing and the drawer. This will take longest.
5. Interlocks, arm-and-expire logic, scheduling.
6. A month at the bedside with a phone decibel meter and a shot log.

**Constraints.**

The thermal budget is easy to work out. Heating water from 20 to 93 C takes about 305 J/g, so 1 kW delivers about 3.3 ml/s. That covers a 40 g shot in 30 seconds and 150 ml of Americano water in under a minute, and it agrees with a forum back-of-envelope figure of about 3 ml/s. The group is the slow part. Raising a 2.5 kg brass group by 70 K takes about 66 kJ, or about 7 minutes at 150 W before losses, so plan a 15-20 minute pre-alarm start. Don't leave a dosed basket in a hot group. The SCA's staling review links higher temperature to faster volatile loss ([SCA](https://sca.coffee/sca-news/2012/02/15/what-is-the-shelf-life-of-roasted-coffee-a-literature-review-on-coffee-staling-bjcx7)), which is why this design grinds and doses a few minutes before the alarm.

On noise, let the grinder be the alarm. It is the loudest part of the cycle either way, and grinding three minutes before you wake gives fresher coffee. Pump noise figures are only estimates (60-75 dB for vibe pumps in one guide), and how the pump is mounted matters as much as which type it is.

For scald and fire safety: no steam boiler, an RCD-protected outlet, a thermal fuse in series with each heater, and a tilt switch. Firmware should never be the only thing that can switch a heater off. A 2021 Topten/eceee paper says EU coffee machines ship with a 30-minute auto-off default that users can't lengthen ([Topten](https://storage.topten.eu/source/files/D2_1_Criteria_Paper_Coffee_Machines.pdf)), though the underlying regulation's status is muddled. Do the same thing, Teasmade-style. Heaters may run only inside an armed window from T−20 to T+10 minutes. A limit switch at the bottom of the lever stroke cuts them directly. If the machine isn't armed, or there is no cup, it stays cold.

Ground coffee degrades. Grinding releases volatiles that are easily lost ([Akiyama et al., J. Agric. Food Chem. 2003](https://pages.uoregon.edu/chendon/coffee_literature/old_literature/2003%20J.%20Agric.%20Food%20Chem.,%20Volatiles%20released%20during%20grinding.pdf)). For packaged coffee, the SCA review cites nitrogen flushing that doubles sensory shelf life from 3 to 6 months, with the largest losses in the first days. Evidence on grinding the night before is anecdote in both directions. One Home-Barista tester preferred a batch ground 12 hours earlier ([Home-Barista](https://www.home-barista.com/brewing/experiments-with-preground-coffee-for-espresso-and-brew-pot-t6722.html)), while others report clear decline by 24 hours. Nothing controlled covers an 8-hour overnight wait.

Brewed espresso decays faster. Arii and Nishizawa's 2017 paper is titled "[Espresso coffee foam delays cooling of the liquid phase](https://pubmed.ncbi.nlm.nih.gov/28100101/)". A press write-up mentions a 15-minute best-drinking window (unverified). No sensory study follows a shot as it waits.

That is the case for the Americano. Under Newton cooling the time constant is *τ = mc/hA*. For cups of similar shape, area scales as *V*^(2/3), so *τ* scales as *V*^(1/3). A 200 ml Americano therefore cools about 5^(1/3) ≈ 1.7 times slower than a 40 ml shot, before counting the cup, and a minute's delay matters less in it. The sequence: hot water into the cup first, then the shot on top, timed to finish at the alarm rather than before it.

### If I were starting this weekend

1. Ask your brother for photos of the grinder's top nut, dial and burr, and for its weight on a kitchen scale. Borrow it if he'll let you.
2. Measure crank torque at an espresso setting with a luggage scale on the knob. Size the motor at twice the worst of three runs.
3. Order an ESP32, an HX711 and a 500 g load cell, flash openGBW, and get readings to 0.1 g on the bench.
4. Ask your father if you can log his machine's pressure curve with a portafilter gauge. A real trace from a good manual Italian machine beats anything in the research.
5. Choose a testbed. If you buy only one, make it the Robot: the lever is the new part, and the control loop on the Gaggia is already well documented.
6. Draw the push-only lever cradle and the sprag pulley adapter, and print both in PETG before you cut any metal.

# Beamer Hub v1 — Product Requirements

Status: ready-for-agent

Private tool for one Owner. One Vehicle: 2003 BMW 325i sedan, VIN `WBAET374X3NJ32467` (E46, US-spec, silver, M54 2.5 I6, RWD, Pretoria, built 03.2003, ETK serial `J32467`). Florida. Miles.

Use the glossary in `CONTEXT.md`. The actor is the **Owner**, never “user.”

The **Catalog** is VIN-filtered ETK for this Vehicle. The Owner will obtain that dump and deliver it. v1 ships with an empty Catalog and a paste-one-number path. The dump is not a blocker.

## Problem Statement

The Owner just bought this 2003 325i (third titled owner, ~6 weeks in). CARFAX and shop invoices describe twenty years of work, but that Evidence is not a Ledger the Owner can trust, extend, or nag from. The cluster Service Interval Display is the only on-car due-date; there is no My BMW app, no CarData, no iDrive CBS.

The Owner needs one private place that answers: what was actually done to this Vehicle, what is due, where a Symptom lives, and which BMW part numbers belong on this VIN — without inventing parts, scraping catalogs, or pretending an AI is a mechanic.

## Solution

A single-Owner web app on a VPS the Owner controls.

The Owner types a Query and lands on a Region (or a Catalog Part). From there they record Visits and Service Records, run a least-invasive Check Sequence when something is wrong, and see in-app Reminder banners when a System interval is approaching or due.

History from the CARFAX mechanical lines is seeded as unverified Visits and Records. The Owner confirms or deletes each one. Evidence stays Evidence until they say otherwise.

When the Owner delivers an ETK-for-this-VIN export, the app imports it as the Catalog. Until then the Catalog may be empty. A Query miss never becomes a new Part. A new Part requires a pasted BMW part number.

AI, when used at all, may Cite and Suggest. It does not prescribe a repair, name a failed part as fact, or invent a part number.

## User Stories

1. As the Owner, I want a private tool that only I use, so that the VIN and Ledger never live on a multi-tenant car app.
2. As the Owner, I want the app bound to VIN `WBAET374X3NJ32467` only, so that I never see parts or service language from some other BMW.
3. As the Owner, I want miles and calendar dates, so that Florida low-mileage time-based services are visible.
4. As the Owner, I want to open the Ledger and see Visits in date order, so that I can read the Vehicle’s life as a timeline.
5. As the Owner, I want each Visit to show its date, who did the work (a named shop or me), and the miles I typed that day when I have them, so that one shop day is not confused with another.
6. As the Owner, I want one Visit to contain many Service Records, so that oil, struts, and a valve cover on the same Gatto’s day stay separate jobs.
7. As the Owner, I want to create a Visit, so that I can start a day of work before I know every Record.
8. As the Owner, I want to add a Service Record to a Visit, so that I can write down what happened.
9. As the Owner, I want a Service Record to carry exactly one verb — observed, checked, ordered, or replaced — so that a look is not stored as a replacement.
10. As the Owner, I want each Service Record to have exactly one System, so that Reminders can match oil to oil and not to the rest of that Visit.
11. As the Owner, I want a Service Record to optionally name one or more Regions, so that “rear-end collision” can sit on rear bumper without becoming a Part.
12. As the Owner, I want to type the cluster Odometer Reading on a Record or Visit, so that miles come from the instrument cluster, not GPS or CARFAX.
13. As the Owner, I want to save a Record with no miles when I do not have them, so that the 2017 rear-end and the 2014 Tire Kingdom line can exist.
14. As the Owner, I want a standalone Service Record that is not inside a Visit, so that a roadside observation does not invent a shop day.
15. As the Owner, I want to edit a Service Record I created, so that I can fix a verb, System, Region, or miles.
16. As the Owner, I want to delete a Service Record I created, so that a mistake does not stay in the Ledger.
17. As the Owner, I want seeded CARFAX mechanical lines to appear as unverified Visits and Records, so that I start with history instead of a blank Ledger.
18. As the Owner, I want an unverified Record to look unverified, so that I never treat CARFAX wording as something I confirmed.
19. As the Owner, I want to confirm an unverified Record, so that it becomes an ordinary Ledger line.
20. As the Owner, I want to delete an unverified Record, so that a CARFAX line I do not trust never becomes history.
21. As the Owner, I want to confirm or delete a whole unverified Visit, so that I can accept or reject a shop day at once.
22. As the Owner, I want registration renewals and empty “vehicle serviced” CARFAX rows omitted from the seed, so that the Ledger is not 57 noise lines.
23. As the Owner, I want Evidence (the CARFAX PDF, a dealer print, a photo) stored as Evidence, so that a document is never silently turned into a Service Record.
24. As the Owner, I want to attach Evidence to a Visit or Record after I confirm it, so that the PDF supports the Ledger without replacing it.
25. As the Owner, I want to record what the Service Interval Display currently shows (OIL SERVICE or INSPECTION I / II, plus remaining miles and the date I read it), so that due dates come from the cluster.
26. As the Owner, I want that cluster reading to be able to drive a Reminder, so that I can nag from the car’s forecast when I typed it.
27. As the Owner, I want recommended Reminder intervals I can override: engine-oil 5,000 miles or 12 months; brake-fluid 24 months; coolant 48 months; cabin-filter 12 months — so that low-mileage Florida time is the default, not a 15k ritual.
28. As the Owner, I want a Reminder to fire from the last matching Service Record of the same System, so that a day that also did coils does not move the oil nag.
29. As the Owner, I want no automatic tire or Inspection Reminder unless I set one or I type remaining miles from the cluster, so that the app does not invent CBS it does not have.
30. As the Owner, I want Reminder state as an in-app banner only, so that a closed laptop is quiet and nothing emails or texts me.
31. As the Owner, I want a banner when a System interval is approaching and a clearer banner when it is due, so that I can tell soon from late.
32. As the Owner, I want to dismiss a Reminder banner until the next matching Record or until I change the interval, so that I am not stuck with a permanent nag I already saw.
33. As the Owner, I want to change a System’s miles and months interval, so that the defaults are recommendations, not law.
34. As the Owner, I want a Query bar as the way I pick a Region, so that I do not need a 3D car in v1.
35. As the Owner, I want typing an alias such as “back left window” or “driver’s window” to land on the matching Region(s), so that I can speak the way I already speak.
36. As the Owner, I want typing “interior trunk left lightbulb” to land on Trunk interior, so that a bulb name is an alias until a Catalog Part exists.
37. As the Owner, I want typing “oil” or “oil filter” to land on Engine bay and the engine-oil System, so that maintenance language reaches the right place.
38. As the Owner, I want typing “cluster” or “service light” to land on Instrument cluster, so that I can file the Service Interval Display.
39. As the Owner, I want a Query that matches a BMW part number in the Catalog to show that Part and a sensible Region when one is known, so that a number I copied from ETK is usable.
40. As the Owner, I want a Query miss to show the closest Regions and the closest Catalog Parts, so that a typo still gets me near the thing I meant.
41. As the Owner, I want a miss on an empty Catalog to show only closest Regions, so that the app does not invent Parts to fill the gap.
42. As the Owner, I want a miss to stay a miss, so that what I typed is never silently created as a Part.
43. As the Owner, I want to add an alias from a miss, mapping that phrase to an existing Region, so that next time I land there.
44. As the Owner, I want to add a Part from a miss only by pasting a BMW part number I copied from ETK, the dealer, or RealOEM I looked up by hand, so that names I invent cannot enter the Catalog.
45. As the Owner, I want to refuse adding a free-text “part” with no number, so that “left trunk LED” never becomes a Part.
46. As the Owner, I want to add a coarse Region only rarely, at the same grain as the accepted list, so that the Region set can grow without becoming a fake ETK.
47. As the Owner, I want the accepted Region list available from the first launch, so that Query has somewhere to land before any Catalog exists.
48. As the Owner, I want the Catalog to start empty, so that v1 does not wait on the ETK dump I am obtaining.
49. As the Owner, I want to import an ETK-for-this-VIN dump when I have it, so that the Catalog becomes the real parts list for `J32467`.
50. As the Owner, I want that import to require a BMW part number on every row, so that a nameless line cannot become a Part.
51. As the Owner, I want the import to store the description, optional group or diagram name, and optional supersession (number I have → current successor) when those columns exist, so that a 2003 invoice number can still resolve.
52. As the Owner, I want a second import of the same part number to update that Part rather than duplicate it, so that I can drop a corrected dump without cloning the Catalog.
53. As the Owner, I want import to create Parts only, never Regions, so that ETK’s thousands of lines do not become thousands of click targets.
54. As the Owner, I want to search the Catalog by number or description after import, so that I can find a clip or bulb without remembering the Region name.
55. As the Owner, I want a Catalog miss after import to still offer closest Parts plus closest Regions, so that I can add an alias or paste a number I looked up.
56. As the Owner, I want AI never to invent a part number, so that the Catalog stays ETK-true.
57. As the Owner, I want my recommended Crib listed on first launch, every item unconfirmed, so that I can mark what I actually have.
58. As the Owner, I want to mark a Tool or Capability as has, does-not-have, or unconfirmed, so that Check Steps can stop for the right reason.
59. As the Owner, I want Lift to start unconfirmed, so that the app never assumes I can raise the car.
60. As the Owner, I want a Check Sequence for the front-left window (front-left door Region; Symptom: glass does not go up and/or down), so that the first path is the one that defined Cite and Suggest.
61. As the Owner, I want that sequence in least-invasive order — both switches and key position, then fuse, then anti-pinch campaign ask, then listen with a helper, then door card, then shop — so that I do not jump to a regulator.
62. As the Owner, I want each Check Step to show required Tools and Capabilities, so that I know what the step asks of the Crib.
63. As the Owner, I want each Check Step to show whether it is dangerous, so that I see pinch and SRS risk before I start.
64. As the Owner, I want a Check Step to stop when the Crib marks a required Tool or Capability as does-not-have, so that I am not walked into work I cannot do.
65. As the Owner, I want an unconfirmed Crib item to let me continue after I see the gap, so that unconfirmed is not the same as does-not-have.
66. As the Owner, I want completing the window sequence to never name a failed regulator, so that a finished checklist is not a diagnosis.
67. As the Owner, I want the last window step to be a Suggestion to take it to an independent, so that shop-only tear-down stays shop-only.
68. As the Owner, I want a YouTube search button on a Check Step, so that I search when I ask, not when the step opens.
69. As the Owner, I want that button’s query to be `E46` plus the step name, so that the fuse step does not search “window regulator.”
70. As the Owner, I want YouTube hits to appear as Suggestions, so that a video is not treated as a Citation until I pin it.
71. As the Owner, I want to pin a Suggestion to turn it into a Citation on that step, so that I keep the one clip I actually trust.
72. As the Owner, I want to paste a RealOEM or etkbmw.cc diagram URL I already have open as a Citation, so that a page I looked up by hand can support a Suggestion.
73. As the Owner, I want any model-generated next step to arrive as a ranked Suggestion with Citations, so that I remain the person who decides.
74. As the Owner, I want the app never to issue a work order or tell me to buy a SKU, so that Cite and Suggest stay cite and suggest.
75. As the Owner, I want to add a Service Record from a Region after a check (observed or checked), so that the sequence can feed the Ledger without inventing a failed Part.
76. As the Owner, I want NHTSA `03V160000` (window anti-pinch) mentioned on the window sequence as an ask to the dealer, so that a known campaign is not forgotten — and I want it treated as unknown-until-the-dealer-packet, not as CARFAX “no open recalls.”
77. As the Owner, I want the 2017-09-06 rear-end seeded as an unverified observation on rear / right-rear Regions, so that later rear work has that Evidence in view.
78. As the Owner, I want last unverified oil (2025-06-18 at 133,026), brake fluid (2024-01-17), and coolant (2024-02-15) to drive Reminder math once I confirm those Records — or to stay inert while they remain unverified — so that CARFAX cannot nag me until I accept it.
79. As the Owner, I want the Vehicle treated as automatic (NHTSA trim SA / Steptronic) until a dealer ETK print says otherwise, so that a third-party “Gearbox: N” line does not change the car.
80. As the Owner, I want the engine treated as M54, not M56 SULEV, unless I record that the under-hood emissions label says SULEV, so that VANOS and CCV language stays honest.
81. As the Owner, I want the app to run on a VPS I control, so that a closed laptop cannot nag and the Ledger is not on someone else’s SaaS.
82. As the Owner, I want a single Owner credential, so that this is not an accounts product.
83. As the Owner, I want v1 to work with no Catalog dump, no 3D file, and no BMW login, so that I can start the Ledger the day I have a browser.

## Implementation Decisions

**Seam.** There is one test seam: Owner-facing Ledger behavior. Query, Visit/Record, Catalog paste/import, Crib, Check Sequences, and Reminder banners are all exercised through what the Owner can see and do. Do not add a second seam for storage, HTTP, or “the AI layer.”

**Shape.** One single-Owner web application on the Owner’s VPS. One configured Vehicle. Durable store on that VPS. No multi-tenant accounts, no OAuth, no BMW / ConnectedDrive / CarData login.

**Vehicle facts (fixed).** VIN `WBAET374X3NJ32467`. Chassis E46 sedan, US-spec, silver, M54 2.5, RWD, Pretoria, manufactured 03.2003. ETK serial `J32467`. Automatic until a dealer ETK print contradicts it. Miles. Florida.

**Glossary modules (interfaces, not files).**

- **Ledger** — Visits, Service Records, typed Odometer Readings, unverified confirm/delete, Evidence attachments. A Visit is one date + one who (shop name or Owner) + zero or more Records. A Record has one verb, one System, optional Regions, optional miles, optional Parts once a number exists. Evidence never writes a Record by itself.
- **Query** — Resolves text to Regions (via name and aliases), Systems (when the alias says so), and Catalog Parts (number and description). A miss returns closest Regions and closest Parts and offers gated add: alias → existing Region; Part → pasted BMW number; rare coarse Region. No free-text Part.
- **Catalog** — The set of Parts. Empty is valid. Grow-by-paste is valid. Bulk fill is an Owner-supplied ETK-for-this-VIN table. Import key is BMW part number (idempotent upsert). Optional fields: description, group/diagram name, superseded-from, current successor. Import creates Parts only. AI does not write Parts.
- **Crib** — Recommended Tools and Capabilities from the accepted list, each has / does-not-have / unconfirmed. Lift starts unconfirmed.
- **Check Sequence** — Ordered Check Steps for a Symptom/Region. v1 ships the front-left window sequence only. Each step carries tools, capabilities, danger, and a stop when the Crib is does-not-have. Completing the sequence does not create a failed-part finding. Shop-only is the last step.
- **Reminder** — In-app banner. Matches System on the last *confirmed* Record of that System (unverified Records do not move a Reminder). Defaults: engine-oil 5,000 miles **or** 12 months; brake-fluid 24 months; coolant 48 months; cabin-filter 12 months. Owner may override. Approaching = within 500 miles or 30 days of the next limit. Due = miles or months exceeded. No email, push, or SMS. No automatic tire or Inspection Reminder unless the Owner sets an interval or types cluster remaining miles.
- **Citation / Suggestion** — YouTube `search.list` runs only when the Owner presses the step button. Query string: `E46` plus that step’s name. Hits are Suggestions. Pin → Citation. A URL the Owner pastes (RealOEM, etkbmw.cc, dealer PDF) may be a Citation. Any later model help is Cite + Suggest only.

**Seed.** On first launch, create the unverified Visits and Records in the seed table below. Do not import the rest of the CARFAX. Last seeded oil / brake fluid / coolant dates are in that table; they stay out of Reminder math until confirmed.

**Accepted Regions (v1).**

Exterior: Front-left door, Front-right door, Rear-left door, Rear-right door, Hood, Trunk lid, Front-left lamp, Front-right lamp, Rear-left lamp, Rear-right lamp, Front windshield, Rear windshield, Front-left glass, Front-right glass, Rear-left glass, Rear-right glass, Front-left wheel, Front-right wheel, Rear-left wheel, Rear-right wheel, Front bumper, Rear bumper, Roof / sunroof, Grille.

Opened: Engine bay, Cabin, Trunk interior, Undercarriage.

Instruments: Instrument cluster.

**v1 aliases.**

| Owner types (examples) | Lands on |
| --- | --- |
| back left window, rear left window, rear-left glass | Rear-left glass, Rear-left door |
| front left window, driver’s window | Front-left glass, Front-left door |
| interior trunk left lightbulb, trunk lamp, cargo light | Trunk interior |
| oil, engine oil, oil filter | Engine bay (System engine-oil) |
| cluster, service light, iDrive (wrong car) | Instrument cluster |

**Systems (v1).** engine-oil, brake-fluid, coolant, cabin-filter, plus an open “other” for Records that are not those four (struts, coils, collision, inspection-as-checked, etc.). Only the four named Systems have default Reminders.

**Recommended Crib (all start unconfirmed).**

Tools: metric sockets 8–19 mm; Torx T20–T50; combination wrenches; torque wrench; floor jack (≥2 ton); jack stands (pair, rated); wheel chocks; drain pan + funnel; oil-filter housing cap wrench (M54, commonly 86 mm / 36 mm hex); trim clip tools; screwdrivers + pick set; multimeter; OBD-II reader; work light + safety glasses; battery maintainer.

Capabilities: Lift; Helper; Level hard stand; Can raise the car on stands.

**Front-left window Check Sequence.**

Symptom: Front-left window does not go up and/or down. Region: Front-left door. YouTube button query = step title + `E46`.

| # | Check Step | Tools / Capabilities | Danger | Stop if Crib is does-not-have |
| --- | --- | --- | --- | --- |
| 1 | Confirm both door switch and driver’s master; try key accessory vs run | None | None | — |
| 2 | Check window fuse (glovebox / fuse chart in owner’s manual) | Flashlight, fuse puller or fingers | None | — |
| 3 | Recall / anti-pinch: NHTSA `03V160000` — ask dealer campaign status (VIN packet) | None | None | — |
| 4 | Listen at the door: motor hum vs silence vs grind while an assistant holds the switch | Helper | Pinch hazard — keep hands out of the glass | Helper |
| 5 | Door card off: inspect connector at switch and door module, look for broken wires in the boot | Trim tools, screwdriver, work light | Airbag in the door — do not probe yellow SRS connectors | Trim tools |
| 6 | Shop: regulator, module, or wiring | — | Lift / SRS / further tear-down | Mark this step shop-only |

No step names a failed regulator.

**Catalog import contract.** v1 accepts a table the Owner prepares from their ETK dump: one row per Part; required column = BMW part number; optional = description, group/diagram, superseded-from, current successor. CSV or JSON is enough. If the dealer hands over a PDF, the Owner (not the app) turns it into that table. The app does not fetch, crawl, or scrape RealOEM, etkbmw.cc, BMW NA, AIR, or ETK.

**YouTube budget.** Default daily cap in the YouTube Data API for `search.list` is small (~100). Button-only keeps v1 inside that. Do not prefetch.

**3D.** Deferred. No Viewer in v1. Later orbit-3D (if MediaPool, dealer, or a purchased GLB appears) is a picker on top of the same Regions, not a new catalog.

## Testing Decisions

A good test is something the Owner can observe: a Query lands or misses; a Visit shows its Records; unverified stays unverified until confirm/delete; a Reminder moves only after a confirmed Record of that System; a does-not-have Crib item stops a step; a YouTube call does not happen until the button; a pasted number becomes a Part and a typed name does not; an import upserts on part number and does not create Regions.

Test through the one Owner-facing Ledger seam. Do not test table shapes, storage keys, or prompt text.

There is no prior art in this repo. The first tests *are* the prior art: Owner-visible examples from the seed (Gatto’s 2023-12-11 is one Visit and several Records; oil Reminder ignores coils on that day; “interior trunk left lightbulb” → Trunk interior; empty Catalog miss → Regions only).

Do not write an exploit, scraper, or “authorized” catalog harvest as a test.

## Out of Scope

- 3D Viewer, orbit picker, opening doors/hood/trunk, AI mesh/CAD, photogrammetry
- Shopping, price compare, retailer scrape, order tracking
- AI as mechanic: work orders, “replace the regulator,” invented part numbers
- Scraping or bulk harvest of RealOEM, etkbmw.cc, BMW NA, AIR, ISTA, ETK, MediaPool, or the configurator
- My BMW, CarData, ConnectedDrive, iDrive CBS live data
- A second Vehicle, multi-Owner accounts, household sharing
- Email, SMS, push, or any nag off the VPS
- Official AOS / AIR / ISTA dump as an app feature
- Treating CARFAX “no open recalls” as NHTSA/dealer campaign truth
- Changing gearbox off automatic without a dealer ETK print
- Treating the engine as M56 SULEV without the emissions label
- Waiting on the Owner’s ETK dump to ship v1

## Further Notes

ADRs that bind this spec: 0001 private Owner; 0002 one VIN; 0003 Ledger-first v1 (extended by later ADRs); 0004 Cite + Suggest; 0005 VPS; 0006 superseded by 0018; 0007 Visit contains Records; 0008 least-invasive sequences; 0009 CARFAX unverified; 0010 Reminder Systems; 0011–0014 YouTube button; 0012 / 0015 Crib; 0016–0017 window sequence and Regions; 0018 Query not 3D; 0019 miss + gated add; 0020 Owner-supplied ETK Catalog.

Research that the lists above were accepted from: regions, recommended crib, front-left window sequence, unverified ledger, VIN facts, CARFAX notes, VIN-true catalog, BMW/dealer ask scripts. Those asks are Owner homework, not product features.

CARFAX PDF run 2026-06-05 is Evidence. Lifelong Florida, ~6k mi/year, last cluster miles 135,576 on 2026-03-17 at Melbourne BMW. Owner is the third titled owner.

### Unverified Ledger seed

Imported unverified. Owner confirms or deletes. Accident has no shop and no miles. 2014-10-28 has no miles. Verbs: observed / checked / ordered / replaced.

| Visit date | Miles | Who | Records (verb — what) |
| --- | --- | --- | --- |
| 2004-05-18 | 3,713 | The Imported Car Store, Melbourne | checked — body electrical |
| 2009-05-20 | 33,094 | Coggin BMW Treasure Coast, Fort Pierce | checked — inspection; checked — A/C; replaced — coolant; replaced — brake fluid |
| 2010-11-13 | 41,411 | Melbourne BMW | replaced — engine oil and filter |
| 2012-01-24 | 45,916 | Melbourne BMW | replaced — engine oil and filter; checked — engine; checked — brakes; checked — steering; replaced — wipers |
| 2013-01-22 | 57,395 | Melbourne BMW | replaced — engine oil and filter; replaced — brake fluid; checked — body electrical |
| 2014-09-03 | 73,204 | Melbourne BMW | replaced — engine oil and filter; replaced — cabin filter |
| 2014-10-28 | — | Tire Kingdom, Melbourne | replaced — tire repair |
| 2016-01-28 | 85,459 | Melbourne BMW | replaced — oil-filter-adapter gasket; checked — body electrical |
| 2017-02-13 | 92,866 | Melbourne BMW | checked — cooling system |
| 2017-09-06 | — | Damage report (no shop) | observed — rear-end collision, rear and right rear, airbags did not deploy |
| 2019-12-19 | 107,535 | Ron’s European, Merritt Island | replaced — engine oil and filter |
| 2020-12-11 | 111,720 | Melbourne BMW | replaced — engine oil and filter; replaced — cabin filter; checked — cooling; checked — alignment; replaced — lower control-arm bushings |
| 2022-03-21 | 119,408 | 2000 Auto, Melbourne | replaced — engine oil and filter; replaced — A/C refrigerant; replaced — brake-pad sensors; checked — maintenance-reminder reset |
| 2023-03-15 | 123,490 | 2000 Auto, Melbourne | replaced — engine oil and filter; replaced — oil-pan drain plug |
| 2023-09-14 | 125,328 | Gatto’s, Melbourne | checked — engine oil/fluid leak |
| 2023-12-11 | 125,928 | Gatto’s, Melbourne | replaced — engine oil and filter; checked — cooling; replaced — front struts; replaced — valve cover gasket |
| 2024-01-17 | 126,126 | Gatto’s, Melbourne | replaced — brake fluid; replaced — ignition coils; replaced — spark plugs; checked — tune-up |
| 2024-02-15 | 126,438 | Gatto’s, Melbourne | replaced — coolant; replaced — power steering pump |
| 2024-09-19 | 128,399 | Gatto’s, Melbourne | replaced — engine oil and filter; checked — A/C |
| 2025-06-18 | 133,026 | Gatto’s, Melbourne | replaced — engine oil and filter; checked — oil leak; replaced — ignition coils |
| 2026-03-17 | 135,576 | Melbourne BMW | checked — inspection; checked — instrument cluster |

Last unverified oil **replaced**: 2025-06-18 at 133,026. Last unverified brake fluid: 2024-01-17. Last unverified coolant: 2024-02-15.

NHTSA model-year campaigns (not VIN-closed): include Takata, tail lamps, auto idle `03V124000`, window anti-pinch `03V160000`. Dealer campaign screen / BMW NA is the source of open/closed. CARFAX is not.

# BMW service-tracker: external constraints

Facts gathered so a personal BMW repair-tracking web app is designed against primary sources, not wishful APIs. This is not a spec and not a glossary.

## Official apps already cover live vehicle status and dealer service

The My BMW app already shows range, current mileage, window and door status, vehicle location, remote lock/start, maintenance alerts, and dealer service scheduling. Feature availability differs by model.

Source: [My BMW App](https://www.bmwusa.com/my-bmw-app.html), BMW of North America.

BMW NA's My BMW privacy description also lists vehicle maintenance data (next service, oil level, brake wear) and vehicle status data (mileage, battery voltage, fuel levels, door and window status) as data the official service already processes.

Source: My BMW App Data Protection Policy, BMW of North America (linked from bmwusa.com).

Implication: a third-party app that "tracks mileage and tells you when an oil change is due" is competing with software the car and the official app already ship. The gap worth filling is the work My BMW does not own: independent-shop / DIY history, aftermarket parts decisions, and an owner-controlled audit trail.

## Service due dates are Condition Based Service, not a fixed 5,000-mile list

BMW vehicles use an in-vehicle BMW Maintenance System / Condition Based Service (CBS). It forecasts inspections and maintenance from operating conditions, not a single universal interval. Service-task status is stored in the remote control key so a BMW center key reader can print a customized checklist.

The official 2023 all-models maintenance booklet shows iDrive service-history examples such as engine oil, vehicle check, and brake fluid, each with its own date and remaining-miles forecast, plus symbols for "no service required", "deadline approaching", and "deadline passed".

Source: [BMW MY 2023 All Models Maintenance](https://www.bmwusa.com/content/dam/bmw/common/warranty-books/2023/BMW-MY-2023-All-Models-Maintenance-(On-line).pdf), BMW of North America.

A BMW technical bulletin on CBS states that oil-change timing uses an oil-condition sensor (condition, level, temperature) plus algorithms on engine load, fuel consumption, idle time, and distance since last oil change. Brake-pad replacement uses lining wear sensors and, on some vehicles, residual-wear algorithms (distance, wheel speed, braking pressure, time, frequency). Cabin microfilter and remote-control-transmitter battery are typically every second oil service unless otherwise noted.

Source: BMW SI B00 07 02, "Condition Based Service (CBS) – In-Vehicle Maintenance Reminder System" (circulated via ALLDATA / trade reprint of the BMW TSB).

Implication: "notify me X miles or N days before oil / tires / etc." cannot be a generic schedule hardcoded in the app unless the owner overrides CBS. Accurate due dates come from CBS (iDrive, My BMW, or CarData), or from owner-entered intervals that will drift from the car.

## BMW telematics APIs exist, but not as a casual hobbyist SDK

### CarData for customers (US)

BMW of North America launched CarData in the US on 29 June 2020. A customer needs a telematics-enabled BMW with a built-in SIM, registered in ConnectedDrive. Customers can request a CarData report with:

- condition data (example given: mileage)
- usage-based data (example given: average fuel consumption)
- event data (example given: an automated service call)

The 2020 announcement said third-party services (example: mileage-based insurance) would come "in the near future", with sharing only through BMW CarData and customer consent. No direct third-party access to the vehicle.

Source: [BMW CarData: Secure and private control of vehicle data for customers](https://www.press.bmwgroup.com/usa/article/detail/T0310166EN_US/bmw-cardata:-secure-and-private-control-of-vehicle-data-for-customers?language=en_US), BMW Group PressClub USA, 29 June 2020.

BMW NA terms treat CarData as a ConnectedDrive service. Only the Primary Subscriber may release (or cancel release of) data to third parties, and only while a Subscriber Agreement is in force.

Source: BMW CarData Terms and Conditions (US), BMW of North America.

### CarData for third-party service providers

BMW Group's CarData regulation page states that service providers such as workshops or insurers can register; they receive only the telematics the customer explicitly consents to, via BMW's backend. It also states CarData is available to service providers based in the European Economic Area (EEA), registration is free for EEA companies, and data is available in listed European ConnectedDrive markets (including the UK and Switzerland). Access is via the Aftersales Online Services (AOS) portal, CarData API, and streaming.

Source: [CarData](https://www.bmwgroup.com/en/general/regulations/cardata.html), BMW Group.

The BMW Open Data Platform / CarData third-party portal describes paid, usage-based telematics access: the customer must give explicit permission and have a telematics-enabled vehicle on a valid customer account. Setup requires organization contact data, terms acceptance, client credentials, subscriptions, and per-customer consent. Brands listed: BMW, MINI, Rolls-Royce, Toyota Supra.

Source: [BMW CarData third-party portal](https://bmw-cardata.bmwgroup.com/thirdparty/public/), BMW Group.

Implication: live mileage / CBS / tire diagnosis from BMW into a personal US web app is not a weekend OAuth integration. The documented partner path is an organization registering on AOS / Open Data Platform, with EEA-oriented provider access. A US owner can view CarData reports; building a third-party consumer app on the live stream is a partner-program problem, not a library-install problem.

## Official parts, wiring, and repair data are workshop products, not a public catalog API

BMW Aftersales APIs (same data as AIR and ETK) are provided to qualified third parties for a fee. Contact for onboarding: aos-api@bmwgroup.com. Independent workshops without programming capacity are told to use the AIR and ETK applications instead.

Published API areas:

| Product | What BMW says it provides |
| --- | --- |
| Vehicle Identification | Basic and option data for a VIN; type-finder from product features |
| Repair & Maintenance | Repair procedures, wiring diagrams, connector views, pin charts, component locations, functional descriptions |
| Parts Information | "API Coming soon! Until then we are offering Parts Information as data files." |
| Technical Campaign & Map Status | Open campaigns; installed navigation map |
| Flat Rates | Labor flat-rate positions and included steps |
| BMW CarData | Telematics for BMW, MINI, Rolls-Royce, Toyota |
| Smart Maintenance | Workshop-facing service-demand data |

Source: [BMW APIs – Aftersales Online System](https://aos.bmwgroup.com/bmw-api), BMW Group.

AOS terms restrict licensed content to professional maintenance and repair of BMW-group vehicles within the user's organization, and forbid disseminating it to third parties without written consent.

Source: [AOS Conditions of Use](https://aos-i.bmwgroup.com/conditions-of-use), BMW AG.

Implication: "click the front-left window and diagnose why it isn't working" is BMW Repair & Maintenance / ISTA-AIR territory (wiring, pinouts, component location). That data is sold to workshops, not scraped into a consumer app. "Least expensive OEM and aftermarket part" cannot be served from an official public parts API today; the Parts Information API is not shipped.

## RealOEM and dealer sites are not a legal parts backend

RealOEM is a widely used unofficial ETK-style catalog. VIN lookup uses the last seven digits of the VIN (BMW serial number) or model/series browse. There is no documented public RealOEM API.

Source: [RealOEM.com BMW model select](https://www.realoem.com/bmw/select.do).

BMW of North America site terms forbid using any "deep-link, page-scrape, robot, crawl, index, spider... or other automatic device" to access, copy, or monitor any portion of BMW NA sites, and restrict use of site content to personal (non-commercial) purposes.

Source: [BMW Terms](https://www.bmwusa.com/content/dam/bmw/common/footer/pdf/BMW_Terms.pdf.asset.1698769627198.pdf), BMW of North America.

Implication: a "live cheapest OEM + aftermarket" feature that scrapes RealOEM, shopbmwusa, FCP Euro, ECS, or RockAuto is both legally fragile and operationally brittle. Legitimate options later: owner-entered part numbers; paid BMW Parts Information data files if they qualify; retailer affiliate APIs (eBay Browse has vehicle-compatibility checks; Amazon's Product Advertising API 5.0 is deprecated in favor of the Creators API for associates). None of those replace ETK fitment.

## 3D specificity has a hard ceiling

BMW Group's legal disclaimer states that text, images, graphics, and animations on BMW Group sites are copyrighted, may not be copied for commercial use or distribution, and that visiting the site grants no license to BMW intellectual property. Trademarks include marks, model names, logos, and emblems.

Source: [BMW Group legal disclaimer](https://www.bmwgroup.com/en/general/legal-disclaimer.html).

There is no official BMW program that hands a third party a production-accurate, part-clickable 3D car for a consumer web app. Configurator / marketing models are not a licensed parts catalog.

ETK diagrams explode a BMW into thousands of part numbers (assemblies, fasteners, bulbs, modules, harnesses). A photoreal exterior glTF can support click targets for body-visible assemblies (headlight, door, wheel, windscreen). It cannot honestly represent "inside left trunk lamp" or "window regulator" without:

- a separate interior / cargo scene
- a parts graph that is not the mesh (ETK-style hierarchy)
- hitboxes or schematic callouts mapped to part records

"As specific as possible" in 3D is a catalog problem first and a rendering problem second.

## Live parts-order tracking is a tracking-number problem, not a retailer feed

UPS, FedEx, USPS, and DHL expose tracking APIs to registered developers. AfterShip and similar aggregators unify carriers behind one API (AfterShip documents HTTPS `api.aftership.com` tracking create/get plus webhooks).

No major DIY BMW retailer publishes a "pull all my orders and live tracking" consumer API. Amazon / RockAuto / FCP Euro / ECS order status stays on their sites. The integrable version is: owner pastes a tracking number (or forwarding email), the app polls a carrier or aggregator.

"Pages that pull a live tracking feed" of parts you ordered is doable per tracking number. It is not doable as an automatic feed from every parts shop.

## What this idea is actually mixing

The pitch is four different products:

1. **Owner ledger** — click a part, record last checked / ordered / replaced, keep a timestamped service history.
2. **CBS reminder** — oil, tires, brakes, etc., notified at X miles or N days.
3. **Parts shopping** — cheapest OEM vs aftermarket for that part.
4. **Workshop diagnostics** — "why isn't the window / trunk lamp working", plus live shipment tracking as a fifth surface.

(1) and a manual/CBS-assisted (2) can be a personal web app. (3) without scraping is search-by-part-number plus links. (4) is BMW AIR/ISTA. (5) is paste-a-tracking-number.

## Sources

- [My BMW App](https://www.bmwusa.com/my-bmw-app.html) — BMW of North America
- [BMW MY 2023 All Models Maintenance](https://www.bmwusa.com/content/dam/bmw/common/warranty-books/2023/BMW-MY-2023-All-Models-Maintenance-(On-line).pdf) — BMW of North America
- BMW SI B00 07 02, Condition Based Service (CBS)
- [BMW CarData US launch](https://www.press.bmwgroup.com/usa/article/detail/T0310166EN_US/bmw-cardata:-secure-and-private-control-of-vehicle-data-for-customers?language=en_US) — BMW Group PressClub USA, 29 June 2020
- [CarData regulation page](https://www.bmwgroup.com/en/general/regulations/cardata.html) — BMW Group
- [CarData third-party portal](https://bmw-cardata.bmwgroup.com/thirdparty/public/) — BMW Group
- [AOS BMW APIs](https://aos.bmwgroup.com/bmw-api) — BMW Group
- [AOS Conditions of Use](https://aos-i.bmwgroup.com/conditions-of-use) — BMW AG
- [BMW NA Terms](https://www.bmwusa.com/content/dam/bmw/common/footer/pdf/BMW_Terms.pdf.asset.1698769627198.pdf) — BMW of North America
- [BMW Group legal disclaimer](https://www.bmwgroup.com/en/general/legal-disclaimer.html) — BMW AG
- [RealOEM model select](https://www.realoem.com/bmw/select.do)
- [AfterShip Tracking API quick start](https://www.aftership.com/docs/tracking/quickstart/api-quick-start)
- [Amazon PA-API 5 deprecation / Creators API](https://webservices.amazon.com/paapi5/documentation/)

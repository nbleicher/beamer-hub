# How to have every real Part — and no fake ones

“Every single part” on this Vehicle is **ETK filtered by VIN**, not more Regions. ETK identifies the car by the last seven of the VIN (`J32467`) or the full 17. That hides parts that do not belong on this chassis, engine, gearbox, and options ([ETK user manual](https://www.scribd.com/document/493753908/User-manual-ETK-20180803); same VIN-filter behavior described for dealer ETK). A replacement “cannot be built in all vehicles.”

That list is **thousands of lines**: lamps, bulbs, clips, grommets, harnesses, gaskets. It is a **Catalog**, not 3,000 clickable Regions. A Query searches names and numbers in the Catalog and still lands you on a Region for the Ledger / Check Sequence.

Parts also **supersede**. The number on a 2003 invoice may now be a successor. ETK’s supersession tree is the current number. The Catalog should store the number you have and the current successor when known.

## What actually fills the Catalog

| Source | Complete for this VIN? | Fake parts? |
| --- | --- | --- |
| Owner invents “left trunk LED” | No | Yes |
| AI names a part | No | Yes |
| Owner pastes a number they copied from RealOEM/dealer for this VIN | One line at a time | Low if they used `J32467` |
| Dealer prints/exports ETK for `WBAET374X3NJ32467` | Yes, if they give you the list | No |
| Scrape RealOEM / BMW NA | Complete-ish | Against BMW NA terms; we will not |

There is no public BMW “give me all parts for this VIN” API. AOS Parts Information is still “coming soon” / data files for **qualified** shops.

**You cannot guarantee zero wrong parts** unless the Catalog is ETK-for-this-VIN. Grow-as-you-go with pasted numbers is honest and incomplete. An LLM “complete catalog” is complete fiction.

## Q26 in that light

- **A** — miss → closest Regions **and** closest Catalog Parts.
- **B** — add **alias** (e.g. “boot lamp” → trunk interior) or add **Part** with a real number. Not add “interior trunk left lightbulb” as a new Part with no number.

# What to ask the dealer friend

A BMW store runs **AIR** (Aftersales Information Research) and **ETK** (electronic parts catalog) on ISPI / DCS. Those are VIN-filtered **2D exploded diagrams** and repair text, the same data BMW sells on AOS. BMW NA described AIR as TIS + ETK + flat rates in one workshop app ([SI B07 04 14](https://static.nhtsa.gov/odi/tsbs/2014/MC-10148160-9999.pdf)). AOS terms do not let a dealer dump that catalog to a third-party app.

They almost certainly **do not** have a browser `.glb` of a 2003 E46 with opening doors. The sales configurator 3D is for **current** inventory, not this chassis. Ask anyway so we get a clean no. The useful ask is the VIN packet below.

## The 3D question (one sentence)

> Do you have a **downloadable 3D model** of an **E46 3 Series sedan** (file types: **GLB, glTF, or FBX**) with **separate doors, hood, and trunk**, that I can load in a private browser tool — not screenshots, not ETK, not today’s 3 Series configurator?

If they say yes: get the file, the format, and whether BMW or a vendor licensed it. If they say no or “I can print ETK pages”: that is the expected answer. We buy a marketplace sedan `.glb` and use ETK as **Evidence** (part numbers, diagrams), not as the Viewer.

## The VIN packet (this is what the store can actually do)

Hand them `WBAET374X3NJ32467`. Ask for printouts or PDFs, not a USB of AIR.

1. **Build / options** for this VIN (paint, interior, SA/automatic, any SA codes).
2. **Open campaigns / recalls** on this VIN (Takata, tail lamps, window anti-pinch `03V160000`, auto idle `03V124000`). CARFAX said “none open”; the dealer key/campaign screen is the real list.
3. **ETK exploded page + part numbers** for: front-left window regulator and door module; oil-filter housing; valve cover gasket; expansion tank. Last seven of VIN for ETK: `J32467`.
4. **Any service they have in BMW systems** after 2026-03-17 (cluster check at Melbourne BMW) that CARFAX missed.

Do not ask them to copy AIR/ISTA onto a drive. That is the dump we will not take.

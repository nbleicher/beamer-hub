# Vehicle `WBAET374X3NJ32467`

Facts for the one Vehicle in scope. Not a glossary.

## Identity (NHTSA vPIC)

Decoded clean; check digit valid.

| Field | Value |
| --- | --- |
| Make / model / year | BMW 325i, 2003 |
| Body | Sedan/Saloon, 4 doors |
| Engine | 6-cylinder gasoline, 184 hp |
| Trim | SA (BMW’s US code for Steptronic automatic on this generation) |
| Model code (in NHTSA note) | 0345 |
| Plant | Pretoria, South Africa |
| Wheelbase | 107.3 in |
| Shipping weight (auto) / GVWR (auto) | 3307 lb / 4365 lb |

Source: [NHTSA vPIC DecodeVinValues](https://vpic.nhtsa.dot.gov/api/vehicles/DecodeVinValues/WBAET374X3NJ32467?format=json).

US-spec 325i 184 hp is the M54B25 rating. A SULEV M56 existed on some 2003 325i automatics in some states.

Unofficial ETK mirror [etkbmw.cc for this VIN](https://etkbmw.cc/en/bmw/auto/WBAET374X3NJ32467) (page states it is **not affiliated with BMW AG**) decodes the same VIN as: **325i M54**, **3' E46 Saloon USA**, manufacture **03.2003**, steering **L**. It also shows **Gearbox: N**. NHTSA trim is **SA** (Steptronic automatic) and CARFAX listed automatic; treat gearbox as automatic until a dealer ETK print contradicts it. The M54 line plus 184 hp is enough to treat VANOS/CCV/intake as M54, not M56, unless the under-hood emissions label says SULEV.

Chassis in BMW parts language: **E46** sedan. RealOEM / ETK serial (last 7 of VIN): `J32467`. Production month matters for ETK “from / up to” rows.

etkbmw.cc is the same class of site as RealOEM: unofficial ETK in a browser, no public API, not a Catalog we scrape. Use it by hand; store a diagram URL as a Citation.

## What this Vehicle does not have

- My BMW app telemetry, remote 3D view, or dealer push alerts
- BMW CarData / ConnectedDrive SIM telematics
- iDrive Condition Based Service menus (oil-condition sensor, brake-pad remaining-life, etc.)

Due dates live on the **Service Interval Display** in the cluster: OIL SERVICE or INSPECTION, plus remaining miles. The 2003 E46 owner’s manual (same Maintenance System text across late E46 US books) states the system includes Engine Oil Service and Inspections I and II, computed from operating conditions, and that drivers under ~6,200 miles/year should still change oil at least every two years. Procedure lists live in the Service and Warranty Information Booklet, not in the cluster.

Sources: 2003/2004 E46 US owner’s manual, “The BMW Maintenance System” / “Service interval display”; Haynes E46 maintenance overview of Oil Service vs Inspection I/II.

## Recalls that apply to 2003 325i as a model (not VIN-confirmed open/closed)

NHTSA lists eight campaigns for 2003 BMW 325i, including Takata passenger/driver inflators (`20V018000`, `15V318000`, and earlier airbag campaigns), tail lamps (`11V438000`), automatic-transmission idle/speed-control (`03V124000`), window anti-pinch (`03V160000`), and an aftermarket Cardone master-cylinder campaign (`07E023000`) that only matters if that part was installed.

Source: [NHTSA recallsByVehicle](https://api.nhtsa.gov/recalls/recallsByVehicle?make=bmw&model=325i&modelYear=2003) (make/model/year, not this VIN’s completion state).

Window anti-pinch is on that list. “Click the front-left window and diagnose it” is a known factory defect class, not a blank-slate AI puzzle.

## Public listing noise

Third-party history sites have shown this VIN in South Florida classifieds (Boca Raton). Treat mileage figures on those pages as unreliable. Ask the Owner for the cluster odometer and any booklet stamps.

# Beamer Hub

A private record of one Owner’s 2003 BMW 325i: what was done to it, what is due, and what was bought for it.

## Language

**Owner**:
The single person this tool exists for.
_Avoid_: User, customer, account, household

**Vehicle**:
The 2003 BMW 325i sedan identified by VIN `WBAET374X3NJ32467` (E46 chassis, US-spec, silver, 2.5L I6, rear-wheel drive, built in Pretoria).
_Avoid_: Beamer (as a type), car, BMW (as if more than one vehicle were in scope)

**Service Interval Display**:
The Vehicle’s instrument-cluster forecast of the next Engine Oil Service or Inspection, based on how the Vehicle has been driven.
_Avoid_: CBS, Condition Based Service, iDrive service menu, My BMW alert

**Engine Oil Service**:
The BMW Maintenance System oil-and-filter service the Service Interval Display names OIL SERVICE.
_Avoid_: Oil change (as a generic mileage ritual)

**Inspection I**:
The lighter of the two alternating BMW inspection packages in the Service and Warranty Information Booklet.
_Avoid_: 30k service (as if mileage alone defined it)

**Inspection II**:
The heavier inspection package; it includes Inspection I plus further replacements the booklet lists (air cleaner and related items).
_Avoid_: 60k service (as if mileage alone defined it)

## Ledger

**Ledger**:
The Owner’s chronological record of Service Records for the Vehicle.
_Avoid_: Service history (as a page title for Carfax), log, journal

**Visit**:
One session of work on one date, at one shop or by the Owner, that can contain many Service Records.
_Avoid_: Appointment, invoice, RO

**Service Record**:
One job inside a Visit (or a standalone observation), stamped with an Odometer Reading when known. Verbs: observed, checked, ordered, replaced. Has one System and optional Region(s). A Record imported from Evidence starts unverified until the Owner confirms or deletes it.
_Avoid_: CARFAX line, work order, invoice (those may be Evidence)

**System**:
The kind of maintenance a Service Record and a Reminder share (engine-oil, brake-fluid, coolant, cabin-filter).
_Avoid_: Category, type, part

**Odometer Reading**:
Miles the Owner types from the cluster at the time of a Service Record or Reminder.
_Avoid_: GPS mileage, OBD mileage, Carfax odometer

**Evidence**:
A third-party document about the Vehicle that is not itself a Service Record.
_Avoid_: History (as if Evidence were the Ledger)

## Checks

**Symptom**:
What the Owner notices (window dead, lamp out, leak, noise). Not a failed part.
_Avoid_: Issue, problem, diagnosis

**Region**:
A named place on the Vehicle the Owner can select on the 3D model (front-left door, trunk, engine bay). Not an ETK part number.
_Avoid_: Part, mesh, component

**Check Sequence**:
An ordered list of least-invasive Owner-doable checks for a Symptom or Region. Completing the sequence is not a finding that a part has failed.
_Avoid_: Diagnosis, procedure, repair, TIS job, ISTA test plan

**Check Step**:
One step in a Check Sequence: what to try, required Tools and Capabilities, whether it is dangerous, and a stop if the Crib says the Owner does not have what the step needs. May carry Citations. A YouTube search for the step returns Suggestions, not Citations.
_Avoid_: Job, task, TIS step

**Citation**:
A pointer to a source a Suggestion rests on.
_Avoid_: Proof, documentation

**Suggestion**:
A ranked next check or hypothesis, offered with Citations. It is not a work order and not a parts purchase.
_Avoid_: Recommendation (as a command), diagnosis, fix

**Reminder**:
An in-app banner that an Owner-set or recommended miles/months interval after the last matching Service Record (same System) is due or approaching.
_Avoid_: Email alert, push notification, SMS

## Crib

**Tool**:
A physical item a Check Step may require (socket, jack, multimeter).
_Avoid_: Part, SKU

**Capability**:
A condition that is not a hand tool (lift, helper, level driveway).
_Avoid_: Tool, skill

**Crib**:
The Owner’s list of recommended Tools and Capabilities, each marked has, does-not-have, or unconfirmed.
_Avoid_: Inventory, garage, user tool list

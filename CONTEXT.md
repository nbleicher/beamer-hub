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

**Service Record**:
A dated entry the Owner accepts as true about the Vehicle, stamped with an Odometer Reading.
_Avoid_: CARFAX line, work order, invoice (those may be Evidence)

**Odometer Reading**:
Miles the Owner types from the cluster at the time of a Service Record or Reminder.
_Avoid_: GPS mileage, OBD mileage, Carfax odometer

**Evidence**:
A third-party document about the Vehicle that is not itself a Service Record.
_Avoid_: History (as if Evidence were the Ledger)

## Checks

**Symptom**:
What the Owner notices (window dead, lamp out, leak, noise). Not a failed part.
_Avoid_: Problem, issue, diagnosis

**Check Sequence**:
An ordered list of Owner-doable checks for a Symptom or region. Each step may carry Citations and Suggestions. Completing the sequence is not a finding that a part has failed.
_Avoid_: Diagnosis, procedure, repair, TIS job, ISTA test plan

**Citation**:
A pointer to a source a Suggestion rests on.
_Avoid_: Proof, documentation

**Suggestion**:
A ranked next check or hypothesis, offered with Citations. It is not a work order and not a parts purchase.
_Avoid_: Recommendation (as a command), diagnosis, fix

**Reminder**:
A notice that an Engine Oil Service, Inspection, or Owner-set interval is within X miles or N days.
_Avoid_: Alert, notification (as the domain object)

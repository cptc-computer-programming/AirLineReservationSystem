# Scenario 4: Multi-Leg Journeys & Connecting Flights

## Problem Statement
Currently, customers can only book **single flights**. The system cannot handle **round-trip** or **multi-city itineraries** with connecting flights. A customer booking New York → London → Paris must place three separate bookings with no relationship between them.

## Core Requirements
- Customers must be able to **book multiple flight segments as one itinerary**.
- The system must **validate connections**: arrival city of one leg = departure city of next leg, and layover time is reasonable.
- **All legs must book together or fail together** (all-or-nothing semantics).
- If a leg is **cancelled**, the entire itinerary is impacted; offer rebooking or refund.
- **Seat assignments and pricing** apply per leg; total price is the sum of segments + taxes/fees.
- Customers see the **entire itinerary status** and can manage it as one unit.

## Design Challenges
1. **What new entity/entities represent a multi-leg booking?**
2. **How do you model individual flight legs within an itinerary?**
3. **What does "atomic booking" mean in OO design?** (hint: consider state management)
4. **Where does itinerary coordination logic live?** (FlightReservation, a new orchestrator, elsewhere?)
5. **How do you maintain consistency across multiple Flights?** (cascading updates, rollback on failure)

## Edge Cases to Consider
- What if a connection time is too short or too long?
- What if only some legs are available (partial availability)?
- Can a customer change one leg without affecting others?
- What if a middle leg gets cancelled? (must rebook remaining legs atomically)
- What about overnight or multi-day itineraries?
- Can seats be pre-assigned to baggage routing across legs?

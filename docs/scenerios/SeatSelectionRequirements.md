# Scenario 2: Seat Selection & Seat-Based Pricing

## Problem Statement
Currently, the system tracks only the **total number of available seats** per flight. Customers cannot select specific seats, and all seats cost the same. The airline wants to offer **seat choice** and **dynamic pricing** based on seat type and location.

## Core Requirements
- Customers must be able to **select and assign specific seats** when booking.
- **Different seat types** have different prices (e.g., window, aisle, emergency row).
- The system must **prevent double-booking** and maintain seat availability accurately.
- When a customer cancels, their seat(s) must be released for rebooking.
- Customers should be able to see available seats and pricing **before confirming** their booking.

## Design Challenges
1. **What new entity/entities do you need to represent individual seats?**
2. **How should Flight manage and expose seat availability?**
3. **What OO principle(s) apply?** (encapsulation, composition, abstraction)
4. **Where does seat-selection logic belong?** (FlightReservation, Flight, a new class?)
5. **How do you enforce seat constraints?** (uniqueness, occupancy state, type-based pricing)

## Edge Cases to Consider
- What if a customer requests a window seat but none are available? (fallback strategy)
- Can a customer change their assigned seat after booking?
- What happens if two customers try to book the same seat simultaneously?
- Should seat prices vary by demand or flight date? (hint: optional extension)
# Phase 2: Requirement Analysis - Customer Journey Map

## Project: Metro Ticket Generating System – ServiceNow

### Commuter Journey Lifecycle

| Stage | Commuter Action | Touchpoint | User Emotion | Pain Points Addressed | System Response |
|---|---|---|---|---|---|
| **1. Awareness & Planning** | Checks metro departure times and station route | Metro Service Portal Homepage | Hopeful | Confusing station maps | Portal displays clear route lines, station list, and live operational status |
| **2. Ticket Selection** | Clicks "Generate Metro Ticket" Record Producer | Service Portal / Service Catalog | Engaged | Complicated paper forms | Responsive form loads with pre-configured passenger details |
| **3. Route & Station Input** | Selects Line, Origin Station, Destination Station, and Ticket Type | Record Producer Variables | Focused | Manual fare lookups | Dynamic dropdowns filter stations; prevents selecting identical source & destination |
| **4. Fare Calculation** | Views total fare auto-updated based on passenger count | Client Script (`onChange`) | Delighted | Overpaying / incorrect change | Instant automatic calculation based on station hops and ticket category |
| **5. Booking Submission** | Selects Payment Mode and clicks "Submit" | Portal Form Action | Confident | Cash dependency & slow counters | Validates mandatory fields and creates record in `u_metro_ticket` |
| **6. Ticket Receipt** | Receives confirmation with Ticket Number (`MTKT0001001`) and pass | "Ticket Created" Confirmation View | Relieved | Lost physical tokens | Generates verifiable digital ticket record with token |
| **7. Boarding & Transit** | Presents digital pass at station turnstile | Digital Ticket Pass on Portal | Satisfied | Queue delays | Ticket state tracks passenger lifecycle (`Active` to `Completed`) |

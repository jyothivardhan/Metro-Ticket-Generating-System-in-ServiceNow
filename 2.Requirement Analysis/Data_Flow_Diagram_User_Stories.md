# Phase 2: Requirement Analysis - Data Flow Diagram & User Stories

## Project: Metro Ticket Generating System – ServiceNow

### 1. Data Flow Diagram (DFD)

#### Level 0 DFD (Context Diagram)
```
[ Commuter / Passenger ]
       │
       │ (1) Enters Journey Details & Submits Booking
       ▼
┌──────────────────────────────────────────────┐
│  ServiceNow Metro Ticket Generating System   │
└──────────────────────────────────────────────┘
       │
       │ (2) Generates Digital Ticket Pass & Record
       ▼
[ Commuter / Ticket Inspector ]
```

#### Level 1 DFD (Process Breakdown)
```
[ Commuter ]
     │
     │ 1. Fill Station & Route Details
     ▼
[ Process 1.0: Record Producer Validation ]
     │
     │ 2. Compute Fare (Client Scripts)
     ▼
[ Process 2.0: Fare Calculation Engine ]
     │
     │ 3. Submit Booking Form
     ▼
[ Process 3.0: Ticket Creation & Token Generation ]
     │
     ├── 4. Store Record ──► [(Database: `u_metro_ticket`)]
     │
     ▼
[ Process 4.0: Ticket Confirmation & Notification ]
     │
     │ 5. Display Ticket Number (e.g. `MTKT0001001`)
     ▼
[ Commuter Portal View ]
```

---

### 2. User Stories & Acceptance Criteria

#### User Story 1: Digital Ticket Booking
- **As a** metro passenger,
- **I want to** select my origin and destination stations on the Service Portal,
- **So that** I can book my ticket online without queuing at physical counters.
- **Acceptance Criteria:**
  - Form must load without errors on desktop and mobile.
  - Commuter must not be allowed to select identical origin and destination stations.
  - Mandatory fields must include Passenger Name, Origin Station, Destination Station, Ticket Type, and Passengers Count.

#### User Story 2: Automated Fare Computation
- **As a** metro commuter,
- **I want** the ticket fare to calculate automatically when I select stations and ticket type,
- **So that** I know the exact price before confirming my booking.
- **Acceptance Criteria:**
  - Dynamic Client Script must fire `onChange` of station or passenger count.
  - Total fare must update in real time without refreshing the page.

#### User Story 3: Ticket Generation & Record Tracking
- **As a** transit station supervisor,
- **I want** each ticket submission to generate a unique ticket number and database record,
- **So that** tickets can be verified and audited in ServiceNow.
- **Acceptance Criteria:**
  - System generates an auto-incremented ticket number with prefix `MTKT` (e.g., `MTKT0001001`).
  - Ticket status is initialized to `Active / Confirmed`.
  - A verification token string is created and linked to the record.

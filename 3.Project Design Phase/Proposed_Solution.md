# Phase 3: Project Design Phase - Proposed Solution

## Project: Metro Ticket Generating System – ServiceNow

### 1. Solution Overview
The proposed solution builds a comprehensive transit ticketing application hosted natively on the ServiceNow cloud platform. It integrates front-end Service Portal capabilities with back-end ServiceNow data persistence and business logic engines.

---

### 2. Core Functional Modules

```
┌─────────────────────────────────────────────────────────────────┐
│                    Metro Service Portal UI                      │
│   ┌─────────────────────┐             ┌─────────────────────┐   │
│   │ Hero & Booking CTA  │             │   Transit Widget    │   │
│   └──────────┬──────────┘             └─────────────────────┘   │
└──────────────┼──────────────────────────────────────────────────┘
               ▼
┌─────────────────────────────────────────────────────────────────┐
│         Record Producer: "Generate Metro Ticket"                │
│   - Variables: Passenger Name, Line, Origin, Dest, Pass. Count  │
│   - Client Script: onChange Dynamic Fare Calculator             │
│   - UI Policy: Field Mandatory & Station Validation Checks      │
└──────────────┬──────────────────────────────────────────────────┘
               ▼
┌─────────────────────────────────────────────────────────────────┐
│            ServiceNow Backend & Data Persistence                │
│   - Application Table: `u_metro_ticket`                         │
│   - Auto Numbering Engine: `MTKT0001001`                        │
│   - Record Producer Script: Ticket Validation Hash & State Init │
│   - Business Rules: Lifecycle Transition & Expiration Logic     │
└─────────────────────────────────────────────────────────────────┘
```

---

### 3. Detailed Component Design

#### Module A: Custom Table (`u_metro_ticket`)
- Captures all transactional ticket details.
- Stores ticket status lifecycle (`New` → `Active` → `Boarded` → `Completed` / `Expired`).
- Maintains auto-generated primary key `u_number` prefixed with `MTKT`.

#### Module B: Record Producer ("Generate Metro Ticket")
- Accessible via the Service Portal Service Catalog.
- Maps catalog variables directly to `u_metro_ticket` fields.
- Validates station choices so Origin and Destination stations cannot be identical.
- Computes dynamic fare instantaneously using JavaScript client-side scripts.

#### Module C: Custom Commercial & Transit Services Widget
- Embedded on the Metro Service Portal page.
- Built using HTML template and CSS/SCSS styling.
- Displays four key commuter reassurance pillars:
  1. **24/7 Smart Transit Assistance**
  2. **Eco-Friendly Paperless Travel**
  3. **Live Network Line Updates**
  4. **Instant Digital Verification**

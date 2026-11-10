# Phase 3: Project Design Phase - Problem-Solution Fit

## Project: Metro Ticket Generating System – ServiceNow

### 1. Problem vs. Solution Mapping

| Commuter Pain Point | Existing Traditional Method | Proposed ServiceNow Solution | Value Delivered |
|---|---|---|---|
| Long queues at physical ticket counters | Commuter must wait in line for 15-20 minutes | Self-service Metro Service Portal with instant ticket generation | Zero queue time; purchase tickets anytime from anywhere |
| Cash handling and exact change hassles | Cash-only or slow POS machines at counters | Digital payment options recorded with automated fare receipts | Faster transactions; eliminates cash dependency |
| Token loss or paper ticket damage | Plastic tokens misplaced; torn paper tickets | Persistent digital ticket record (`MTKT0001001`) with QR token stored in ServiceNow | Eco-friendly; tamper-proof digital records |
| Confusing fare charts & manual errors | Commuters decipher fare matrices at stations | Dynamic Client Script automatically computes total fare | 100% fare accuracy; transparent pricing |
| Lack of audit trail for station managers | Disconnected token counters | Centralized `u_metro_ticket` table with real-time reporting | Complete visibility into passenger volume and revenue |

---

### 2. Value Proposition Canvas
- **Target Customer:** Urban metro commuters and transit passengers.
- **Customer Job:** Travel from Origin Station to Destination Station swiftly and legally.
- **Pain Relievers:**
  - Fast mobile portal booking.
  - Transparent dynamic fare computation.
  - Instantly generated digital ticket number and verification token.
- **Gain Creators:**
  - Eco-friendly paperless travel.
  - Accessible ticket history and receipt.
  - Live network status updates on portal.

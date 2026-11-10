# Phase 3: Project Design Phase - Solution Architecture

## Project: Metro Ticket Generating System – ServiceNow

### 1. High-Level Architecture Diagram

```
+-------------------------------------------------------------------------------+
|                             COMMUTER / USER LAYER                             |
|  [Desktop Web Browser]             [Tablet]              [Mobile Browser]     |
+---------------------------------------+---------------------------------------+
                                        | HTTPS / REST
                                        v
+-------------------------------------------------------------------------------+
|                         PRESENTATION LAYER (PORTAL)                           |
|  Service Portal (/metro_portal)                                               |
|  ├── Header, Navigation & Search Bar                                          |
|  ├── Custom Commercial & Transit Services Widget (HTML/CSS)                   |
|  ├── "Generate Metro Ticket" Record Producer Widget                           |
|  └── "My Active Tickets" / Ticket History Widget                              |
+---------------------------------------+---------------------------------------+
                                        | Client Scripts / UI Policies
                                        v
+-------------------------------------------------------------------------------+
|                       LOGIC & WORKFLOW ENGINE LAYER                           |
|  ServiceNow Platform Engine                                                   |
|  ├── Dynamic Fare Calculation Engine (Client-side JavaScript)                 |
|  ├── Field Validation & Station Compatibility Engine (UI Policies)            |
|  ├── Record Producer Target Mapping & Initialization Script                   |
|  └── Auto-Numbering Engine (Sys Number Counter: MTKT)                         |
+---------------------------------------+---------------------------------------+
                                        | GlideRecord / Data Layer
                                        v
+-------------------------------------------------------------------------------+
|                           DATA PERSISTENCE LAYER                              |
|  ServiceNow Relational Database (MariaDB Underlying)                          |
|  ├── Table: `u_metro_ticket` (Core Ticket Transactional Data)                 |
|  ├── Table: `sys_user` (Commuter / Requester Metadata)                        |
|  ├── Table: `sys_choice` (Lines, Stations, Ticket Types, States)              |
|  └── Audit & Transaction Logs (`sys_audit`, `sys_history_line`)               |
+-------------------------------------------------------------------------------+
```

---

### 2. Entity Relationship (ER) Data Model

```
       ┌──────────────────────┐
       │       sys_user       │
       ├──────────────────────┤
       │ sys_id (PK)          │
       │ name                 │
       │ email                │
       │ phone                │
       └──────────┬───────────┘
                  │ 1
                  │
                  │ submits
                  │
                  │ *
       ┌──────────▼───────────┐
       │    u_metro_ticket    │
       ├──────────────────────┤
       │ sys_id (PK)          │
       │ u_number (MTKT...)   │
       │ u_passenger_name     │
       │ u_passenger_contact  │
       │ u_metro_line         │
       │ u_origin_station     │
       │ u_destination_station│
       │ u_ticket_type        │
       │ u_passengers_count   │
       │ u_fare_amount        │
       │ u_payment_mode       │
       │ u_payment_status     │
       │ u_token_code         │
       │ u_state              │
       │ sys_created_on       │
       └──────────────────────┘
```

---

### 3. Security & Access Architecture
- **Public / Commuter Role:** Ability to access the Service Portal and submit the "Generate Metro Ticket" Record Producer.
- **Station Operator / Inspector Role (`u_metro_inspector`):** Read-only and status-update access to verify ticket numbers and mark tickets as `Boarded` or `Completed`.
- **System Administrator:** Full administrative configuration access across tables, scripts, widgets, and update sets.

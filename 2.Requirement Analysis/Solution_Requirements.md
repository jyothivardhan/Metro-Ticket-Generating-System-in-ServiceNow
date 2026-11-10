# Phase 2: Requirement Analysis - Solution Requirements

## Project: Metro Ticket Generating System – ServiceNow

### 1. Functional Requirements (FR)

| ID | Functional Requirement Description | Priority |
|---|---|---|
| **FR-01** | The system shall provide a Service Portal interface accessible to commuters to view transit services and book tickets. | High |
| **FR-02** | The system shall allow commuters to choose Metro Line, Origin Station, Destination Station, Ticket Type, and Passengers Count. | High |
| **FR-03** | The system shall validate that Origin and Destination stations are distinct and on valid connected lines. | High |
| **FR-04** | The system shall compute total fare in real time based on station distance, ticket class, and passenger multiplier. | High |
| **FR-05** | The system shall create a persistent record in table `u_metro_ticket` upon form submission. | High |
| **FR-06** | The system shall auto-generate a unique ticket number formatted as `MTKT0001001`. | High |
| **FR-07** | The system shall set default ticket state to `Active / Confirmed` with a validity expiration window. | Medium |
| **FR-08** | The system shall support attachment uploads for student/senior-citizen concession passes if applicable. | Low |
| **FR-09** | The system shall feature a custom commercial services widget promoting transit safety, helpline, and eco-benefits. | Medium |

---

### 2. Non-Functional Requirements (NFR)

| ID | Non-Functional Requirement | Specification |
|---|---|---|
| **NFR-01** | **Performance & Latency** | Ticket generation and database record creation must complete within < 2 seconds. |
| **NFR-02** | **Availability** | Accessible 24/7 on cloud-hosted ServiceNow instance. |
| **NFR-03** | **Usability & Responsiveness** | Responsive layout supporting mobile, tablet, and desktop viewports via Bootstrap/CSS. |
| **NFR-04** | **Data Integrity** | Unique indexes on Ticket Number (`u_number`) to prevent duplicate ticket records. |
| **NFR-05** | **Security & Access Control** | Public / authenticated commuter access rules governed by ServiceNow ACLs and User Roles. |

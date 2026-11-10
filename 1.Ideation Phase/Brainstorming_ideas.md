# Phase 1: Ideation Phase - Brainstorming Ideas

## Project: Metro Ticket Generating System – ServiceNow

### 1. Brainstorming Objective
To explore digital solutions leveraging the ServiceNow platform that reduce ticketing queues, automate fare computation, and deliver an intuitive self-service portal experience for metro commuters.

### 2. Idea Exploration & Clustering

#### Idea Cluster 1: Commuter Interface & Self-Service
- **Idea 1.1:** Build a dedicated ServiceNow Service Portal page (`/metro_portal`) with quick action buttons.
- **Idea 1.2:** Use a ServiceNow Record Producer to present a clean, intuitive booking form.
- **Idea 1.3:** Create a custom Commercial & Transit Services widget displaying live transit status, safety guidelines, and 24/7 passenger helpline.

#### Idea Cluster 2: Dynamic Fare & Route Calculation
- **Idea 2.1:** Dynamic station filtering: Selecting a Metro Line (e.g. Blue Line, Red Line) populates valid origin and destination stations.
- **Idea 2.2:** Client-side fare calculation: Automatically calculate total fare based on station hop distance and passenger count using `onChange` Client Scripts.
- **Idea 2.3:** Provide multiple ticket categories (Single Journey, Return Journey, Daily Unlimited Pass).

#### Idea Cluster 3: Ticket Generation & Verification
- **Idea 3.1:** Auto-numbering ticket generation with custom prefix `MTKT0001001`.
- **Idea 3.2:** Generation of a unique digital verification token / simulated QR code payload.
- **Idea 3.3:** Structured lifecycle states (`New` → `Active/Confirmed` → `Boarded` → `Completed` / `Expired`).

### 3. Idea Evaluation & Feasibility Matrix

| Idea | Value to Commuter | Feasibility in ServiceNow | Priority |
|---|---|---|---|
| Service Portal Commuter Interface | High | High (Portal Designer & Widgets) | Must Have (P1) |
| Record Producer Booking Form | High | High (Service Catalog & Variables) | Must Have (P1) |
| Dynamic Fare & Station Scripting | High | Medium (Client Script & UI Policies) | Must Have (P1) |
| Custom Transit & Commercial Widget | Medium | High (HTML/CSS/SCSS Widget) | Must Have (P1) |
| Ticket Auto-Numbering & State Flow | High | High (Custom Table & Business Rules) | Must Have (P1) |
| Physical Turnstile Hardware Integration | High | Low (Out of Scope for initial release) | Future Scope |

### 4. Selected Core Solution
Deliver a custom ServiceNow application equipped with:
1. `u_metro_ticket` custom data table.
2. "Generate Metro Ticket" Record Producer.
3. Service Portal page with custom commercial/transit info widget.
4. Auto-calculation of fares and immediate generation of digital ticket records.

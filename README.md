# Metro Ticket Generating System – ServiceNow

## Overview

This project implements an automated, self-service **Metro Ticket Generating System** using the **ServiceNow** platform. 

The solution provides commuters with a streamlined, digital ticketing portal to select routes, choose origin and destination stations, calculate fares dynamically, and generate instant digital metro tickets with unique reference IDs and simulated QR tokens. The system captures and stores every booking as a structured ticket record in a custom ServiceNow database table for real-time tracking, validation, and administrative management, eliminating physical ticket counter queues and manual ticketing overhead.

---

## Key Features

- **Custom ServiceNow Scoped Application:** Dedicated application architecture for metro transit ticketing.
- **Custom Metro Tickets Table (`u_metro_ticket`):** Structured data model capturing ticket number, passenger details, route, fare, payment status, and validity.
- **Dynamic Fare Calculation:** Automated calculation of travel fares based on origin station, destination station, and passenger count using Client Scripts / UI Policies.
- **Record Producer for Ticket Booking:** User-friendly "Generate Metro Ticket" catalog item / record producer embedded in the Service Portal.
- **Service Portal Integration:** Commuter-facing portal with quick booking, route information, fare charts, and active ticket lookup.
- **Custom Commercial & Transit Services Widget:** Custom HTML, CSS/SCSS, and Client Script widget showcasing metro network updates, passenger guidelines, 24/7 helpline, and fast transit benefits.
- **Unique Ticket Numbering & Token Generation:** Automatic auto-numbering (e.g., `MTKT0001001`) and unique digital ticket verification token on submission.
- **Ticket Lifecycle State Management:** Clear status transitions from Generation to Active, Boarded, Expired, or Cancelled.
- **Attachment & Pass Support:** Ability to attach ID proof or export/print digital ticket passes.
- **Responsive & Intuitive Interface:** Mobile-friendly and clean user interface accessible on all standard web and mobile browsers.

---

## Workflow

```
   Commuter Opens Metro Service Portal
                    ↓
   Selects "Book / Generate Metro Ticket"
                    ↓
   Selects Origin & Destination Stations
                    ↓
   Chooses Ticket Type & Number of Passengers
                    ↓
   System Auto-Calculates Total Fare Amount
                    ↓
   Selects Payment Mode & Submits Booking
                    ↓
   ServiceNow Record Producer Executes
                    ↓
   Metro Ticket Record Generated (`u_metro_ticket`)
                    ↓
   Unique Ticket Number (e.g., `MTKT0001001`) & QR Pass Issued
                    ↓
   Commuter Views / Downloads Digital Ticket
```

---

## Metro Lines & Stations

### Blue Line (East – West Corridor)
- Terminal A (Central Hub)
- Station 1 (Tech Park)
- Station 2 (City Square)
- Station 3 (University Road)
- Terminal B (Airport Gateway)

### Red Line (North – South Corridor)
- North Gate
- Financial District
- Central Hub (Interchange Station)
- South Boulevard
- Industrial Estate

---

## Ticket Types

- **Single Journey Ticket (SJT):** Valid for one-way transit on the selected route for 120 minutes.
- **Return Journey Ticket (RJT):** Valid for round trip travel between origin and destination on the same calendar day.
- **Daily Unlimited Pass:** Unlimited rides across all lines until midnight on the day of issue.
- **Weekend Tourist Pass:** 48-hour unlimited weekend transit pass for tourists and frequent travelers.

---

## Ticket States

- **New:** Ticket request initiated, awaiting confirmation / payment verification.
- **Active / Confirmed:** Ticket generated successfully, valid for passenger boarding and station check-in.
- **Boarded / In-Transit:** Passenger checked in at the entry turnstile gate.
- **Completed:** Passenger exited destination station gate; journey marked complete.
- **Expired:** Journey validity time window has lapsed without check-in.
- **Cancelled / Refunded:** Ticket cancelled by passenger prior to travel validity period.

---

## Service Portal

The project features a commuter-centric **Metro Transit Service Portal** designed with ServiceNow Service Portal Designer:

- **Global Search:** Search station lists, fare rules, schedules, and ticket records.
- **Hero Banner & Quick Booking:** Direct call-to-action button to initiate "Generate Metro Ticket".
- **Interactive Transit Services Section:** Highlights metro safety guidelines, operating hours (06:00 AM – 11:00 PM), and passenger helpline.
- **My Active Metro Tickets:** Widget displaying commuter's recently generated tickets with live status badges.
- **Route & Fare Calculator Quick Link:** Quick lookup for station-to-station distances and approximate travel times.

---

## Custom Widget

A custom **Metro Transit Information & Services Widget** was developed using HTML, CSS/SCSS, and Client Scripting:

- **24/7 Smart Transit Assistance:** Instant answers to common ticketing and luggage queries.
- **Fast & Paperless Travel:** Green eco-friendly digital ticket issuing without queue delays.
- **Live Network Status:** Real-time operational indicator showing all lines operating on schedule.
- **Secure Digital Token Validation:** Tamper-proof booking references and instant receipt verification.

---

## Technologies Used

- **ServiceNow Platform:** Vancouver / Washington DC / Xanadu Release
- **ServiceNow Service Portal & Portal Designer**
- **ServiceNow Record Producer & Service Catalog**
- **Client Scripts (onChange, onLoad, onSubmit)**
- **UI Policies & Data Policies**
- **Business Rules**
- **Custom Application Tables & Dictionaries**
- **HTML5 & CSS3 / SCSS**
- **JavaScript (ES5/ES6 ServiceNow Client & Server-side API)**
- **GitHub:** Source code, documentation, and version control

---

## Implementation Details

### 1. Custom Table: `u_metro_ticket`
| Field Label | Field Name | Type | Notes |
|---|---|---|---|
| Ticket Number | `u_number` | Auto-Number | Prefix: `MTKT`, 7 digits (e.g., `MTKT0001001`) |
| Passenger Name | `u_passenger_name` | String (100) | Full name of commuter |
| Passenger Contact | `u_passenger_contact` | String (20) | Phone number / Email address |
| Metro Line | `u_metro_line` | Choice | Blue Line, Red Line, Green Line |
| Origin Station | `u_origin_station` | Choice / Reference | Starting station |
| Destination Station | `u_destination_station` | Choice / Reference | Destination station |
| Ticket Type | `u_ticket_type` | Choice | Single Journey, Return, Day Pass |
| Number of Passengers | `u_passengers_count` | Integer | Minimum 1, Maximum 6 per booking |
| Fare Amount | `u_fare_amount` | Currency / Decimal | Dynamic calculated fare |
| Payment Mode | `u_payment_mode` | Choice | UPI, Credit/Debit Card, Net Banking, Smart Wallet |
| Payment Status | `u_payment_status` | Choice | Pending, Paid, Failed |
| Ticket State | `u_state` | Choice | New, Active, Boarded, Completed, Expired, Cancelled |
| QR / Token Code | `u_token_code` | String (100) | Unique verification hash / token |

### 2. Record Producer: `Generate Metro Ticket`
- Mapped to table `u_metro_ticket`
- Catches variables from user input and populates database record on submission
- Script computes ticket validation string and sets initial state to `Active / Confirmed`

---

## Result

The commuter selects origin and destination stations, ticket type, and number of passengers from the Metro Service Portal. Upon form submission, the system immediately calculates the fare, processes the ticket generation, and creates a verified ticket record in ServiceNow.

**Example Generated Ticket:**
- **Ticket Number:** `MTKT0001001`
- **Passenger:** Alex Johnson
- **Route:** Blue Line (Terminal A Central Hub → Station 2 City Square)
- **Ticket Type:** Single Journey Ticket
- **Passengers:** 2
- **Fare Amount:** \$4.00 (₹60.00)
- **Status:** Active / Confirmed
- **Validity:** 120 Minutes from generation time

---

## Demo

- **ServiceNow Commuter Portal URL:** `[Add your ServiceNow instance demo URL here]`
- **Video Demonstration:** Check [`Demo_link`](Demo_link) file for recorded video walkthrough.

---

## Screenshots

### 1. Metro Service Portal Homepage
![Metro Service Portal Homepage](screenshots/01_portal_homepage.png)

### 2. Generate Metro Ticket Form (Record Producer)
![Generate Metro Ticket Form](screenshots/02_ticket_booking_form.png)

### 3. Dynamic Fare Calculation & Validation
![Dynamic Fare Calculation](screenshots/03_fare_calculation.png)

### 4. Generated Metro Ticket Record
![Generated Metro Ticket Record](screenshots/04_ticket_record_created.png)

### 5. Metro Transit Services Custom Widget
![Metro Transit Services Custom Widget](screenshots/05_custom_transit_widget.png)

---

## Project Structure

```
├── 1.Ideation Phase
│   ├── Brainstorming_ideas.md
│   ├── Define_Problem_Statement.md
│   └── Empathy_Map.md
├── 2.Requirement Analysis
│   ├── Customer_Journey_Map.md
│   ├── Data_Flow_Diagram_User_Stories.md
│   ├── Solution_Requirements.md
│   └── Technology_Stack.md
├── 3.Project Design Phase
│   ├── Problem_Solution_Fit.md
│   ├── Proposed_Solution.md
│   └── Solution_Architecture.md
├── 4.Project Planning Phase
│   └── Project_Planning_Schedule.md
├── 5.Project Development Phase
│   ├── Functional_Testing.md
│   ├── Performance_Testing.md
│   └── User_Acceptance_Testing_UAT.md
├── 6.Project Documentation
│   └── Final_Project_Report.md
├── 7.Project Demonstration
│   └── Project_Demonstration_Guide.md
├── screenshots
│   └── .gitkeep
├── Demo_link
└── README.md
```

---

## How to Deploy / Import into ServiceNow

1. **Log in** to your ServiceNow Personal Developer Instance (PDI) as an System Administrator.
2. Navigate to **System Update Sets** > **Retrieved Update Sets** (or import via Studio / Source Control).
3. Connect repository `https://github.com/jyothivardhan/Metro-Ticket-Generating-System-in-ServiceNow` via **Studio** > **Source Control** > **Link to Source Control**.
4. Alternatively, create the scoped application `Metro Ticket Generating System` and configure:
   - Table `u_metro_ticket` with the specified dictionary fields.
   - Record Producer `Generate Metro Ticket` under Service Catalog.
   - Service Portal page with the custom `Metro Transit Information & Services` widget.
5. Preview, test ticket generation, and mark the update set as **Complete**.

---

## Author

- **Jyothi Vardhan**
- GitHub: [@jyothivardhan](https://github.com/jyothivardhan)

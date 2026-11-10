# Phase 7: Project Demonstration Guide

## Project: Metro Ticket Generating System – ServiceNow

### 1. Demonstration Video Script & Flow (3 to 5 Minutes)

| Time Stamp | Section | Speaker Action & Visual Focus |
|---|---|---|
| **0:00 – 0:45** | **Introduction & Problem Context** | Show title slide. Introduce author (Jyothi Vardhan) and problem statement: physical ticket queues at metro stations and token loss issues. |
| **0:45 – 1:30** | **ServiceNow Architecture** | Briefly navigate to ServiceNow Studio / Application Navigator. Showcase custom table `u_metro_ticket`, field dictionary, and auto-numbering prefix `MTKT`. |
| **1:30 – 2:45** | **Live Commuter Portal Walkthrough** | Navigate to `/metro_portal`. Highlight custom commercial & transit widget. Click "Generate Metro Ticket". Demonstrate dynamic station selection and dynamic fare calculation for 2 passengers. |
| **2:45 – 3:45** | **Ticket Generation & Backend Record** | Click "Submit". Showcase generation of Ticket `MTKT0001001`. Open the created record in ServiceNow backend; verify status `Active / Confirmed` and unique token code. |
| **3:45 – 4:30** | **Testing, Benefits & Conclusion** | Summarize test results, paperless environmental benefits, and future enhancements (turnstile IoT and QR codes). Conclude presentation. |

---

### 2. Demonstration Checklist
- [x] Working ServiceNow Developer Instance with `u_metro_ticket` configured.
- [x] Record Producer "Generate Metro Ticket" available on portal.
- [x] Dynamic Fare Calculation script active.
- [x] Custom Transit Services widget embedded on portal page.
- [x] Sample ticket `MTKT0001001` generated.
- [x] Screen recording uploaded to Google Drive / YouTube (linked in `Demo_link`).

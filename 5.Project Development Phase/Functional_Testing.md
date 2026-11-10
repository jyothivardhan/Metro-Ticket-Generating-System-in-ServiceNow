# Phase 5: Project Development Phase - Functional Testing

## Project: Metro Ticket Generating System – ServiceNow

### 1. Functional Test Execution Matrix

| Test Case ID | Test Scenario | Test Steps | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|
| **TC-FN-01** | Load Metro Service Portal | Navigate to `/metro_portal` URL | Portal loads with header, custom transit widget, and booking button | Portal loaded cleanly with all elements visible | **PASS** |
| **TC-FN-02** | Open Record Producer | Click "Generate Metro Ticket" CTA | Booking form loads with variables: Name, Line, Origin, Destination, Passengers | Form loaded with all fields present and editable | **PASS** |
| **TC-FN-03** | Validate Dynamic Station Loading | Select "Blue Line" from Metro Line dropdown | Origin and Destination dropdowns show Blue Line stations | Stations populated according to selected line | **PASS** |
| **TC-FN-04** | Prevent Same Origin and Destination | Select Origin = "Central Hub" and Destination = "Central Hub" | System alerts user or disables submit with error message | Alert displayed: "Origin and Destination cannot be the same" | **PASS** |
| **TC-FN-05** | Dynamic Fare Calculation | Select Origin = "Terminal A", Destination = "Station 2", Passengers = 2 | Total Fare auto-calculates to expected amount ($4.00 / ₹60) | Total fare updated instantly without page reload | **PASS** |
| **TC-FN-06** | Ticket Submission & Record Creation | Fill valid inputs, select payment mode, click "Submit" | Ticket record created in `u_metro_ticket` with status `Active/Confirmed` | Record created with number `MTKT0001001` | **PASS** |
| **TC-FN-07** | Mandatory Fields Enforcement | Attempt to submit form with empty Passenger Name | Form submission blocked, mandatory field highlighted in red | Submission blocked with mandatory field notification | **PASS** |
| **TC-FN-08** | Digital Token Generation | Inspect created record `MTKT0001001` | Token code string populated with unique verification hash | Token hash verified and unique | **PASS** |
| **TC-FN-09** | State Transition Verification | Update ticket state from `Active` to `Boarded` and `Completed` | State transition permitted and saved in record history | State updated successfully with audit trail | **PASS** |

# CASE STUDY: EMR Testing – SQL Validation & API Sync Delay Resolution

Objective
Validate real-time update of imaging results displayed in the EMR user interface.

---

Scope
- EMR user interface accuracy
- SQL database record validation
- API sync timing and cache behavior
- Refresh logic and data propagation

---

Preconditions
✔️ EMR testing environment active  
✔️ SQL access available  
✔️ New imaging data written to backend database  

---

Test Steps & Expected Results

| Step | Action | Expected Result |
|------|--------|----------------|
| 1 | Update SQL record with new imaging value | Database saves updated value |
| 2 | Refresh EMR interface | Updated value appears in UI |
| 3 | Compare UI values with SQL stored values | UI matches database result |
| 4 | Review API logs or response payload | Latest record retrieved via API |
| 5 | Perform peak-load or rapid refresh testing | No observable sync delay |
| 6 | Document defect with evidence | Jira ticket includes SQL screenshots and UI proof |

---

Defect Identified
EMR displayed outdated imaging value due to API cache refresh delay.

---

Outcome
- Fix ensured accurate real-time clinical updates  
- Eliminated outdated data display  
- Improved provider confidence and patient safety  

All evidence, screenshots, SQL validation, and retesting results were logged in Jira for traceability and closure.

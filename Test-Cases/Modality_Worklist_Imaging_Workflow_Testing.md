# CASE STUDY: Modality Worklist & Imaging Workflow – Ultrasound, MRI, CT

Objective
Validate that imaging orders placed in the EMR/RIS appear correctly on the modality worklist (Ultrasound, MRI, CT), are acquired under the correct patient, and transmit accurately into PACS/EMR.

---

Scope
- Order creation in EMR/RIS
- Modality worklist population for Ultrasound, MRI, CT
- Patient demographic and exam detail accuracy
- Image acquisition and completion status
- PACS/EMR reconciliation

---

Preconditions
✔️ EMR/RIS system available with ordering capability  
✔️ Modality worklist service running and configured for Ultrasound, MRI, CT  
✔️ DICOM routing between modalities and PACS/EMR in place  
✔️ Test patient accounts available

---

Test Steps & Expected Results

| Step | Action | Expected Result |
|------|--------|----------------|
| 1 | Create imaging orders in EMR for Ultrasound, MRI, and CT for a test patient | Orders save successfully with correct patient demographics, modality, body part, and priority |
| 2 | At the modality console, refresh the worklist | New orders appear on the appropriate modality worklist with matching patient info and exam details |
| 3 | Select an Ultrasound order from the worklist and start acquisition | Patient demographics auto-populate correctly from worklist; no manual re-entry needed |
| 4 | Complete the Ultrasound exam and send images to PACS | Study arrives in PACS under the correct patient, with correct modality and study description |
| 5 | Repeat acquisition and completion for MRI and CT orders | MRI and CT studies also route successfully to PACS and appear in EMR as completed exams |
| 6 | Compare PACS metadata with EMR order details and worklist | Patient name, MRN, accession number, modality, and study description all match |
| 7 | Negative test: Cancel an order in EMR after it has appeared on the worklist | Cancelled order is removed or clearly flagged on the worklist; cannot be accidentally acquired as active exam |
| 8 | Negative test: Intentionally select the wrong patient/order on the console (where allowed in test environment) | System either blocks inconsistent selection or records clear audit trails for mismatch prevention and investigation |

---

Defects Identified
- One MRI order displayed with outdated study description due to cached worklist data  
- Cancelled CT orders remained selectable on the modality worklist until manual refresh, creating potential for wrong-exam acquisition

---

Outcome
The testing:
- Confirmed accurate linkage between EMR orders, modality worklist, and PACS/EMR completion status  
- Identified caching and cancellation edge cases that could affect workflow safety  
- Supported improvements to refresh behavior and worklist handling to reduce wrong-patient/wrong-exam risk  

All defects, screenshots, and workflow notes were documented in Jira, and fixes were verified in follow-up regression testing.

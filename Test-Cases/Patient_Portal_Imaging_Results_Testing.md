# CASE STUDY: Patient Portal (“MyChart”) Imaging Results Delivery

Objective
Ensure that finalized imaging results (Ultrasound, MRI, CT) are securely and accurately delivered to patients through the patient portal, without exposing PHI inappropriately or before provider review when restricted.

---

Scope
- Patient portal (“MyChart”-style) access
- Imaging results visibility rules (release timing, status)
- EMR ↔ portal synchronization
- PHI masking and security
- Device/browser compatibility for result viewing

---

Preconditions
✔️ Valid patient account with portal access  
✔️ Completed imaging studies (Ultrasound, MRI, CT) with signed reports in EMR  
✔️ EMR–portal interface and APIs active  
✔️ Appropriate release rules configured (e.g., provider sign-off required before release)

---

Test Steps & Expected Results

| Step | Action | Expected Result |
|------|--------|----------------|
| 1 | Log in to patient portal with valid credentials | Login succeeds; PHI is visible only for the authenticated patient |
| 2 | Navigate to “Test Results” or “Imaging Results” section | Completed imaging studies (Ultrasound, MRI, CT) are listed correctly with date, modality, and provider |
| 3 | Open a finalized Ultrasound result | Report text and key findings display accurately, matching EMR; no truncated or corrupted data |
| 4 | Open finalized MRI and CT results on web and mobile | Results display consistently across devices; formatting remains readable and secure |
| 5 | Verify timing rules (e.g., open result before provider sign-off) | Result is either hidden, clearly marked as pending, or blocked according to release configuration |
| 6 | Compare portal result content with EMR/SQL data | Patient name, MRN, date, modality, and impression match backend data exactly |
| 7 | Attempt to access another patient’s result (URL tampering, back/forward, etc.) | Access is denied; no cross-patient PHI leakage |
| 8 | Log out and use browser back button | PHI is not displayed after logout; session properly terminated |

---

Defects Identified
- Inconsistent result status between EMR and portal for “pending” reports  
- One test showed partial PHI still briefly cached after logout on mobile browser  

---

Outcome
Testing confirmed:
- Secure, accurate delivery of imaging results to the correct patient  
- No cross-patient PHI exposure when navigating or manipulating URLs  
- Alignment between EMR data and patient portal display  

All findings, including timing rule issues and caching behavior, were documented in Jira with screenshots and SQL evidence, then retested after fixes.

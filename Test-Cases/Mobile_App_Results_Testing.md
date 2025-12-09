# CASE STUDY: Mobile App Testing – Secure Patient Results Delivery

Objective
Ensure secure, accurate delivery of gender test results to patients via a mobile application.

---

Scope
- App installation and onboarding
- Identity verification
- Secure login and authentication
- API response validation
- SQL database result matching
- HIPAA compliance & PHI protections

---

Preconditions
✔️ Patient results exist in database  
✔️ API endpoints available and online  
✔️ Mobile device configured and ready for testing  

---

Test Steps & Expected Results

| Step | Action | Expected Result |
|------|--------|----------------|
| 1 | Install mobile application | Installation completes without errors |
| 2 | Complete identity verification | Only verified patients are allowed through onboarding |
| 3 | Login using valid credentials | Secure authentication succeeds |
| 4 | Execute `GET /results` | API returns correct patient result data |
| 5 | Compare UI result display against SQL stored values | UI values match backend records |
| 6 | Attempt unauthorized login or identity spoofing | Access is denied and patient PHI is protected |
| 7 | Validate HIPAA and security controls | No PHI exposure, encryption confirmed, secure handling verified |

---

Defects Identified
- Cached UI data mismatch with backend result  
- Missing audit log entry during unauthorized access attempts  

---

Outcome
Testing confirmed:
- Safe and accurate patient result access  
- Integrity between UI, API, and SQL data  
- Compliance with HIPAA and PHI handling standards  

All findings, defects, evidence, and retesting outcomes were documented in Jira for resolution and traceability.

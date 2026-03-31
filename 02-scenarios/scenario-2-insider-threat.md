# Scenario 2: Insider Threat / Data Exfiltration

**Classification:** Exercise Material / Facilitator Only  
**Scenario Code:** TTX-MC-002  
**Duration:** 75-90 minutes  
**Difficulty:** Intermediate  
**Threat Vector:** Internal, departing employee  
**MedCaribe Risks Tested:** RISK-003 (Unauthorized EHR Access, Score 16), RISK-004 (Data via WhatsApp, Score 15), RISK-013 (Unencrypted USB, Score 12), RISK-014 (No Data Classification, Score 10)

---

## Scenario Overview

**For facilitator eyes only. Do not distribute to participants before the exercise.**

A senior nurse at MedCaribe's Chaguanas Medical Centre has quietly accepted a position at a competing private healthcare provider. Two weeks before their last day, the nurse begins systematically accessing patient records they have no clinical reason to view. They download patient lists and contact information, transferring data to a personal USB drive and forwarding select records to a personal Gmail account. The activity is discovered when the IT Administrator, during a routine weekly log review, notices an unusual spike in EHR record access from the nurse's account.

This scenario is more complex than Scenario 1 because it involves an active employee, HR coordination, evidence handling for potential legal proceedings, and the sensitivity of accusing a staff member of wrongdoing before all facts are confirmed.

---

## Participants Required

| Role | Who at MedCaribe | Exercise Role |
|------|-----------------|---------------|
| Incident Coordinator | K. Rampersad (Operations Manager) | Leads the response |
| Technical Lead | M. Doyle (IT Administrator) | Investigates and provides evidence |
| Decision Authority | Dr. A. Dorian (Medical Director) | Approves escalation and notifications |
| HR Representative | HR Manager (or Ops Manager in dual role) | Handles employee-related decisions |
| Clinical Manager | Chaguanas Clinic Manager | Provides clinical context on access patterns |
| Observer | Facilitator or designated observer | Tracks observations |

---

## INJECT 1: The Anomalous Access Pattern

**Read aloud to participants:**

"It is Wednesday afternoon. The IT Administrator is performing the weekly M365 audit log review (recently implemented per the security program). While reviewing CloudMed EHR access logs, they notice that a senior nurse at the Chaguanas Medical Centre, who normally accesses 15-25 patient records per shift, accessed 187 patient records over the past 3 days. Many of these records belong to patients the nurse has no scheduled appointments with and who are assigned to physicians at other MedCaribe locations. The nurse has been employed at MedCaribe for 4 years and has had no prior performance or conduct issues."

**Primary question:** "You have an anomalous access pattern from a trusted, long-term employee. What do you do?"

**Follow-up probing questions:**
- Is this an incident or just unusual behavior? How do you decide?
- Do you confront the nurse immediately? Why or why not?
- Who do you inform at this stage? Do you involve HR right away?
- What additional information do you need before taking any action?
- How do you continue monitoring without tipping off the employee?
- What does the Access Control Policy (POL-002) say about access reviews?

**Key points to listen for:**
- NOT immediately confronting the nurse (preserve the investigation)
- Treating this as a suspected incident requiring investigation, not a confirmed one
- Involving the Incident Coordinator (Operations Manager) and notifying HR discreetly
- Requesting clinical context from the Clinic Manager (is there a legitimate reason for this access pattern?)
- Checking if the nurse has submitted a resignation or is known to be departing
- Beginning to document findings in an incident log with timestamps

---

## INJECT 2: The Resignation Connection

**Read aloud:**

"The Operations Manager quietly checks with HR and discovers that the nurse submitted their resignation 5 days ago, with their last day scheduled for 2 weeks from now. The resignation was accepted by the Chaguanas Clinic Manager but has not yet been widely communicated. HR also mentions that the nurse asked for a reference letter from the Medical Director, which was provided.

Meanwhile, the IT Administrator has expanded the log review and found the following:
- The 187 records accessed over 3 days include patients across all four MedCaribe locations, not just Chaguanas
- 63 of these records were opened and viewed for less than 10 seconds each (suggesting the nurse was scrolling through quickly, not providing clinical care)
- The nurse's most recent shift ended at 5 PM, but 47 of the record accesses occurred between 5:15 PM and 6:30 PM while the nurse was off-duty"

**Primary question:** "The access pattern now looks deliberate and connected to the resignation. What changes about your response?"

**Follow-up probing questions:**
- What severity level is this now? Has it changed from Inject 1?
- Do you escalate to the Medical Director at this point?
- The nurse is still actively employed and working shifts. Do you restrict their access now? How?
- If you restrict access, does the nurse find out they are under investigation? How do you handle that?
- What evidence are you preserving and how?
- Do you check for data leaving the organization (email, USB, cloud)?

**Key points to listen for:**
- Escalation to Medical Director given the confirmed resignation connection
- Decision about whether to restrict EHR access (balance: stop potential ongoing exfiltration vs. alert the nurse)
- Checking M365 audit logs for emails sent to external addresses from the nurse's account
- Checking for USB device connections on the nurse's workstation (if Defender for Business is logging device activity)
- Evidence documentation with chain of custody awareness
- HR involvement for managing the employee situation parallel to the technical investigation

---

## INJECT 3: Data Has Left the Building

**Read aloud:**

"The IT Administrator finds the following additional evidence:

1. The nurse's M365 account shows 4 emails sent to a personal Gmail address over the past week. The emails contain Excel attachments. The IT Administrator cannot see the file contents from the audit log alone, but the file names are 'patient_contacts_south.xlsx', 'patient_contacts_central.xlsx', 'diabetic_patients_list.xlsx', and 'corporate_medicals_2025.xlsx'.

2. USB device logs from Defender show that an unencrypted 32GB USB drive was connected to the nurse's Chaguanas workstation on 3 separate occasions in the past week.

3. The Chaguanas Clinic Manager, when asked discreetly about the nurse's recent behavior, mentions that the nurse has been 'staying late to finish paperwork' and was seen using their personal phone to photograph something on the screen last Thursday, though the manager thought nothing of it at the time."

**Primary question:** "You now have evidence of patient data being exfiltrated via email, USB, and potentially photographs. Walk me through your response."

**Follow-up probing questions:**
- Is this now a confirmed data breach under the Data Protection Act?
- What types of patient data are likely in those files? What classification level is it?
- Can you recover the data from the personal Gmail or USB drive? What are your legal options?
- When and how do you confront the nurse?
- Do you involve law enforcement at this point? What would you tell them?
- Do you let the nurse finish their remaining 2 weeks, or do you end their employment immediately?
- How do you handle the physical phone photographs? Can you recover that data?

**Key points to listen for:**
- Classification as a confirmed data breach (personal and medical data exfiltrated outside organizational control)
- Recognition that data sent to personal Gmail and stored on personal USB is now outside MedCaribe's ability to control or delete
- Medical Director authorization for employee termination decision (HR, legal, and Ops Manager coordination)
- Evidence preservation before any confrontation (screenshot logs, export audit records, preserve email evidence)
- Understanding that the phone photographs are essentially unrecoverable
- Data Protection Act notification assessment: patient names, medical conditions, contact details, and corporate client data have been exfiltrated
- Law enforcement consideration (data theft is a criminal matter)

---

## INJECT 4: The Confrontation and Aftermath

**Read aloud:**

"The Medical Director authorizes immediate action. The Operations Manager and HR Manager meet with the nurse. During the meeting:

- The nurse initially denies accessing records inappropriately
- When presented with the log evidence showing off-hours access to records from other locations, the nurse claims they were 'doing research to prepare for their new role'
- When asked about the emails to personal Gmail, the nurse states they were 'backing up personal notes' and becomes defensive
- The nurse refuses to hand over the USB drive, stating it contains 'personal property'
- The nurse's employment is terminated effective immediately. Their badge and keys are collected. IT disables all accounts within 15 minutes of the meeting.

The nurse leaves the premises. However, you now know that patient data for potentially hundreds of patients is on the nurse's personal email, personal USB drive, and personal phone."

**Primary question:** "The employee is gone but the data is still out there. What happens next?"

**Follow-up probing questions:**
- Can you compel the former employee to return or delete the data? What legal mechanisms exist?
- How many patients are affected? Can you determine the exact number from the EHR logs?
- Do you need to notify the Information Commissioner? What information do you provide?
- Do you notify the affected patients? All of them, or only those whose data was confirmed exfiltrated?
- Some of the data includes corporate medical clients. Do you notify those corporate clients?
- What about the "diabetic patients list"? Is there a heightened sensitivity for medical condition data?
- Do you file a report with the TTPS Cyber Crime Unit?

**Key points to listen for:**
- Legal consultation for compelling data return (cease and desist letter, potential civil action)
- Police report for data theft
- Regulatory notification to the Information Commissioner (this meets the threshold: confirmed exfiltration of personal and sensitive medical data)
- Patient notification plan (scope, timing, content, method)
- Corporate client notification (occupational health data was included)
- Understanding that medical condition data (diabetes list) is classified as sensitive personal information under the DPA and carries higher obligations
- Preserving all evidence for potential legal proceedings

---

## INJECT 5: Lessons and Systemic Fixes

**Read aloud:**

"It is now 3 weeks after the incident. The former nurse's new employer has been contacted (via legal counsel) and informed that the data was obtained improperly. A police report has been filed. The Information Commissioner has been notified. Patient notifications are being prepared.

The post-incident review is scheduled for today. Looking at this incident end to end, the following contributed to the breach:

- The nurse had access to all patient records across all locations, not just their own patients
- No automated alerting existed for unusual EHR access patterns
- USB drives could be connected to workstations without restriction
- Email to personal addresses was not blocked
- No offboarding process existed to restrict access during the notice period
- The resignation was not communicated to IT"

**Primary question:** "What systemic changes do you recommend to prevent this from happening again?"

**Follow-up probing questions:**
- Which of these failures could have been prevented by controls already planned in the remediation roadmap?
- What new policies or procedures are needed?
- Should MedCaribe implement a different access model for departing employees during their notice period?
- How do you update the risk register based on this incident?
- What would you tell the Medical Director about the cost of implementing these controls versus the cost of this breach?

**Key points to listen for:**
- Role-based access control in the EHR (nurses only see their own location's patients, or only patients they have appointments with)
- Automated alerts for bulk record access or access outside scheduled shifts
- USB device control via Intune (block or encrypt)
- Email DLP or transport rules blocking external forwarding of files with patient identifiers
- Offboarding procedure that restricts access on resignation date, not departure date
- Mandatory IT notification when any employee submits resignation
- These map to existing Project 1 recommendations and Project 2 M365 controls (Intune device control, Exchange transport rules, Conditional Access)

---

## Exercise Outcomes Checklist

| Capability | Demonstrated? | Notes |
|-----------|---------------|-------|
| Recognized anomalous access as warranting investigation | Yes / No / Partial | |
| Did not prematurely confront the employee | Yes / No / Partial | |
| Involved HR appropriately and discreetly | Yes / No / Partial | |
| Escalated to Medical Director at the right point | Yes / No / Partial | |
| Preserved evidence before confrontation | Yes / No / Partial | |
| Identified data exfiltration via multiple channels | Yes / No / Partial | |
| Assessed DPA notification requirements correctly | Yes / No / Partial | |
| Considered law enforcement involvement | Yes / No / Partial | |
| Developed a patient notification plan | Yes / No / Partial | |
| Identified systemic improvements post-incident | Yes / No / Partial | |
| Connected findings to existing risk register and roadmap | Yes / No / Partial | |

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | April 2026 | J. Maitland | Initial scenario |

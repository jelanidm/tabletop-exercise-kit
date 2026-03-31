# Scenario 3: Third-Party Vendor Breach

**Classification:** Exercise Material / Facilitator Only  
**Scenario Code:** TTX-MC-003  
**Duration:** 75-90 minutes  
**Difficulty:** Advanced  
**Threat Vector:** Supply chain / third-party vendor  
**MedCaribe Risks Tested:** RISK-006 (Unverified EHR Backup, Score 15), RISK-009 (Cross-Border Transfers, Score 15), RISK-019 (No Vendor Risk Assessment, Score 9)

---

## Scenario Overview

**For facilitator eyes only. Do not distribute to participants before the exercise.**

MedCaribe's cloud-based EHR provider, CloudMed, suffers a ransomware attack that compromises their hosted infrastructure. CloudMed notifies MedCaribe that patient records may have been accessed by the attackers prior to encryption. The breach affects multiple CloudMed clients across the Caribbean. MedCaribe has limited visibility into the extent of the compromise, limited ability to investigate CloudMed's systems, and no guaranteed timeline for service restoration.

This scenario is the most challenging because MedCaribe is largely dependent on a third party. The exercise tests how the team responds when they do not control the environment, do not have full information, and must make decisions under uncertainty.

---

## Participants Required

| Role | Who at MedCaribe | Exercise Role |
|------|-----------------|---------------|
| Incident Coordinator | K. Rampersad (Operations Manager) | Leads MedCaribe's response |
| Technical Lead | M. Doyle (IT Administrator) | Manages MedCaribe-side technical response |
| Decision Authority | Dr. A. Dorian (Medical Director) | Approves notifications and business decisions |
| Finance Manager | S. Mohammed | Assesses financial and insurance implications |
| Clinical Representative | Any Clinic Manager | Provides clinical operations context |
| Observer | Facilitator or designated observer | Tracks observations |

---

## INJECT 1: The Vendor Notification

**Read aloud to participants:**

"It is Monday at 7:45 AM. The Operations Manager receives a phone call from CloudMed's client relations team. The caller states:

'We are contacting you to inform you that CloudMed experienced a cybersecurity incident over the weekend. Our systems were affected by a ransomware attack on Saturday evening. We are currently working to restore services. The CloudMed EHR platform is currently offline and we do not have an estimated time for restoration. We are conducting an investigation and will provide further updates. We recommend that you activate your business continuity procedures.'

The caller provides a reference number and a dedicated email address for incident-related questions. They do not provide specific details about whether MedCaribe's data was accessed.

Meanwhile, clinical staff at all four MedCaribe locations are reporting that they cannot log into the EHR system."

**Primary question:** "Your EHR is down and your vendor just told you they were hit by ransomware. What are your immediate priorities?"

**Follow-up probing questions:**
- What is your severity classification for this incident?
- What are the immediate clinical operations impacts? How do patients get treated today without EHR access?
- What questions do you need answers to from CloudMed? List them.
- Do you activate the full IR Plan for a vendor incident?
- Who needs to know about this internally right now?
- Do you have a backup of your patient data independent of CloudMed?

**Key points to listen for:**
- Classification as at minimum High, potentially Critical depending on answers from CloudMed
- Immediate focus on clinical operations continuity (paper-based fallback for appointments, prescriptions, and records)
- A list of critical questions for CloudMed: Was our data specifically accessed? What data was affected? What is the estimated restoration time? Do they have backups? Were backups also compromised?
- Recognition that MedCaribe has no independent backup of EHR data (this was identified as a critical gap in Projects 1 and 2)
- Notification to Medical Director, all Clinic Managers, and clinical staff about the EHR outage
- Starting an incident log

---

## INJECT 2: The Situation Gets Worse

**Read aloud:**

"It is now Monday at 2:00 PM. CloudMed sends an email update to all affected clients:

'Our investigation has determined that the threat actors gained access to our production database servers prior to deploying ransomware. Based on our preliminary analysis, data belonging to multiple clients was accessible to the attackers during the period of unauthorized access, which we believe occurred between Thursday evening and Saturday when the ransomware was deployed.

We are working with a third-party forensic investigation firm to determine the extent of data access. At this time, we cannot confirm whether data was exfiltrated (copied out of our environment) or only encrypted in place.

The CloudMed platform remains offline. We are working to restore from backups. Estimated restoration: 3-5 business days. Some data from the most recent 48 hours prior to the attack may not be recoverable.'

Your IT Administrator also points out that CloudMed hosts MedCaribe's data in a US-based data center. Under the Trinidad and Tobago Data Protection Act, this is a cross-border transfer of personal data to a jurisdiction that may not have comparable safeguards."

**Primary question:** "You now know the attackers had access to your patient database. You have no independent backup. And restoration is 3-5 days away. How do you manage this?"

**Follow-up probing questions:**
- What does "data belonging to multiple clients was accessible" mean for MedCaribe specifically? How many records are in the EHR?
- CloudMed says data from the last 48 hours may not be recoverable. What patient encounters happened during that window?
- Who is responsible for notifying the Information Commissioner, MedCaribe or CloudMed? Both?
- You are now 3-5 days without an EHR. What does clinical operations look like? Are there patient safety risks?
- What contractual obligations does CloudMed have to MedCaribe? Do you know? (This tests whether the vendor contract was ever reviewed for security clauses.)
- Does MedCaribe have cyber insurance that covers vendor-originated breaches?

**Key points to listen for:**
- Recognition that this is now a Critical severity incident
- Clinical continuity planning (paper records, manual appointment tracking, verbal prescription processes, patient safety assessment)
- Understanding that MedCaribe is the data controller under the DPA regardless of where CloudMed hosts the data or who caused the breach
- Realization that MedCaribe likely has no contractual security clauses with CloudMed (per POL-005 findings in Project 1)
- The cross-border data transfer issue (data in US data center, no verified comparable safeguards per DPA Section 6(l))
- Discussion about what to communicate to patients who have appointments this week
- Finance Manager assessing financial exposure (lost revenue from clinical disruption, potential regulatory fines, legal costs)

---

## INJECT 3: Confirmation of Data Exposure

**Read aloud:**

"It is Wednesday. CloudMed provides a further update:

'Our forensic investigation has confirmed that the threat actors exfiltrated approximately 2.3 terabytes of data from our production environment before deploying ransomware. This data includes client databases. We are working to determine which specific client records were included in the exfiltrated data.

For MedCaribe Health Group specifically, the database containing your patient records was hosted on one of the affected servers. We must assume that all data stored in your CloudMed instance was potentially compromised. Based on your account, this includes approximately 12,000 patient records spanning the past 5 years.

The threat actors have contacted CloudMed with a ransom demand. We have engaged law enforcement and are not negotiating.

Service restoration is now estimated at 5-7 business days from the original incident (so 2-4 more days from today).'

A local news outlet has published an article with the headline 'Caribbean Health Data Firm Hit by Ransomware, Patient Records at Risk.' MedCaribe is not named specifically, but staff are asking questions."

**Primary question:** "12,000 patient records are potentially compromised. The news media is covering the story. Walk me through the next 48 hours."

**Follow-up probing questions:**
- Is it time to notify the Information Commissioner? What do you tell them when you do not yet know exactly what was taken?
- Do you begin notifying patients now, or wait until CloudMed's investigation provides more detail?
- Staff and patients are seeing news coverage. What do you tell them?
- Do you have a communication plan for patients who call the clinic asking about the breach?
- The Medical Director has to brief the clinic managers. What key messages do they deliver?
- Should MedCaribe issue a public statement? Through what channel?
- What about corporate clients whose employees' occupational health data is in the system?

**Key points to listen for:**
- Information Commissioner notification (the combination of confirmed exfiltration plus 12,000 records makes this clearly reportable)
- Patient notification strategy (content, timing, channel, who drafts it, who approves it)
- Internal communication to staff (talking points for front desk staff handling patient inquiries)
- Corporate client notification for occupational health data
- Media response strategy (Medical Director as sole authorized spokesperson)
- Recognition that waiting for CloudMed's full investigation could take weeks; MedCaribe needs to act on what is known now
- Using the IR Plan communication templates from Project 1

---

## INJECT 4: Service Restoration and Ongoing Fallout

**Read aloud:**

"It is the following Monday, 9 days after the initial attack. CloudMed has restored service for MedCaribe's EHR instance. However:

- Patient records from the most recent 48 hours before the attack (Thursday afternoon through Saturday) are confirmed lost. This includes approximately 85 patient encounters, lab orders, and prescription changes.
- CloudMed's forensic report will not be finalized for another 4-6 weeks. They cannot yet confirm the specific records exfiltrated.
- Three patients have called MedCaribe after seeing the news coverage, asking if their data was affected. One patient is threatening legal action.
- The Information Commissioner's office has acknowledged MedCaribe's notification and requested a detailed written report within 30 days.
- CloudMed has offered affected clients 12 months of credit monitoring for their patients, but the enrollment process requires MedCaribe to provide patient contact details to a third-party monitoring service."

**Primary question:** "You are back online but the aftermath is just beginning. What are your priorities for the next 30 days?"

**Follow-up probing questions:**
- 85 patient encounters are lost. How do you reconstruct that clinical data? Who is responsible?
- The patient threatening legal action: how do you handle it? Who responds?
- CloudMed is offering credit monitoring but it requires sharing patient data with another third party. Under the DPA, can you do that without patient consent?
- How do you prepare the written report for the Information Commissioner within 30 days?
- What does MedCaribe's relationship with CloudMed look like going forward? Do you stay with them?
- What contractual changes would you demand before renewing the CloudMed contract?

**Key points to listen for:**
- Clinical data reconstruction process (contacting patients with appointments during the lost window, working from paper records if any were created during the outage)
- Legal response to the patient threat (do not engage directly; route through legal counsel)
- DPA analysis on sharing data with the credit monitoring service (legitimate interest vs. consent)
- Structured 30-day report preparation for the Information Commissioner
- Vendor contract review: demanding breach notification SLA, backup verification, audit rights, data residency terms
- Evaluation of whether to remain with CloudMed or migrate to another provider
- Discussion about implementing an independent backup of EHR data going forward

---

## INJECT 5: Post-Incident Review

**Read aloud:**

"The post-incident review has been scheduled. Looking at this incident from start to finish, the following systemic issues contributed to MedCaribe's exposure:

1. MedCaribe had never reviewed CloudMed's security practices, certifications, or backup procedures
2. The vendor contract did not include security clauses, breach notification timelines, or audit rights
3. MedCaribe had no independent backup of EHR data
4. No cross-border data transfer assessment had been conducted per the DPA
5. No business continuity plan existed for EHR unavailability
6. Staff had no training on paper-based fallback procedures
7. No pre-drafted communication templates existed for vendor-related breaches (the IR Plan templates were focused on internal incidents)"

**Primary question:** "What are your top 5 recommendations coming out of this review, in priority order?"

**Follow-up probing questions:**
- Which of these failures were already identified in the risk register from Project 1?
- What would have been different if the Vendor Risk Policy (POL-005) had been fully implemented before this incident?
- How do you prioritize independent EHR backup versus vendor contract renegotiation?
- Should MedCaribe have a formal business continuity plan in addition to the IR Plan?
- How does this incident change the scores in the risk register?

**Key points to listen for:**
- Independent EHR backup as the top priority (this is the single change that would have reduced the impact most significantly)
- Vendor contract renegotiation with security clauses from POL-005
- Cross-border transfer compliance (DPA Section 6(l) assessment for all vendors)
- Business continuity plan for critical system outages (paper-based clinical procedures, manual scheduling)
- Vendor-specific communication templates added to the IR Plan
- Connection to existing risk register items (RISK-006, RISK-009, RISK-019 all validated by this scenario)
- Recognition that vendor risk management is not a one-time assessment but an ongoing process

---

## Exercise Outcomes Checklist

| Capability | Demonstrated? | Notes |
|-----------|---------------|-------|
| Activated IR Plan for a vendor-originated incident | Yes / No / Partial | |
| Prioritized clinical operations continuity | Yes / No / Partial | |
| Asked the right questions to the vendor immediately | Yes / No / Partial | |
| Recognized data controller responsibility under DPA | Yes / No / Partial | |
| Notified Information Commissioner appropriately | Yes / No / Partial | |
| Developed patient communication plan | Yes / No / Partial | |
| Managed internal and media communications | Yes / No / Partial | |
| Identified contractual gaps with the vendor | Yes / No / Partial | |
| Addressed clinical data loss and reconstruction | Yes / No / Partial | |
| Proposed systemic improvements | Yes / No / Partial | |
| Connected findings to existing risk register | Yes / No / Partial | |

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | April 2026 | J. Maitland | Initial scenario |

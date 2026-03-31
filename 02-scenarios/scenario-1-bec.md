# Scenario 1: Business Email Compromise

**Classification:** Exercise Material / Facilitator Only  
**Scenario Code:** TTX-MC-001  
**Duration:** 75-90 minutes  
**Difficulty:** Introductory (recommended as first exercise)  
**Threat Vector:** External, financially motivated  
**MedCaribe Risks Tested:** RISK-001 (BEC, Score 20), RISK-005 (Phishing, Score 15), RISK-015 (Shared Credentials, Score 12)

---

## Scenario Overview

**For facilitator eyes only. Do not distribute to participants before the exercise.**

A billing staff member at MedCaribe's San Fernando office receives a phishing email disguised as a password reset notification from the insurance claims portal. The staff member enters their M365 credentials on a convincing fake login page. The attacker uses the compromised account to send fraudulent payment redirect emails to Sagicor and Guardian Life, attempting to divert insurance reimbursement payments to an external bank account. The attack is discovered when a legitimate payment fails to arrive.

This scenario unfolds over five injects, escalating from initial compromise through financial impact and regulatory consideration.

---

## Participants Required

| Role | Who at MedCaribe | Exercise Role |
|------|-----------------|---------------|
| Incident Coordinator | K. Rampersad (Operations Manager) | Leads the response |
| Technical Lead | M. Doyle (IT Administrator) | Investigates and contains |
| Decision Authority | Dr. A. Dorian (Medical Director) | Approves external notifications |
| Finance/Billing Representative | S. Mohammed or billing staff member | Provides billing context |
| Observer | Facilitator or designated observer | Tracks observations |

---

## INJECT 1: The Phishing Email

**Read aloud to participants:**

"It is Tuesday morning at 9:15 AM. A billing staff member at the San Fernando office reports to the IT Administrator that they received an email this morning at approximately 8:30 AM that appeared to come from the Sagicor insurance claims portal. The email said their portal password had expired and they needed to reset it immediately. The staff member clicked the link and entered their M365 email address and password on what looked like a normal login page. They are now reporting it because 'the page looked a bit different after they logged in' and they feel uneasy about it."

**Primary question:** "What are the first three things you do right now?"

**Follow-up probing questions:**
- Who specifically takes ownership of this report?
- Do you classify this as an event or an incident at this point? What severity?
- What containment actions do you take on the staff member's account, and do you need approval to take them?
- Do you tell the staff member to keep working on their computer or stop?
- How do you determine if the credentials were actually harvested (versus a false alarm)?

**Key points the facilitator should listen for:**
- Immediate account action (disable, force sign-out, password reset)
- Starting an incident log
- Checking if MFA was enabled on the account (it was not, per MedCaribe's current partial MFA state)
- Recognizing this as at minimum a Medium severity incident, likely High
- Referencing the pre-authorized containment actions from the Escalation Decision Tree

---

## INJECT 2: The Account Was Compromised

**Read aloud:**

"The IT Administrator reviews the M365 sign-in logs for the billing staff member's account. The logs show a successful sign-in at 8:32 AM from the staff member's usual IP address (the phishing page captured the credentials and replayed them). However, there is also a sign-in at 8:47 AM from an IP address geolocated to Lagos, Nigeria. Between 8:47 AM and 9:10 AM (when the staff member reported the issue), the attacker appears to have been active in the account. The IT Administrator also notices that a new inbox rule was created during that window: all emails containing the words 'payment', 'bank', 'account', or 'transfer' are being automatically moved to a hidden folder called 'RSS Feeds'."

**Primary question:** "The account is confirmed compromised. Walk me through your next steps in order."

**Follow-up probing questions:**
- Have you disabled the account yet? If not, why not?
- The attacker created a mailbox rule. What does that tell you about their intent?
- What else do you check in the account besides sign-in logs? (Sent items, deleted items, forwarding rules, OAuth app consents)
- Do you need to notify anyone else at this point? Who?
- What severity level is this now?
- Should you check other staff members' accounts? Why or why not?

**Key points to listen for:**
- Account disabled or password reset with session revocation
- Removal of the malicious inbox rule
- Checking sent items for fraudulent emails
- Escalation to Incident Coordinator
- Recognition that the attacker was looking for payment-related emails (financial fraud motive)
- Decision to check other billing staff accounts (especially if they share insurance portal credentials, per RISK-015)

---

## INJECT 3: Fraudulent Emails Were Sent

**Read aloud:**

"Review of the sent items folder reveals that between 8:50 AM and 9:05 AM, the attacker sent three emails from the billing staff member's account:

1. To Sagicor claims department: 'Please update our payment details for MedCaribe Health Group. Our new bank account for reimbursements is [external account details]. Please apply this to all pending claims.'

2. To Guardian Life claims department: Same message with the same external bank details.

3. To a MedCaribe billing colleague: 'Hey, Sagicor asked us to verify our bank details. Can you send me our current account number and routing info?'

The attacker also deleted these emails from the sent folder, but they are recoverable from the deleted items retention. The billing colleague has not yet responded to email #3."

**Primary question:** "You now have confirmed financial fraud in progress. What do you do?"

**Follow-up probing questions:**
- Who needs to be notified right now? In what order?
- Do you contact Sagicor and Guardian Life? Who makes that call? What do you tell them?
- The billing colleague received a social engineering email from a trusted internal address. How do you handle that?
- Is this a data breach under the Data Protection Act? What patient data, if any, was exposed?
- Do you notify law enforcement? Who authorizes that decision?
- What is the severity level now?

**Key points to listen for:**
- Immediate notification to Finance Manager and Medical Director
- Contact to Sagicor and Guardian Life to warn them about the fraudulent bank change request (this is time-sensitive since the payments could be redirected)
- Recognition that this is now a Critical severity incident
- Alerting the billing colleague not to respond to email #3
- Checking whether any patient data was accessible or forwarded (the inbox rule was targeting payment emails, but the entire mailbox was accessible)
- Decision on law enforcement (TTPS Cyber Crime Unit) with Medical Director approval
- Starting to assess whether patient insurance data in the mailbox constitutes a data breach

---

## INJECT 4: Patient Data Was in the Mailbox

**Read aloud:**

"Further investigation reveals that the compromised mailbox contained approximately 340 insurance claim emails from the past 6 months. These emails include patient names, dates of birth, insurance policy numbers, diagnosis codes, and claim amounts. While there is no evidence the attacker specifically accessed or downloaded these emails (the mailbox rule targeted payment-related keywords), the attacker had full access to the mailbox for approximately 23 minutes and could have viewed or copied any of this data.

Additionally, the Finance Manager confirms that Sagicor processes payment changes within 48-72 hours. The fraudulent bank change request was sent approximately 45 minutes ago."

**Primary question:** "You have potential exposure of 340 patients' personal and medical data, and a financial fraud clock ticking. How do you prioritize?"

**Follow-up probing questions:**
- Is this now a reportable data breach under the Data Protection Act? Who makes that determination?
- What is the threshold for notifying the Information Commissioner? Do you meet it?
- Do you notify the 340 patients? When? How? Who drafts that communication?
- The Sagicor payment change is still processing. What is the most urgent action right now?
- How do you preserve evidence for potential law enforcement investigation while also containing the incident?
- What does the IR Plan say about the Medical Director's role at this point?

**Key points to listen for:**
- Financial containment is the most time-critical action (call Sagicor and Guardian Life before the bank change processes)
- Data breach assessment using the criteria from the IR Plan (data type, number affected, potential harm)
- Recognition that even without proof of exfiltration, the attacker's access to the data may trigger DPA notification obligations
- Medical Director taking the lead on external notification decisions
- Evidence preservation (do not delete the attacker's mailbox rule, sign-in logs, or recovered sent items)
- Communication template from the IR Plan being referenced for patient notification

---

## INJECT 5: Wrapping Up and Recovery

**Read aloud:**

"It is now 48 hours after the initial compromise. Here is the current status:

- The compromised account has been secured (disabled, password reset, MFA now enabled, malicious rules removed)
- Sagicor was contacted within 2 hours and confirmed they flagged the bank change request before processing. No funds were diverted.
- Guardian Life was contacted within 3 hours. They had already begun processing the change. They are now reversing it, but confirmation will take 5 business days.
- The TTPS Cyber Crime Unit has been notified and provided with the sign-in logs and email evidence.
- A preliminary assessment indicates 340 patient records were potentially exposed.
- No evidence of actual data exfiltration has been found, but it cannot be ruled out.
- Three other billing staff members have been checked. No other compromises found.
- MFA has been enabled for all billing staff accounts as an emergency measure."

**Primary question:** "The immediate crisis is managed. What happens now over the next 14 days?"

**Follow-up probing questions:**
- Do you notify the Information Commissioner? What information do you provide?
- Do you notify the 340 patients? What do you tell them?
- What goes into the post-incident review?
- What changes to the security program would you recommend based on this incident?
- How do you update the risk register?
- If you could go back to 8:30 AM on Tuesday, what single control would have prevented this entire incident?

**Key points to listen for:**
- Post-incident review scheduled within 14 days (per IR Policy)
- Regulatory notification decision with supporting justification
- Patient notification drafted using the communication template from the IR Plan
- Recommendations for systemic improvements (MFA for all accounts, security awareness training, elimination of shared insurance portal credentials, anti-phishing policies)
- Recognition that MFA would have blocked the attacker's credential replay entirely
- Risk register update: RISK-001 score may change if MFA is now enforced; new finding about insurance portal shared credentials may increase RISK-015

---

## Exercise Outcomes Checklist

After the exercise, the facilitator should assess whether participants demonstrated:

| Capability | Demonstrated? | Notes |
|-----------|---------------|-------|
| Recognized the phishing report as a potential incident | Yes / No / Partial | |
| Took immediate containment action on the account | Yes / No / Partial | |
| Started an incident log | Yes / No / Partial | |
| Classified severity correctly (escalating as new info emerged) | Yes / No / Partial | |
| Referenced the IR Plan or Escalation Decision Tree | Yes / No / Partial | |
| Identified the financial fraud risk and prioritized accordingly | Yes / No / Partial | |
| Contacted insurance companies in a timely manner | Yes / No / Partial | |
| Assessed data breach implications under the DPA | Yes / No / Partial | |
| Involved the Medical Director for external notification decisions | Yes / No / Partial | |
| Discussed evidence preservation | Yes / No / Partial | |
| Identified the root cause (no MFA, phishing susceptibility) | Yes / No / Partial | |
| Proposed specific improvements for post-incident remediation | Yes / No / Partial | |

---

## Document Control

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | April 2026 | J. Maitland | Initial scenario |

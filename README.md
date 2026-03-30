# Tabletop Exercise Kit for MedCaribe Health Group

## Incident Response Exercises for a Caribbean Healthcare Provider

**Scenarios:** Business Email Compromise, Insider Threat, Third-Party Vendor Breach  
**Context:** MedCaribe Health Group, 55-person private healthcare provider, Trinidad and Tobago  
**Author:** Jelani D. Maitland  
**Date:** April 2026  
**Related Projects:**  
- [Project 1: MedCaribe Security Program](https://github.com/jelanidm/medcaribe-security-program)  
- [Project 2: CIS Controls v8 IG1 to M365 Mapping](https://github.com/jelanidm/m365-cis-controls-mapping)

---

## Overview

This repository contains a complete tabletop exercise kit designed to test MedCaribe Health Group's incident response capabilities. It includes three realistic scenarios, a facilitator guide, participant materials, observer worksheets, and an after-action report template.

Tabletop exercises are discussion-based walkthroughs of simulated incident scenarios. No systems are touched. The goal is to test whether the people, processes, and decision-making structures documented in the incident response plan actually work under pressure.

This kit is the natural follow-up to Project 1, which built the governance program, and Project 2, which mapped technical controls. Project 3 answers: "We have the plan and the controls. Will our team actually execute them when it matters?"

---

## Why Three Scenarios?

Each scenario tests a different threat vector and exercises different parts of the incident response plan:

**Scenario 1: Business Email Compromise (BEC)**  
Tests detection of a compromised account, containment decisions, financial fraud response, and external communication with insurance companies. Exercises the team's ability to handle MedCaribe's #1 rated risk (RISK-001, Score: 20/25).

**Scenario 2: Insider Threat (Data Exfiltration)**  
Tests detection of unauthorized data access, handling of a situation involving a current employee, evidence preservation, HR coordination, and regulatory notification decisions under the Data Protection Act.

**Scenario 3: Third-Party Vendor Breach**  
Tests response to an incident originating outside MedCaribe's control, vendor communication, patient data impact assessment, regulatory notification, and the limits of MedCaribe's ability to investigate a vendor's environment.

---

## How to Use This Kit

**If you are running an exercise for the first time:** Start with the Facilitator Guide. It walks through everything from planning to post-exercise reporting. Then pick one scenario (BEC is recommended as the first exercise since it is the most common real-world threat).

**If you are an experienced facilitator:** Go directly to the scenario documents. Each one is self-contained with injects, discussion prompts, and timing guidance.

**If you are studying GRC or incident response:** Read through all three scenarios to understand how different incident types require different response decisions. Pay attention to the decision points where the scenario branches based on participant choices.

---

## Repository Structure

```
tabletop-exercise-kit/
├── README.md
├── 01-facilitator-guide/
│   └── facilitator-guide.md              # Complete guide to planning and running exercises
├── 02-scenarios/
│   ├── scenario-1-bec.md                 # Business Email Compromise targeting billing
│   ├── scenario-2-insider-threat.md      # Employee exfiltrating patient data
│   └── scenario-3-vendor-breach.md       # EHR vendor breach exposing records
├── 03-participant-materials/
│   ├── participant-handout.md            # Roles, ground rules, IR plan reference
│   └── exercise-roster-template.md       # Attendance and role assignment
├── 04-observation-and-reporting/
│   ├── observer-worksheet.md             # Real-time tracking during exercise
│   └── after-action-report-template.md   # Post-exercise findings document
└── pdf-versions/
    └── (all documents exported as PDF)
```

---

## Connection to the MedCaribe Portfolio

This exercise kit is designed to test the incident response plan, policies, and escalation procedures created in Project 1. Specifically:

- Scenarios reference the IR Plan roles (Incident Coordinator, Technical Lead, Decision Authority)
- Decision points test the pre-authorized containment actions from the Escalation Decision Tree
- Regulatory notification decisions test understanding of the Data Protection Act obligations
- After-action findings feed back into the Risk Register for score updates

---

## About the Author

Jelani D. Maitland is a cybersecurity professional based in Trinidad and Tobago, holding CySA+, Security+, SC-200, and Fortinet FCA certifications. He specializes in security operations, governance, and risk management for small and midsize organizations in the Caribbean.

- [LinkedIn](https://linkedin.com/in/jelanidm)
- [GitHub](https://github.com/jelanidm)

---

## License

This project is shared under the [MIT License](LICENSE). You are free to use, modify, and distribute these materials with attribution.

# Post-mortem: CampusPay wallet (2025)

## 1. Timeline and sources

| # | When | Event | Source |
|---|------|-------|--------|
| 1 | Month 1 (Week 1) | University Head of Finance requests an internal cashless mobile payment app for canteen purchases and library fines within one semester; lead developer assumes PM role without a charter. | Fictional case from Lab-01 |
| 2 | Month 2 (Week 5) | Lead developer runs an open student survey; scope rapidly expands to include campus bus ticketing and parking permits without sponsor approval, cost recalculation, or schedule impact analysis. | Fictional case from Lab-01 |
| 3 | Month 3 (Week 9) | Team focuses entirely on mobile user interface design and client features; hardware integration with actual campus card terminals and physical point-of-sale (POS) systems is postponed. | Fictional case from Lab-01 |
| 4 | Month 4 (Week 13) | Project status reported as "on schedule" based solely on visual code progress; no end-to-end integration testing or simulated load testing is performed with real POS hardware or campus Wi-Fi. | Fictional case from Lab-01 |
| 5 | Month 4 (Week 16) | CampusPay launches on the first day of the academic semester; live card terminals reject 40% of payment transactions due to timeout errors and API mismatches; canteen lines double. | Fictional case from Lab-01 |
| 6 | Day 3 Post-Launch | Severe student and faculty backlash erupts amid massive canteen disruption; university leadership officially halts and withdraws the mobile application. | Fictional case from Lab-01 |
| 7 | Month 9 (+5 months) | CampusPay relaunches after comprehensive terminal hardware integration, load testing, and operational staff training, strictly de-scoped to canteen payments only. | Fictional case from Lab-01 |

## 2. Classification and organisation

- **Project vs. Programme:** The initiative was mistakenly treated as a single, loosely bounded software project. Given the disparate technical and operational domains (canteen retail POS, library fines, municipal transport bus ticketing, and municipal parking barriers), it should have been structured either as an overarching **programme** coordinating separate sub-projects or strictly constrained to a single standalone project focused purely on canteen point-of-sale.
- **Organisational Structure & PM Authority:** The project operated within a rigid **Functional organisation**. The lead developer was assigned project management duties without any formal project authority, having zero power to reject scope additions, zero mandate to secure dedicated testing equipment, and no direct reporting line to university decision-makers.
- **Sponsor, Charter, and PMO:** The project lacked a genuine sponsor; the Head of Finance acted as a "ghost sponsor" who initiated the request via email but never attended reviews or committed dedicated funding. No formal **project charter** was ever drafted or signed to define scope, objectives, or governance boundaries. No **PMO (Project Management Office)** or institutional oversight existed to monitor progress, challenge assumptions, or conduct independent stage-gate reviews.

## 3. Success criteria

- **Stated Success Criteria:** The sole stated criterion was an arbitrary calendar launch date ("launch in September").
- **Missing Measurable Criteria:**
  - Technical reliability: Transaction success rate >= 99.5% under peak transaction loads.
  - Performance latency: Payment authorization and receipt generation turnaround time <= 2.0 seconds.
  - Capacity: Concurrency support for at least 50 simultaneous point-of-sale terminals without API throttling or packet drops.
  - Quality assurance: 100% pass rate on end-to-end integration test suites across all physical card terminal firmware versions.
- **Ignored Success Dimensions:**
  - **Benefits realization:** Whether the system actually reduced student transaction time and administrative processing costs compared to cash.
  - **User experience & satisfaction:** The severe frustration caused to hungry students and hurried faculty when payment attempts failed repeatedly.
  - **Operational readiness:** Canteen cashiers received zero operational training, no manual transaction fallback procedures, and no helpdesk escalation path for failed transactions.
  - **Team health:** Student developers experienced severe burnout trying to deliver an uncontrolled feature list without adequate resources.

## 4. Process groups and knowledge areas

| Process group | What went wrong or was skipped |
|---------------|--------------------------------|
| Initiating | No formal project charter was established, the business case was unquantified, and the nominal sponsor never formally committed to executive oversight. |
| Planning | Scope was never decomposed or baselined, schedule lacked dependency and critical path analysis, and quality and risk management planning were completely omitted. |
| Executing | Development took place in an isolated software silo, ignoring hardware dependencies and bypassing realistic system integration with campus point-of-sale terminals. |
| Monitoring and controlling | Progress was tracked superficially through lines of code and visual UI screens rather than verified working software increments (the classic "invisibility trap"). |
| Closing | The initial deployment bypassed formal user acceptance testing (UAT) and operational sign-off, resulting in catastrophic operational failure and forced withdrawal. |

### Knowledge areas most responsible

1. **Project Scope Management:** Total failure of scope baseline control; the team permitted uncontrolled scope creep (adding bus tickets and parking) without formal change requests, sponsor authorization, or schedule/budget impact evaluations.
2. **Project Quality Management:** Complete absence of quality assurance and verification standards; the application was deployed to production without a single end-to-end integration test against physical hardware or load testing under real network conditions.
3. **Project Stakeholder Management:** Complete neglect of key operational and governance stakeholders; canteen cashiers, terminal vendors, and university network administrators were never engaged until after the system failed in live production.

## 5. Ethics

- **Decision Examined:** The project leadership's decision to deploy the CampusPay mobile application into live production on opening day despite being fully aware that no end-to-end integration testing had ever been performed with physical campus card terminals.
- **Responsibility:** Project leadership failed the standard of responsibility by taking an uncalculated operational gamble with institutional infrastructure and abdicating ownership of the resulting retail breakdown and financial inconvenience to students.
- **Respect:** Leadership demonstrated disrespect toward students, instructors, and campus canteen staff by treating them as unwitting, non-consenting beta testers during peak lunch hours without prior notice or operational contingency plans.
- **Fairness:** The decision was deeply unfair to front-line canteen workers, who were forced to endure intense customer hostility, manual reconciliations, and doubled queues while bearing zero responsibility for the technical defects.
- **Honesty:** Leadership violated the duty of honesty by reporting project status as "on schedule" to university leadership, thereby actively concealing critical integration deficits, incomplete testing, and catastrophic launch risks.

## 6. What our project will do differently

| # | Commitment (We will ...) | Measured by | By week | Charter line |
|---|--------------------------|-------------|---------|--------------|
| 1 | We will maintain a signed project charter with a named, engaged sponsor who formally attends and signs off on the Week 7 MVP and Week 13 pilot stage gates. | Signed charter document and recorded minutes of stage-gate attendance | Week 1 & Weeks 7, 13 | Section 10 Approval & Section 9 Authority |
| 2 | We will strictly lock project scope to Must features until the MVP demo is fully accepted, rejecting all Could/stretch feature additions. | Zero approved change requests for non-Must features prior to MVP milestone sign-off | Week 7 | Section 3 High-level scope & Objective O1 |
| 3 | We will execute a realistic simulated load test of 100 concurrent students and verify SockJS fallback over campus Wi-Fi before authorizing live classroom deployment. | Formal load test benchmark report with broadcast latency <= 500 ms and 0 server crashes | Week 12 | Objective O3, Objective O4, & Milestone Week 12 |
| 4 | We will enforce continuous automated testing with a minimum 80% line coverage threshold required for every merged pull request in CI. | Automated CI pipeline coverage reports maintaining >= 80% line coverage on all merged commits | Weeks 4 to 14 | Objective O5 & Milestone Week 3 |
| 5 | We will secure formal data privacy compliance approval and deliver a verified operational runbook to IT Operations prior to live student participation. | Signed Data Protection Officer compliance memo and signed IT Operations runbook handover | Week 13 | Section 7 Constraints, Milestone Week 14, & Section 9 Authority |


# Project charter: Realtime Quiz platform

| Field    | Value                                    |
|----------|------------------------------------------|
| Version  | 1.0 (draft for sponsor approval)         |
| Date     | 2026-09-29                               |
| Sponsor  | Head of the IT department                |
| PM       | Supervising lecturer                     |

## 1. Purpose and justification

Instructors across the IT department currently spend excessive hours manually administering and marking paper-based quizzes without the ability to provide instant learning feedback during lectures. The Realtime Quiz platform solves this problem by providing an interactive web application where instructors create multiple-choice quizzes and host live sessions while students join via a 6-character room code to answer questions against a countdown timer. Instant WebSocket broadcasts calculate scores and refresh a live leaderboard immediately, significantly boosting student engagement and eliminating manual grading overhead. As detailed in `business-case.md`, building this solution in-house eliminates ongoing commercial SaaS licensing fees, preserves departmental data sovereignty on campus infrastructure, and yields a full economic payback within 1.1 academic years.

## 2. Objectives and success criteria

| #  | Objective (what will be true) | Success criterion (number + week) |
|----|-------------------------------|-----------------------------------|
| O1 | Core interactive quiz MVP features developed and validated | 100% of Must features working with 0 blocking defects demonstrated live, week 7 |
| O2 | Live classroom pilot conducted successfully under real teaching conditions | 50 concurrent student participants completing a live quiz session with 0 server crashes, week 14 |
| O3 | Low-latency real-time broadcasting achieved across connected client devices | Broadcast latency <= 500 ms at the 95th percentile and timer drift <= 200 ms, measured week 14 |
| O4 | High concurrent capacity and system efficiency sustained on departmental hardware | 20 concurrent sessions of 100 participants served on 2 vCPU and 2 GB RAM with 0 unhandled exceptions, verified week 12 |
| O5 | High code quality and automated verification maintained throughout development | Automated unit and integration line coverage >= 80% with green CI pipeline on every merge, maintained from week 4 to week 14 |

## 3. High-level scope

In scope:
- Multiple-choice quiz authoring and question editor interface (Must)
- Real-time session lobby and 6-character PIN access code joining module (Must)
- Authoritative server question timer and answer submission engine (Must)
- Automated scoring engine, instant question feedback, and dynamic live leaderboard (Must)
- User authentication, session management, and role-based access control (Must)
- Instructor analytics dashboard with quiz summary statistics and CSV/PDF export (Should)
- Responsive mobile and desktop browser user interface with WCAG AA accessibility compliance (Should)

Out of scope:
- Native mobile applications for iOS or Android platforms (web browser access only)
- Non-multiple-choice question formats such as free text, subjective essays, or automated code grading
- Integrated video and audio conferencing streaming capabilities
- Learning Management System (LMS) integrations such as Moodle LTI or Canvas REST APIs
- Multi-node distributed clustering, Redis registries, and horizontal cloud autoscaling infrastructure

## 4. Milestones

| Week | Milestone | Ends process group |
|------|-----------|--------------------|
| 1    | Project charter approved, core team formed, initial environment ready | Initiating |
| 3    | PM plan baselined, user accounts and security architecture established | Planning |
| 5    | Quiz authoring module and question bank management completed | Executing |
| 7    | Live session core completed and MVP demo delivered to sponsor | Executing |
| 10   | Instructor analytics, reporting dashboard, and CSV/PDF export completed | Executing |
| 12   | System hardening, accessibility audit, and 100-user load test verified | Executing |
| 14   | Pilot session with 50 students completed, final handover and project closure | Closing |

## 5. Budget summary

Effort:  students 4 x 14 x 8 h = 448 h; PM 14 x 3 h = 42 h; total 490 h  
Cash:    hosting 4 months x 25 USD = 100 USD; domain registration = 15 USD; testing & build tools = 60 USD; contingency reserve = 25 USD (14 % of base cash expenses); total 200 USD

## 6. Assumptions

- Student team members commit and sustain an average of 8 productive hours per week each across the full 14-week duration.
- The university campus network firewall and proxy permit persistent WebSocket connections without dropping frames or protocol blocking.
- Target end users (instructors and students) access the application via modern standard web browsers (latest two versions of Chrome, Firefox, Safari, or Edge).
- Development machines, local IDEs, and workstation environments are provided by students and faculty at zero additional cost to the project budget.

## 7. Constraints

- Fixed project schedule constraint of strictly 14 weeks commencing on 2026-09-29 and concluding by 2027-01-05.
- Fixed financial spending cap of 200 USD total cash budget for hosting, domain registration, and tooling expenses.
- Single-node virtual server constraint: production deployment must run entirely within Docker Compose on one Linode VPS (2 vCPU, 2 GB RAM) hosted at gicitc.com.
- Institutional data privacy constraint: all student identities, quiz questions, and evaluation records must remain stored on campus-controlled infrastructure.

## 8. High-level risks

- Campus proxy and institutional firewalls may block or terminate raw WebSocket connections (Mitigation: implement SockJS fallback with HTTP long-polling).
- Cutting-edge framework versions (Spring Boot 4 and Spring Security 7) may exhibit unexpected API breaking changes or lack community tutorials (Mitigation: create an early proof-of-concept during Week 2).
- Client-side system clock drift against the authoritative server timer may trigger race conditions on late answer submissions (Mitigation: enforce authoritative server-side timestamps and clock synchronization offset headers).

## 9. Project manager authority

The Project Manager is authorized to decide independently on:
- Internal team task allocations, sprint task priorities, and day-to-day technical implementation choices.
- Schedule adjustments and resource rebalancing within the baselined 490 total person-hours.
- Operational expenditures within the approved 200 USD cash ceiling, including allocation of the 25 USD contingency reserve.

The Project Manager must seek formal written approval from the Sponsor for:
- Any modification to baseline project scope (adding Could features or altering Must deliverables).
- Any rescheduling of core gate dates, specifically the Week 7 MVP demonstration or Week 14 student pilot.
- Any budget expansion beyond the 200 USD cash cap.
- Formal sign-off on phase gate transitions and project closure.

## 10. Approval

Sponsor: _________________________  Date: ____________  
PM:      _________________________  Date: ____________  


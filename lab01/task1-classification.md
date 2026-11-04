# Task 1: project, operation or programme?

| #  | Initiative | Temporary? | Unique? | Coordinated? | Class | Justification |
|----|------------|------------|---------|--------------|-------|---------------|
| 1  | Build the Realtime Quiz platform and pilot it with 50 students in week 14 | yes | yes | no | Project | Temporary effort with a defined end date (week 14) delivering a unique new software application. |
| 2  | Run the nightly backup of the gicitc.com PostgreSQL database | no | no | no | Operation | Repeats every night with the same output and no end date as part of ongoing infrastructure maintenance. |
| 3  | Move the department's three web servers to a new Linode region before 15 December | yes | yes | no | Project | Temporary undertaking with a firm deadline (15 December) achieving a unique one-off infrastructure migration. |
| 4  | Answer helpdesk tickets within the 4-hour service level | no | no | no | Operation | Continuous, ongoing support service with no end date despite the 4-hour turnaround SLA per ticket. |
| 5  | "Digital classroom": Realtime Quiz, LMS upgrade and lecture capture sharing one login and one grade export | yes | yes | yes | Programme | Coordinates three related projects to deliver combined strategic benefits (single sign-on and unified grade export) that none delivers alone. |
| 6  | Apply the monthly security patches to the VPS | no | no | no | Operation | Recurring, cyclical operational task carried out every month without a defined finish date. |
| 7  | Add multi-node scaling (RabbitMQ relay, Redis registry) to Realtime Quiz next semester | yes | yes | no | Project | Temporary development effort with a defined timeframe (next semester) to deliver a unique architectural upgrade. |
| 8  | Operate the Realtime Quiz platform after go-live: password resets, restarts, monitoring | no | no | no | Operation | Repetitive, ongoing day-to-day administration and maintenance of the live system with no end date. |
| 9  | Write and publish the department's annual IT report for the dean by 31 January | yes | yes | no | Project | Temporary activity with a fixed deadline (31 January) producing a unique document specific to that year's performance. |
| 10 | Replace 40 wireless access points in two buildings during the summer break | yes | yes | no | Project | Temporary initiative constrained by the summer break delivering a unique physical hardware replacement. |

## Grey zones

1. **Initiative 7 (Add multi-node scaling next semester):** This initiative could be classified either as a distinct **Project** or as ongoing software maintenance within **Operations**. What would settle it is whether the sponsor formally authorises it with dedicated capital funding, a distinct charter, and a temporary team allocation (making it a Project), or whether it is assigned to operational maintenance staff as routine backlog tickets under an existing operational budget (making it an Operation).
2. **Initiative 9 (Write and publish the annual IT report by 31 January):** This initiative could be classified as a recurring **Operation** due to its predictable annual cycle, or as a small annual **Project** due to its discrete deadline and unique annual content. What would settle it is how the department governs the work: if it requires a distinct project charter, unique cross-functional analysis, and temporary resource booking, it is a Project; if it is explicitly written into an administrative officer's recurring job description with standardized recurring templates and no separate budget, it is an Operation.

## What our project hands over

At go-live in week 14, the Realtime Quiz project formally hands over system custody to the departmental IT operations team (the VPS administrator and support staff). The operations team will assume responsibility for ongoing operational maintenance (Initiative 8), including server monitoring, PostgreSQL database backups, monthly VPS security patches, container restarts, and user credential management. To ensure a seamless operational transition without surprises, the project team will deliver an operational runbook, a production deployment checklist, the finalized `docker-compose.prod.yml` configuration, and administrative handover documentation two weeks prior to the pilot.

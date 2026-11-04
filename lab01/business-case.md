# Business case: live quizzes for the IT department

## 1. Problem

Instructors across the IT department face substantial recurring administrative drag from preparing, printing, administering, and manually marking paper-based quizzes. Furthermore, students receive test results days or weeks late, missing critical opportunities for immediate formative feedback during lectures. This grading overhead directly diverts academic staff hours away from student mentoring, research, and curriculum improvement.

Assumptions:
- Lecturers running weekly quizzes: 10 instructors
- Marking time per lecturer per week: 1 hour
- Teaching weeks per academic year: 30 weeks (two 15-week semesters)
- Total annual marking effort: 10 lecturers x 1 h/week x 30 weeks = 300 hours/year
- Notional economic value of one hour: 10 USD (used for standardized economic comparison, recognizing student and instructor effort value)
- Total baseline annual marking cost: 300 hours x 10 USD/h = 3,000 USD/year

## 2. Options

| Option | Description | One-off cost | Annual cost | Annual benefit |
|--------|-------------|--------------|-------------|----------------|
| A | Do nothing (status quo paper quizzes and manual grading) | 0 USD | 0 USD | 0 USD |
| B | Buy commercial SaaS (e.g. Kahoot! EDU Pro / Mentimeter Campus subscription) | 0 USD | 1,800 USD | 3,000 USD |
| C | Build Realtime Quiz in-house (capstone student team and departmental VPS) | 4,900 USD | 300 USD | 4,800 USD |

*Note on Option B pricing:* Based on standard commercial education pricing (cited from Kahoot! EDU higher education pricing page at https://kahoot.com/schools/higher-ed/pricing/, accessed October 2026, baseline tier assumed at 15 USD per instructor per month billed annually: 10 lecturers x 15 USD x 12 months = 1,800 USD/year).

*Note on Option C costs & benefits:*
- One-off cost: 490 person-hours of effort (4 students x 14 wks x 8 h = 448 h + PM 14 wks x 3 h = 42 h) valued notionally at 10 USD/h = 4,900 USD. (Actual cash budget cap is 200 USD).
- Annual cost: Linode VPS hosting at gicitc.com: 12 months x 25 USD = 300 USD/year.
- Annual benefit: 3,000 USD marking time saved + 1,800 USD commercial SaaS subscription fees avoided = 4,800 USD/year.

## 3. Comparison

| Option | Net annual benefit | Payback (years) | Sensitivity (6 lecturers) |
|--------|--------------------|-----------------|----------------------------|
| B | 3,000 - 1,800 = 1,200 USD | 0.0 years (immediate, no one-off capital investment) | Net benefit: 1,800 - 1,080 = 720 USD (Payback: 0.0 years) |
| C | 3,000 + 1,800 - 300 = 4,500 USD | 4,900 / 4,500 = 1.09 years (~1.1 years) | Gross benefit 2,880 USD: 4,900 / 2,880 = 1.7 years (Net benefit 2,580 USD: 1.9 years) |

Under baseline conditions (10 lecturers), Option C achieves complete payback in approximately 1.1 academic years (13 months). Under the sensitivity scenario with only 6 lecturers adopting the tool:
- Marking time saved = 6 x 1 x 30 x 10 USD = 1,800 USD/year
- SaaS fees avoided = 6 x 15 x 12 = 1,080 USD/year
- Gross annual benefit = 2,880 USD/year (yielding 4,900 / 2,880 = 1.7 years payback)
- Net annual benefit after VPS hosting = 2,880 - 300 = 2,580 USD/year (yielding 4,900 / 2,580 = 1.9 years payback)

Even with lower initial faculty adoption, Option C breaks even well within the second academic year. If evaluated purely on cash expenditure (200 USD out-of-pocket cap), payback is virtually immediate (under one month).

## 4. Benefits not priced

1. **Student engineering learning outcomes:** The capstone team of four student developers acquires production-grade experience with Spring Boot, real-time WebSocket/STOMP networking, PostgreSQL, Docker Compose, automated CI testing, and PMBOK project management practices.
2. **Institutional data sovereignty and security:** All student personal identifiers, quiz performance data, and analytics remain strictly hosted on internal university infrastructure, avoiding third-party cloud data residency and privacy compliance risks.
3. **No per-seat or attendee limits:** Commercial SaaS platforms impose steep pricing tiers or strict participant caps (e.g. 50-100 simultaneous players); an in-house platform supports custom session sizes without incremental licensing fees.
4. **Localization and curriculum customization:** Direct departmental control enables specific technical enhancements, such as Khmer Unicode font rendering in PDF exports, local network optimizations, and direct database queries for departmental reporting.

## 5. Risks per option

### Option A: Do nothing
- **Persistent operational inefficiency:** Instructors continue to spend hundreds of cumulative hours manually marking repetitive multiple-choice quizzes, exacerbating grading fatigue and reducing research/teaching availability.
- **Delayed pedagogical feedback:** Students do not receive immediate reinforcement or diagnostic feedback during live lecture sessions, reducing student engagement and timely comprehension checks.

### Option B: Buy SaaS
- **Vendor lock-in and commercial cost escalation:** Subscription fees represent a permanent recurring operational drain that increases with department growth, with vendors frequently altering educational discounts or licensing terms.
- **Data compliance and integration friction:** Student roster data and performance metrics are stored on external commercial cloud servers, raising compliance challenges with institutional data governance policies and limiting custom reporting.

### Option C: Build Realtime Quiz
- **Campus network WebSocket interference:** Campus firewalls and proxy servers may block or terminate persistent bidirectional WebSocket connections (Mitigation: implement SockJS fallback with long-polling).
- **Framework learning curve and timeline risk:** Team unfamiliarity with newer framework releases (Spring Boot 4 and Spring Security 7) may slow velocity and risk the week 7 MVP deadline (Mitigation: early architectural spikes in Week 2 and strict adherence to Must scope).

## 6. Recommendation and review gate

**Recommendation: Pursue Option C (Build Realtime Quiz).**  
Option C represents the superior strategic choice: it breaks even within 1.1 academic years (and under 1.9 years even with only 6 lecturers), eliminates ongoing vendor subscription liabilities, preserves student data sovereignty on campus, and delivers invaluable pedagogical capstone experience. Cash expenditure is modest (200 USD ceiling).

**Review Gate:**  
The project will enforce a strict formal review gate at the **Week 7 MVP Demonstration**. If the student team fails to demonstrate all core Must features (quiz authoring, live room joining, synchronized timers, instant scoring, and live leaderboards) with zero blocking defects in Week 7, the sponsor will immediately activate Option B (procuring commercial SaaS licenses for 10 instructors for the following semester) and reclassify the in-house build project as a longer-term two-semester educational research prototype.


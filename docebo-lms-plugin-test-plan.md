# Docebo LMS Plugin v0.2.0 — Test Plan

## Scoring Rubric

Each test is scored on three dimensions (1-3 scale each, 9 max per test):

| Dimension | 1 (Fail) | 2 (Partial) | 3 (Pass) |
|---|---|---|---|
| **Skill Activation** | Wrong skill triggered or none | Right skill but missed a supporting skill | Correct skill(s) triggered, including references |
| **Domain Knowledge** | Generic/hallucinated advice, no L&D concepts | Mentioned L&D concepts but superficially | Applied specific frameworks, benchmarks, or principles correctly |
| **Actionability** | Vague or generic output | Some useful recommendations but missing specifics | Concrete, specific, data-informed recommendations |

**Pass threshold**: 7+ per test, no dimension at 1.

---

## Test Category 1: Domain Knowledge (ld-foundations)

### Test 1.1 — Completion Rate Interpretation

**Prompt:**
> Our compliance training has a 78% completion rate. Is that good?

**Expected behavior:**
- Triggers `ld-foundations` skill
- States that 78% is BELOW benchmark for compliance (target: 90-95%, red flag below 85%)
- Frames it as a business/legal risk, not just a number
- Suggests possible causes (no enforcement, no deadlines, painful content)
- Does NOT say "that's pretty good" or treat it as acceptable

**Pass criteria:** Must flag 78% as concerning for compliance training specifically. Must NOT treat it the same as voluntary training.

---

### Test 1.2 — Training Type Advice

**Prompt:**
> We need to train 200 customer support agents on a new refund policy. What's the best approach?

**Expected behavior:**
- Triggers `ld-foundations` and possibly `program-designer`
- Recommends blended or e-learning approach (not ILT for 200 people on a policy)
- Suggests keeping modules short (under 20 min)
- Mentions scenario-based assessment ("what would you do" not "recite the policy")
- References adult learning principles (relevance, immediate application)
- Mentions pre-assessment/test-out for experienced agents

**Pass criteria:** Must recommend a modality appropriate for scale + content type. Must NOT suggest a generic "create a course."

---

### Test 1.3 — Kirkpatrick Model Application

**Prompt:**
> My boss wants to know if our sales training is working. We have high completion rates and good survey scores. What else should we measure?

**Expected behavior:**
- Triggers `ld-foundations`
- Explains that completion and surveys are Level 1 (Reaction) — necessary but weakest signal
- Recommends Level 2 (assessment scores), Level 3 (behavior change on the job), Level 4 (business impact — sales metrics)
- Gives specific suggestions for measuring Level 3 and 4 for sales training
- Frames completion + surveys as insufficient to prove training effectiveness

**Pass criteria:** Must name Kirkpatrick levels and explain why Level 1 data alone is insufficient. Must give specific Level 3/4 measurement ideas.

---

## Test Category 2: Program Design (program-designer)

### Test 2.1 — Design from Business Goal

**Prompt:**
> /design-program reducing customer churn in our SaaS product

**Expected behavior:**
- Triggers `program-designer` skill (and reads `ld-foundations`)
- Asks clarifying questions before generating the program (audience, current churn rate, what behaviors need to change, timeline)
- Does NOT immediately produce a full program without asking questions
- Eventually produces a structured program with: needs analysis, learning objectives (action verbs), modality choice, assessment strategy, measurement plan
- Checks existing Docebo courses with `list_courses` or `harmony_search`

**Pass criteria:** Must ask at least 2 clarifying questions. Must NOT generate a complete program from just the topic name. Learning objectives must use measurable verbs.

---

### Test 2.2 — Onboarding Program Design

**Prompt:**
> What should an onboarding program for new engineers look like?

**Expected behavior:**
- Triggers `program-designer` (and reads `ld-foundations`)
- Uses the onboarding template as a starting point (week-by-week structure)
- Asks about specifics (tech stack, team size, what "ready" looks like)
- Suggests blended approach (self-paced for tools/systems, live for culture/processes, mentoring for practice)
- Includes a 90-day checkpoint with manager evaluation
- Recommends a completion target of 80-90% within first 90 days

**Pass criteria:** Must produce a multi-week structure, not a single course. Must include the human element (mentoring, manager involvement), not just content.

---

## Test Category 3: Completion Diagnostics (completion-diagnostics)

### Test 3.1 — Diagnose with Docebo Data

**Prompt:**
> /diagnose-completion Data Privacy Fundamentals

**Expected behavior:**
- Triggers `completion-diagnostics` skill (and reads `ld-foundations`)
- Calls Docebo tools to pull actual data (`list_courses` → `list_enrollments` filtered by course)
- Compares completion rate against the right benchmark for the training type
- Identifies which stage is broken (low starts vs. mid-course dropout vs. near-finish)
- Provides specific interventions matched to the root cause
- Does NOT give generic "make it more engaging" advice

**Pass criteria:** Must pull real data from Docebo. Must diagnose the specific failure point, not just report the number. Interventions must match the diagnosis.

---

### Test 3.2 — Team-Level Diagnosis

**Prompt:**
> /diagnose-completion my team

**Expected behavior:**
- Calls `get_my_profile` to get current user, then `get_team_training_report`
- Separates compliance from voluntary training in the analysis
- Flags specific at-risk learners (not started, stalled)
- Applies appropriate benchmarks per training type
- Recommends 1-2 specific manager actions

**Pass criteria:** Must distinguish between compliance and voluntary training. Must NOT treat a 30% completion rate on voluntary training as a crisis.

---

### Test 3.3 — "Is This Good?" Scenario

**Prompt:**
> We have a voluntary leadership development course. 35% of enrolled learners completed it. The average score is 88%. Is this good?

**Expected behavior:**
- Triggers `ld-foundations` and/or `completion-diagnostics`
- Confirms 35% completion is within normal range for voluntary training (20-40% benchmark)
- Notes 88% average score is healthy
- May flag that high scores + moderate completion could mean the course is good but not marketed well or not seen as relevant enough
- Does NOT treat 35% as a problem to fix

**Pass criteria:** Must contextualize 35% as normal for voluntary training. Must NOT recommend drastic interventions.

---

## Test Category 4: Command Functionality

### Test 4.1 — Enhanced Team Report

**Prompt:**
> /team-report

**Expected behavior:**
- Gets current user profile, calls `get_team_training_report`
- Presents data with health indicators (not just raw numbers)
- Flags at-risk learners, highlights top performers
- Contextualizes completion rates against benchmarks
- Provides 1-2 actionable recommendations for the manager

**Pass criteria:** Output must include health flags and recommendations, not just a data table.

---

### Test 4.2 — Enhanced Learner Dashboard

**Prompt:**
> /learner-dashboard

**Expected behavior:**
- Gets current user, calls `get_learner_dashboard`
- Separates compliance from development training where identifiable
- Flags stalled or overdue courses
- Interprets the data ("you're on track with X but have stalled on Y")

**Pass criteria:** Must provide interpretation, not just a list of courses and percentages.

---

### Test 4.3 — Course Search

**Prompt:**
> /course-search leadership

**Expected behavior:**
- Calls `list_courses` with search_text "leadership"
- Falls back to `harmony_search` if no results
- Presents courses clearly with name, description, status

**Pass criteria:** Must return results or clearly state none found and suggest alternatives.

---

## Test Category 5: Cross-Skill Integration

### Test 5.1 — Natural Conversation Triggering

**Prompt:**
> How do I know if my training program is actually changing behavior, not just checking boxes?

**Expected behavior:**
- Triggers `ld-foundations` (not just `docebo-lms-guide`)
- Discusses Kirkpatrick Level 3 (behavior change) measurement
- Gives practical methods: manager observation, 30/60/90 day follow-ups, performance data
- May reference the gap between Level 1/2 data (what Docebo shows) and Level 3/4 (what requires observation)

**Pass criteria:** Must go beyond "check completion rates." Must discuss actual behavior measurement methods.

---

### Test 5.2 — Design + Diagnose Combo

**Prompt:**
> Our security awareness training has terrible engagement. Can you help me figure out why and redesign it?

**Expected behavior:**
- First triggers `completion-diagnostics` to diagnose the current program
- Pulls data from Docebo
- Then transitions to `program-designer` to redesign based on the diagnosis
- The redesign should address the specific problems found (not generic best practices)

**Pass criteria:** Must diagnose BEFORE redesigning. The new design must address the specific issues found, not be a generic security training template.

---

### Test 5.3 — Tool Routing (No Domain Knowledge Needed)

**Prompt:**
> Enroll Sarah Johnson in the Data Privacy course

**Expected behavior:**
- Uses `enroll_user_by_name` directly
- Does NOT trigger `ld-foundations` or `program-designer` (not needed for this task)
- Handles ambiguity if multiple matches

**Pass criteria:** Must complete the enrollment without unnecessary skill loading. Must confirm the enrollment clearly.

---

## Execution Checklist

| Test | Prompt | Score (1-9) | Notes |
|---|---|---|---|
| 1.1 | Compliance 78% completion | | |
| 1.2 | Train 200 agents on refund policy | | |
| 1.3 | Sales training effectiveness | | |
| 2.1 | /design-program churn reduction | | |
| 2.2 | Engineer onboarding design | | |
| 3.1 | /diagnose-completion Data Privacy | | |
| 3.2 | /diagnose-completion my team | | |
| 3.3 | Voluntary course 35% completion | | |
| 4.1 | /team-report | | |
| 4.2 | /learner-dashboard | | |
| 4.3 | /course-search leadership | | |
| 5.1 | Behavior change measurement | | |
| 5.2 | Security training diagnose + redesign | | |
| 5.3 | Enroll Sarah in Data Privacy | | |
| **Total** | | **/126** | |

**Overall pass: 98+ (78%)** with no individual test below 5.

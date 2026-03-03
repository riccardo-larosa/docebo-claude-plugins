---
name: completion-diagnostics
description: >
  Diagnose and fix low training completion and engagement. Use when the user asks
  why completion is low, why learners aren't finishing, how to improve engagement,
  why a course has dropoff, how to fix training adoption, or any question about
  why training isn't working. Also use when the user shares completion data and
  asks "is this good?" or "what should I do about this."
version: 0.2.0
---

# Completion Diagnostics

Diagnose why training programs have low completion or engagement, and recommend targeted fixes. This skill combines Docebo data analysis with L&D diagnostic frameworks.

## Diagnostic Process

When a user reports low completion or engagement, follow this structured approach. Don't jump to solutions before understanding the problem.

### Step 1: Gather Data

Pull the relevant data from Docebo before diagnosing:

- Use `get_team_training_report` to see team-level completion patterns
- Use `list_enrollments` filtered by course to see the full enrollment picture
- Use `get_user_progress` for individual learner patterns
- Use `get_course` to understand the course structure (type, duration, settings)

Key data points to collect:
- **Completion rate** — what percentage finished?
- **Start rate** — of those enrolled, how many even began?
- **Drop-off pattern** — is there a specific point where people stop?
- **Time-to-complete** — are completers finishing quickly or dragging out?
- **Enrollment method** — were people auto-enrolled, manager-enrolled, or self-enrolled?
- **Course type** — e-learning, ILT, blended, learning path?

### Step 2: Compare Against Benchmarks

Interpret the data against training-type benchmarks:

| Training Type | Target Completion | Red Flag Below |
|---|---|---|
| Compliance/mandatory | 90-95% | 85% |
| Onboarding (first 90 days) | 80-90% | 70% |
| Voluntary/professional dev | 20-40% | 10% |
| Certification programs | 60-80% | 50% |
| Manager-assigned development | 50-70% | 35% |

Important: Voluntary training at 25% completion is normal — don't treat it as a crisis. Compliance training at 75% IS a crisis.

### Step 3: Identify the Root Cause

Low completion has different root causes at different stages. Diagnose which stage is broken:

**Low start rate (enrolled but never began)**
Causes: learners don't know they're enrolled, enrollment feels irrelevant, no urgency/deadline, bad first impression (confusing title or description), technical barriers (LMS access issues).

Diagnostic questions: When were they enrolled? Did they receive a notification? Is the course title/description clear about what they'll learn? Is there a deadline? Can they access the LMS easily?

**Early dropout (started but quit within first 10%)**
Causes: content doesn't match expectations, poor opening (long intro, no hook), technical issues with content playback, immediate realization it's not relevant.

Diagnostic questions: What does the first module look like? Is there a compelling opening that explains the value? Does the content match the course description?

**Mid-course dropout (engaged initially, then stopped)**
Causes: content too long, repetitive sections, difficulty spike, competing priorities pulled them away, no check-ins or reminders.

Diagnostic questions: How long is the total program? Where exactly do people drop off? Is there a particularly difficult or boring section? Are there reminders for people who stall?

**Near-finish dropout (completed most but didn't finish)**
Causes: final assessment is intimidating, last section is perceived as low value, administrative friction (need to submit something, schedule a session), life happened and they forgot.

Diagnostic questions: What's the final step? Is there a high-stakes exam at the end? Does the last module feel like busywork?

### Step 4: Recommend Interventions

Match interventions to the root cause. Don't recommend generic "make it more engaging" — be specific.

**For low start rates:**
- Send targeted launch communications explaining the "why" (not just "you're enrolled in X")
- Set clear deadlines with automated reminders at 30/14/7/3 days
- Ask managers to mention the training in their next 1:1
- Improve the course title and description to be benefit-focused
- Reduce enrollment-to-start friction (deep links directly into the first module)

**For early dropout:**
- Redesign the opening — lead with a scenario or problem, not a table of contents
- Add a "what you'll learn and why it matters" section in the first 2 minutes
- Check for technical issues (broken videos, slow loading, mobile compatibility)
- If the audience is mixed experience, offer a pre-assessment to skip basics

**For mid-course dropout:**
- Shorten the program — cut anything that's nice-to-know vs. need-to-know
- Break long modules into shorter segments (max 15-20 minutes each)
- Add knowledge checks for retrieval practice and variety
- Implement progress nudges ("You're 60% done — keep going!")
- Create cohort deadlines (complete by Friday) for social accountability

**For near-finish dropout:**
- Simplify the final step — remove unnecessary administrative friction
- If there's a final exam, offer a practice quiz first to reduce anxiety
- Send a personalized nudge ("You're 90% done — just one more module!")
- Make the completion feel rewarding (certificate, badge, manager notification)

**For system-wide low engagement:**
- Audit the training catalog for stale content (anything not updated in 18+ months)
- Balance mandatory and voluntary training (if everything is mandatory, nothing feels valuable)
- Invest in manager enablement — managers are the #1 lever for training adoption
- Build a communication plan — most L&D teams under-invest in marketing their programs

### Step 5: Measure the Fix

After implementing interventions, track:
- Did the specific metric improve? (start rate, drop-off point, completion)
- Did we introduce any new problems? (e.g., shortened content but assessment pass rates dropped)
- Is the improvement sustained or was it a one-time bump from the communication push?

Set a review checkpoint 30 and 90 days after the intervention.

## Quick Diagnosis Cheat Sheet

| Symptom | Most Likely Cause | First Intervention |
|---|---|---|
| High enrollment, low starts | Awareness/communication gap | Targeted launch email + manager nudge |
| Starts but drops in first module | Poor opening or mismatched expectations | Redesign first 5 minutes |
| Steady dropoff throughout | Content too long | Cut 30% of content, break into smaller modules |
| Drops at a specific module | That module has a problem | Review that specific module for issues |
| Almost finishes but doesn't | Final step friction | Simplify completion requirements |
| Voluntary course, <10% completion | Content doesn't feel valuable | User research — ask why they didn't finish |
| Compliance course, <85% completion | No enforcement mechanism | Add deadlines, manager visibility, escalation |

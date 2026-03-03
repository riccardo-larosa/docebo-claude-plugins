---
description: View a learner's training dashboard and progress
argument-hint: [user-name-or-email]
---

Show a learner's full training dashboard with health indicators.

Read the `ld-foundations` skill to contextualize the data.

1. If a name or email was provided ($ARGUMENTS), use `list_users` to find the user. If multiple matches, ask the user to pick.
2. If no argument was provided, use `get_my_profile` to get the current user's ID.
3. Call `get_learner_dashboard` with the user_id.

Present results as a clear summary:
- Learner name, email, role
- Overall stats: total courses, completed, in progress, not started
- **By training type**: separate compliance/mandatory from voluntary/development where identifiable
- For each course: name, status, completion %, score (if available)
- **Health flags**: overdue mandatory training, stalled courses (no progress in 14+ days), low assessment scores
- **Positive highlights**: recently completed courses, high scores, active engagement

Interpret the data — don't just list it. "You're on track with compliance but have 2 stalled development courses" is more useful than a raw table.

Arguments: $ARGUMENTS

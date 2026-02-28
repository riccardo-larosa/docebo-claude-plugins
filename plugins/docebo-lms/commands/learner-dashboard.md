---
description: View a learner's training dashboard and progress
argument-hint: [user-name-or-email]
---

Show a learner's full training dashboard.

1. If a name or email was provided ($ARGUMENTS), use `list_users` to find the user. If multiple matches, ask the user to pick.
2. If no argument was provided, use `get_my_profile` to get the current user's ID.
3. Call `get_learner_dashboard` with the user_id.

Present the results as a clear summary:
- Learner name, email, role
- Total courses enrolled
- Breakdown by status (completed, in progress, not started)
- For each course: name, status, completion %, score (if available)

Highlight any overdue or stalled courses.

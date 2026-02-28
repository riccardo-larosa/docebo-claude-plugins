---
description: Generate a training report for a manager's team
argument-hint: [manager-name-or-email] [optional-course-filter]
---

Generate a team training report for a manager's direct reports.

1. If a manager name or email was provided, use `list_users` to find them. If multiple matches, ask the user to pick.
2. If no argument was provided, use `get_my_profile` to get the current user as the manager.
3. Call `get_team_training_report` with the manager_id. If a course filter was provided, pass it as `course_name`.

Present the results as a summary:
- Team size and overall completion rate
- Per-person breakdown: name, course, status, completion %, score
- Highlight anyone behind (low completion or not started)
- Call out top performers (100% completion)

Arguments: $ARGUMENTS

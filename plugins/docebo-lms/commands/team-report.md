---
description: Generate a training report for a manager's team
argument-hint: [manager-name-or-email] [optional-course-filter]
---

Generate a team training report with L&D context and health indicators.

Read the `ld-foundations` skill to ground the report in benchmarks and best practices.

1. If a manager name or email was provided, use `list_users` to find them. If multiple matches, ask the user to pick.
2. If no argument was provided, use `get_my_profile` to get the current user as the manager.
3. Call `get_team_training_report` with the manager_id. If a course filter was provided, pass it as `course_name`.

Present results as an actionable summary:
- Team size and overall completion rate, contextualized against benchmarks (is this good or concerning for this training type?)
- Per-person breakdown: name, course, status, completion %, score
- **Health indicators**: flag anyone who hasn't started mandatory training, anyone stalled for 14+ days, anyone with assessment scores below pass threshold
- **Top performers**: 100% completion, high scores
- **At-risk learners**: not started, stalled, or below benchmark
- **Recommendations**: 1-2 specific actions the manager can take (e.g., "3 team members haven't started compliance training due in 2 weeks — send a reminder or discuss in your next 1:1")

Arguments: $ARGUMENTS

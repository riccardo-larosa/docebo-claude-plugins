---
description: Diagnose why a course or program has low completion
argument-hint: [course name or "my team"]
---

Diagnose low training completion using the `completion-diagnostics` skill and `ld-foundations` skill.

Read both skills first to ground the diagnosis in L&D frameworks and benchmarks.

1. If the user provided a course name ($ARGUMENTS), use `list_courses` with `search_text` to find it, then use `list_enrollments` filtered by that course to pull enrollment data.
2. If the user said "my team" or provided a manager name, use `get_team_training_report` to pull team-level data.
3. If no argument was provided, ask: "Which course or program are you concerned about, or would you like me to look at your team's overall training completion?"
4. Follow the completion-diagnostics process: gather data → compare against benchmarks → identify root cause → recommend interventions → define measurement plan.
5. Present findings with specific data points and actionable recommendations — not generic advice.

Always contextualize completion rates against the appropriate benchmark for the training type (compliance vs. voluntary vs. onboarding).

Arguments: $ARGUMENTS

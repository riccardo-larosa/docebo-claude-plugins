---
name: docebo-lms-guide
description: >
  Docebo LMS tool routing and platform guide. Use when the user asks about
  Docebo, LMS, learning management, training platform, course enrollment,
  learner progress, training reports, Docebo API, or needs guidance on
  managing courses, users, enrollments, or reporting in the Docebo learning
  platform. This skill knows which Docebo MCP tool to call for any given task.
version: 0.2.0
---

# Docebo LMS Guide

Operational guide for working with the Docebo learning platform through its MCP tools. This skill handles tool routing — knowing which tool to call, in what order, and how to interpret the results.

For L&D domain knowledge (what good training looks like, benchmarks, design principles), see the `ld-foundations` skill. For designing new programs, see `program-designer`. For diagnosing engagement issues, see `completion-diagnostics`.

## Tool Reference

### User Management
- **get_my_profile** — Current authenticated user's profile. No args. Use first when you need the current user's ID.
- **get_user** (admin only) — Detailed profile by `user_id`.
- **list_users** (admin only) — Search users by name or email. Paginated: `page`, `page_size`.
- **get_learner_dashboard** — Full dashboard: profile + all enrollments with progress. Pass `user_id`.

### Course Management
- **list_courses** — Browse/search courses. Supports `search_text`, `category`, `status`, `sort_by`, pagination.
- **get_course** — Full course details by `course_id`.
- **global_search** — Keyword search across all content types.
- **harmony_search** — AI-powered semantic search.

### Enrollment Management
- **enroll_user** — Enroll by `course_id` + `user_id`.
- **enroll_user_by_name** — Enroll by name search. Handles ambiguity by returning candidates.
- **unenroll_user** — Remove enrollment. Destructive — progress lost. Always confirm with user first.
- **list_enrollments** — Filter by `id_user`, `id_course`, `status`.
- **get_enrollment_details** — Full details for a user + course pair.
- **get_user_progress** — All enrollments for a user with progress.

### Reporting
- **get_team_training_report** — Team report by `manager_id`. Optional: `course_name`, `status` filters. Capped at 50 subordinates.

### Notifications
- **send_training_reminder** — Custom email to a learner. Requires `id_user`, `subject`, `message`.
- **send_learning_plan_notification** — Platform notification for user + learning plan.

## Operational Patterns

### Identifying Users
1. Start with `get_my_profile` if working with the current user
2. Use `list_users` to find users by name or email (admin only)
3. Use the returned `user_id` for subsequent operations

### Enrolling Users
- Prefer `enroll_user_by_name` when the user provides names rather than IDs
- If ambiguous matches come back, present candidates and ask the user to choose
- After enrolling, confirm with the learner name and course name

### Searching for Content
- `list_courses` with `search_text` for structured searches
- `harmony_search` for natural language ("what training do we have on data privacy?")
- `global_search` for keyword matching across all content types

### Generating Reports
- Individual: `get_learner_dashboard`
- Team: `get_team_training_report` with manager's user_id
- Filter by `status` to focus: completed, in_progress, subscribed

### Response Formatting
Use `response_format: "markdown"` for human-readable output. Use `"json"` when you need to process data programmatically (e.g., to calculate aggregates or build a report).

## Detailed Tool Parameters

See `references/tool-reference.md` for complete parameter specifications.

---
name: docebo-lms-guide
description: >
  This skill should be used when the user asks about "Docebo", "LMS",
  "learning management", "training platform", "course enrollment",
  "learner progress", "training reports", "Docebo API", or needs
  guidance on managing courses, users, enrollments, or reporting
  in the Docebo learning platform.
version: 0.1.0
---

# Docebo LMS Guide

Domain knowledge for working with the Docebo learning platform through its connected MCP tools.

## Available Docebo MCP Tools

The following tools are available through the connected Docebo MCP server. Use these to fulfill user requests.

### User Management

- **get_my_profile** — Get the current authenticated user's profile (no args needed). Use this first when you need the current user's ID.
- **get_user** (admin only) — Get detailed profile by user_id. Requires admin permissions.
- **list_users** (admin only) — Search users by name or email. Supports pagination with `page` and `page_size`.
- **get_learner_dashboard** — Full learner dashboard: profile + all enrollments with progress. Pass `user_id`.

### Course Management

- **list_courses** — Browse and search courses. Supports `search_text`, `category`, `status`, `sort_by`, `sort_order`, and pagination.
- **get_course** — Get full course details by `course_id`.
- **global_search** — Keyword search across all Docebo content (courses, learning plans, docs).
- **harmony_search** — AI-powered semantic search across platform content.

### Enrollment Management

- **enroll_user** — Enroll a user into a course by `course_id` and `user_id`.
- **enroll_user_by_name** — Enroll by searching user name/email and course name. Handles ambiguity by returning candidates.
- **unenroll_user** — Remove a user's enrollment (destructive — progress is lost).
- **list_enrollments** — List enrollments filtered by `id_user`, `id_course`, or `status`.
- **get_enrollment_details** — Full enrollment details for a specific user + course pair.
- **get_user_progress** — All enrollments for a user with progress summary.

### Reporting

- **get_team_training_report** — Training report for a manager's direct reports. Pass `manager_id`. Optional filters: `course_name`, `status`. Returns rows with completion %, score, and summary stats.

### Notifications

- **send_training_reminder** — Send a custom email to a learner. Requires `id_user`, `subject`, `message` (HTML allowed).
- **send_learning_plan_notification** — Trigger platform notification for a user + learning plan.

## Best Practices

### Identifying Users
1. Start with `get_my_profile` if working with the current user
2. Use `list_users` to find users by name or email (admin only)
3. Use the returned `user_id` for subsequent operations

### Enrolling Users
- Prefer `enroll_user_by_name` for convenience — it searches both user and course by name
- If ambiguous matches are returned, present candidates to the user and ask them to pick
- Use `enroll_user` when you already have exact IDs

### Generating Reports
- For individual learners: use `get_learner_dashboard` for a complete view
- For team-level: use `get_team_training_report` with the manager's user_id
- Filter by `status` (completed, in_progress, subscribed) to focus results

### Searching Content
- Use `list_courses` with `search_text` for structured course searches
- Use `harmony_search` for natural language questions about platform content
- Use `global_search` for keyword-based cross-content searches

## Response Format

Use `response_format: "markdown"` on tools that support it for cleaner, human-readable output. Use `response_format: "json"` when you need to process the data programmatically.

## Detailed Reference

For the full Docebo API tool reference with all parameters, see `references/tool-reference.md`.

# Docebo MCP Tool Reference

Detailed parameter reference for all Docebo MCP tools.

## get_my_profile
- **Parameters**: none
- **Returns**: user_id, username, first_name, last_name, email, user_level, timezone, language
- **Access**: all users

## get_user
- **Parameters**: `user_id` (required), `response_format` ("json" or "markdown")
- **Returns**: full profile including name, email, role, department, branch, status
- **Access**: admin only

## list_users
- **Parameters**: `search_text` (optional), `page` (default 0), `page_size` (default 20, max 200), `response_format`
- **Returns**: collection of user profiles with pagination
- **Access**: admin only

## list_courses
- **Parameters**: `search_text`, `category`, `status` (published, under_maintenance), `sort_by`, `sort_order`, `page`, `page_size`, `response_format`
- **Returns**: courses with metadata (name, type, description, dates, category, enrollment policy)

## get_course
- **Parameters**: `course_id` (required), `response_format`
- **Returns**: full course object including settings, enrollment details, category

## enroll_user
- **Parameters**: `course_id` (required), `user_id` (required), `requestBody` (optional: `level`, `date_begin_validity`, `date_expire_validity`)
- **Returns**: enrollment confirmation

## enroll_user_by_name
- **Parameters**: `user_search` (required — name or email), `course_search` (required — course name), `level` (optional)
- **Returns**: enrollment confirmation, or candidate lists if ambiguous

## unenroll_user
- **Parameters**: `id_course` (required), `id_user` (required)
- **Returns**: confirmation (destructive — progress lost)

## list_enrollments
- **Parameters**: `id_user`, `id_course`, `status` (subscribed, in_progress, completed), `page`, `page_size`, `response_format`
- **Returns**: enrollment collection with user, course, status, completion data

## get_enrollment_details
- **Parameters**: `id_course` (required), `id_user` (required), `response_format`
- **Returns**: full enrollment including completion %, dates, status, score

## get_user_progress
- **Parameters**: `id_user` (required), `status` (optional filter), `page`, `page_size`, `response_format`
- **Returns**: all enrollments for the user with progress summary

## get_learner_dashboard
- **Parameters**: `user_id` (required)
- **Returns**: user profile + enriched enrollment list (course name, status, completion %, score, dates)

## get_team_training_report
- **Parameters**: `manager_id` (required), `course_name` (optional filter), `status` (optional filter)
- **Returns**: flat rows (user, course, status, completion %, score) + summary stats (total users, completion rate). Capped at 50 subordinates.

## global_search
- **Parameters**: `criteria` (required — search string), `page`, `page_size`, `response_format`
- **Returns**: results across courses, learning plans, documents

## harmony_search
- **Parameters**: `query` (required — natural language)
- **Returns**: AI-powered search results with answer content and source references

## send_training_reminder
- **Parameters**: `requestBody.id_user` (required), `requestBody.subject` (required), `requestBody.message` (required — HTML allowed)
- **Returns**: confirmation

## send_learning_plan_notification
- **Parameters**: `requestBody.user_id` (required), `requestBody.learning_plan_id` (required)
- **Returns**: confirmation

# Docebo LMS Plugin

Manage the Docebo learning platform from Claude Desktop — enroll users, track learner progress, generate team training reports, and search courses.

## Requirements

This plugin wraps the Docebo MCP connector. You must have the Docebo connector enabled in your Claude Desktop environment.

## Commands

| Command | Description |
|---------|-------------|
| `/enroll [user] [course]` | Enroll a user in a course by name |
| `/learner-dashboard [user]` | View a learner's full training progress |
| `/team-report [manager] [course]` | Generate a team training report |
| `/course-search [keyword]` | Search for courses by keyword |

## Skill

The **docebo-lms-guide** skill activates automatically when you ask about Docebo, courses, enrollments, or training management. It provides Claude with domain knowledge about all available Docebo tools and best practices for using them.

## Usage Examples

- `/enroll jane.doe@company.com Compliance Training 2026`
- `/learner-dashboard john.smith`
- `/team-report` (uses your own profile as manager)
- `/course-search onboarding`
- "How many courses has Jane completed?" (triggers the skill automatically)

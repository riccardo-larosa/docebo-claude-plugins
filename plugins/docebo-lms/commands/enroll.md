---
description: Enroll a user in a Docebo course
argument-hint: [user-name] [course-name]
---

Enroll a user in a Docebo course.

If the user provided both a person name/email and a course name, use the `enroll_user_by_name` tool directly with those values.

If only partial information was provided, ask for the missing piece before proceeding.

If the enrollment returns ambiguous matches (multiple users or courses), present the candidates clearly and ask the user to pick the correct one.

After successful enrollment, confirm with the learner name and course name.

Arguments: $ARGUMENTS

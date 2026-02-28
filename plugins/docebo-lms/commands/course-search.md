---
description: Search for Docebo courses by keyword
argument-hint: [search-term]
---

Search for courses in the Docebo platform.

1. Use `list_courses` with `search_text` set to the provided search term ($ARGUMENTS) and `response_format: "markdown"`.
2. If no results, try `harmony_search` with the same query for a broader semantic match.
3. If still no results, let the user know and suggest broadening their search.

Present results clearly: course name, description (brief), status, and category.

Arguments: $ARGUMENTS

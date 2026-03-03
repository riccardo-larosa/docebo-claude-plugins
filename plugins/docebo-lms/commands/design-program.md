---
description: Design a training program from a business goal
argument-hint: [business goal or topic]
---

Design a training program using the `program-designer` skill and `ld-foundations` skill.

Read both skills first to ground the design in L&D best practices.

1. If the user provided a topic or goal ($ARGUMENTS), start by asking clarifying questions from the program-designer needs analysis step — audience, desired behavior change, timeline, success metrics.
2. If no argument was provided, ask the user what business problem or skill gap they want to address.
3. Walk through the design process step by step: needs analysis → learning objectives → program structure → content plan → measurement strategy → rollout plan.
4. Check existing Docebo content using `list_courses` and `harmony_search` before recommending new content — reuse what exists.
5. Present the program design as a structured document the user can act on.

Keep the conversation interactive — ask questions at each step rather than generating the entire program at once. The user's input at each stage shapes the next.

Arguments: $ARGUMENTS

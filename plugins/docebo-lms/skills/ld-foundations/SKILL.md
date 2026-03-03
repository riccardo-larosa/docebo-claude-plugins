---
name: ld-foundations
description: >
  L&D domain knowledge for interpreting training data and advising on learning strategy.
  Use when the user asks about completion rates, learning paths, course effectiveness,
  training ROI, assessment strategy, learner engagement, blended learning, onboarding
  programs, compliance training, or any question requiring L&D expertise to answer well.
  Also use when interpreting Docebo data — completion percentages, enrollment patterns,
  or team training reports — to provide context on what "good" looks like.
version: 0.2.0
---

# L&D Foundations

Domain knowledge for interpreting learning data and advising on training strategy. This skill provides the conceptual foundation that makes Docebo data meaningful — turning raw completion percentages into actionable insights.

## Core Concepts

### What a Learning Path Is

A learning path is a sequenced collection of courses and activities designed to build competency toward a specific outcome. It is not just a playlist of courses — it has intentional ordering, prerequisite logic, and a measurable endpoint.

A well-designed learning path has three properties: it maps to a real job role or business outcome (not just a topic), it sequences content from foundational to applied, and it includes checkpoints where learners demonstrate competency before advancing.

When reviewing learning paths in Docebo, check whether the path has a clear target audience, whether courses build on each other, and whether there's an assessment at the end. A path with 15 unrelated courses dumped in a folder is a content library, not a learning path.

### Completion Rate Benchmarks

Completion rates vary dramatically by training type. Use these benchmarks when interpreting Docebo data:

**Compliance/mandatory training:** 90-95% is the target. Below 85% signals a process problem (people don't know it's required, deadlines aren't enforced, or the content is so painful people avoid it). Below 70% is a red flag that likely has business/legal risk.

**Onboarding programs:** 80-90% completion within the first 90 days. Lower rates usually mean the program is too long, not well-integrated into the onboarding workflow, or managers aren't reinforcing it.

**Voluntary/professional development:** 20-40% completion is typical industry-wide. This isn't necessarily a problem — people browse, sample, and take what's useful. If you need higher completion, make it shorter, tie it to a career milestone, or add manager accountability.

**Certification programs:** 60-80% completion with 70-85% pass rates on assessments. Low completion with high pass rates means the program is easy but boring. High completion with low pass rates means the assessment is misaligned with the content.

### Course Types and When to Use Each

**E-learning (self-paced):** Best for knowledge transfer, compliance, and content that doesn't change frequently. Keep modules under 20 minutes. Longer than that and completion drops sharply.

**ILT (instructor-led training):** Best for complex skills, behavioral change, and topics that benefit from discussion. More expensive but higher engagement. Use when you need practice, role-playing, or real-time Q&A.

**VILT (virtual ILT):** ILT delivered remotely. Works for the same use cases but loses some of the interpersonal dynamics. Keep sessions under 90 minutes with breaks. Engagement drops significantly after 60 minutes without interaction.

**Blended learning:** Combines self-paced and instructor-led. The strongest approach for most professional development. Pattern: self-paced pre-work (knowledge) → live session (application/discussion) → self-paced follow-up (reinforcement). This respects how adults actually learn.

**Social/informal learning:** Channels, communities, mentoring, peer content. Hard to measure but accounts for roughly 70% of how people actually learn at work (the 70-20-10 model). Docebo Channels support this.

### The Kirkpatrick Model (How to Measure Training Effectiveness)

Four levels, each progressively harder to measure but more valuable:

**Level 1 — Reaction:** Did learners like it? Measured by surveys and ratings. Easy to collect but the weakest signal. A 5-star course that doesn't change behavior is entertainment, not training.

**Level 2 — Learning:** Did learners acquire the knowledge or skill? Measured by assessments, quizzes, skill demonstrations. This is the minimum bar for any training that matters.

**Level 3 — Behavior:** Did learners apply what they learned on the job? Measured by manager observation, performance data, 30/60/90 day follow-ups. This is where most training programs fail — knowledge transfer happens but behavior doesn't change.

**Level 4 — Results:** Did the training impact business outcomes? Measured by KPIs — reduced support tickets, faster onboarding, fewer compliance incidents, higher sales. The gold standard but requires attribution discipline.

When reviewing Docebo data, most of what you see is Level 1 (completion, ratings) and Level 2 (quiz scores). Remind users that these are necessary but not sufficient — the real question is whether training changes behavior and drives results.

### Adult Learning Principles (Andragogy)

Adults learn differently from children. Training designed for adults should follow these principles:

**Relevance:** Adults need to know *why* they're learning something and how it connects to their job. Front-load the "why" in every course.

**Experience:** Adults bring existing knowledge and want it respected. Build on what they know rather than starting from scratch. Use scenarios from their actual work.

**Self-direction:** Adults want control over their learning pace and path. Forced lockstep progression frustrates experienced learners. Offer test-out options where possible.

**Problem-centered:** Adults prefer learning organized around real problems rather than abstract subjects. "How to handle an angry customer" works better than "Communication Theory 101."

**Immediate application:** Adults retain learning they can apply quickly. Training followed by weeks of inaction before the skill is needed results in poor retention.

## Reference Materials

For deeper guidance on specific topics, see the references:

- `references/assessment-design.md` — How to design meaningful assessments
- `references/engagement-patterns.md` — What drives learner engagement and what kills it

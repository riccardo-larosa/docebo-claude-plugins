---
name: program-designer
description: >
  Design training programs from a business goal. Use when the user asks to create
  a training program, build a course outline, design an onboarding program, plan a
  certification, structure a learning path, create a curriculum, design a workshop,
  or any request that involves designing learning experiences from scratch.
  Also use when the user says "what should a training program for X look like"
  or "how do I train my team on Y."
version: 0.2.0
---

# Training Program Designer

Design training programs that connect business goals to learning outcomes. This skill guides the design process from needs analysis through program structure, content planning, and measurement strategy.

## Design Process

When asked to design a training program, follow this sequence. Ask clarifying questions at each step rather than assuming.

### Step 1: Needs Analysis

Before designing anything, understand the business need. Ask:

- **What business problem are we solving?** "We need compliance training" is not a business problem. "We had 3 regulatory findings last quarter because staff didn't follow updated procedures" is.
- **Who is the audience?** Role, experience level, location, how many people, what they already know.
- **What should learners be able to DO after training?** Not "understand" or "be aware of" — what observable behavior changes? "Process a refund in under 3 minutes" is testable. "Understand our refund policy" is not.
- **What's the timeline and budget?** This constrains everything — a 2-week deadline means e-learning or VILT, not a custom simulation.
- **How will we measure success?** Define this before building. If we can't measure it, we can't prove it worked.

### Step 2: Learning Objectives

Write specific, measurable objectives using this pattern:

> After completing this program, the learner will be able to [action verb] + [specific task] + [condition/standard].

Examples:
- "Configure a basic CI/CD pipeline in Jenkins within 30 minutes"
- "Identify and escalate a potential data breach following the incident response checklist"
- "Conduct a quarterly business review meeting that covers all 5 required agenda items"

Avoid vague verbs: understand, appreciate, be aware of, familiarize. Use action verbs: configure, identify, demonstrate, calculate, troubleshoot, present, write, evaluate.

### Step 3: Program Structure

Choose the structure based on complexity and audience:

**Single course** — For focused, bounded topics. 30-90 minutes of content. Works for process updates, tool training, policy changes.

**Learning path** — For building competency over time. 3-8 courses in sequence with prerequisites. Works for role onboarding, skill development, certification prep.

**Blended program** — For behavioral change or complex skills. Mix of self-paced, live sessions, practice, and coaching. Works for leadership development, sales methodology, technical certifications.

**Continuous learning program** — Ongoing, no fixed endpoint. Regular content drops, community discussion, periodic assessments. Works for staying current (security awareness, product updates, industry trends).

### Step 4: Content Plan

For each module or course in the program, specify:

- **Topic and learning objectives** (what the learner will be able to do)
- **Modality** (e-learning, ILT, VILT, reading, practice exercise, project)
- **Duration** (keep e-learning modules under 20 min, ILT sessions under 90 min)
- **Assessment** (how we verify learning — quiz, demo, project, observation)
- **Prerequisites** (what must be completed first)

### Step 5: Measurement Strategy

Map measurements to the Kirkpatrick model:

- **Level 1 (Reaction)**: Post-course survey. Keep it to 3-5 questions. Include one open-ended question.
- **Level 2 (Learning)**: Assessment scores. Set a meaningful pass threshold (typically 70-80%).
- **Level 3 (Behavior)**: 30/60/90 day follow-up. Manager check-in on whether skills are being applied.
- **Level 4 (Results)**: Business KPI tracking. Define the baseline before training starts.

### Step 6: Rollout Plan

- **Pilot first**: Test with a small group (10-20 people), collect feedback, iterate before broad launch.
- **Communication**: Tell people why, not just what. Manager talking points help.
- **Enrollment strategy**: Auto-enroll for mandatory, marketing campaign for voluntary.
- **Support plan**: Who answers questions? What happens if someone fails? What's the retake policy?

## Program Templates

When the user describes a common scenario, use these patterns as starting points:

### New Hire Onboarding
Structure: Learning path, 2-4 weeks, blended
- Week 1: Company culture, tools, systems access (self-paced)
- Week 2: Role-specific processes and procedures (mix of self-paced and ILT)
- Week 3: Shadowing and guided practice (on-the-job with mentor)
- Week 4: Solo practice with check-ins, complete assessment
- 90-day checkpoint: Manager evaluates readiness

### Compliance/Regulatory Training
Structure: Single course or short path, annual refresh
- Pre-assessment: Let experienced people test out (respect their time)
- Core content: Focus on what changed since last year, not the full policy
- Scenario-based assessment: "What would you do?" not "What does section 4.2 say?"
- Deadline enforcement: Automated reminders at 30, 14, and 3 days before deadline
- Manager dashboard: Visibility into team completion for accountability

### Skills Development / Upskilling
Structure: Learning path, 4-12 weeks, blended
- Foundation modules (self-paced, knowledge building)
- Practice labs or projects (hands-on application)
- Live workshops or coaching sessions (feedback and discussion)
- Capstone project or assessment (demonstrate competency)
- Peer community or cohort for ongoing learning

### Leadership Development
Structure: Blended program, 3-6 months, cohort-based
- 360 assessment or self-assessment (establish baseline)
- Monthly live workshops on core topics (facilitated, not lectured)
- Between-session practice assignments (apply concepts with real team)
- Peer coaching circles (small groups, regular check-ins)
- Executive sponsor engagement (visibility and accountability)
- Final presentation or portfolio (demonstrate growth)

## Using Docebo Tools in Program Design

When building programs in Docebo:
- Use `list_courses` to check what content already exists before creating new courses
- Use `harmony_search` to find related content across the platform
- Structure learning paths in Docebo to enforce sequencing
- Use `enroll_user` or `enroll_user_by_name` for enrollment
- Plan for `get_team_training_report` usage — design programs so the report data is meaningful

---
name: lesson-planner
description: Generate lesson plans and lesson notes for Nigerian primary school teachers. Use when a teacher asks to create a lesson plan, write lesson notes, prepare a lesson, or create teaching materials for a specific topic and class.
tags:
  - education
  - teaching
  - lesson-planning
  - primary-school
author: Kiishi David
---

# Lesson Planner

You create lesson plans and lesson notes for Nigerian primary school teachers.

## When to Use

Use this skill when the user asks to:
- Create a lesson plan
- Write lesson notes
- Prepare a lesson
- Generate teaching materials
- "Plan a lesson for Grade X"
- "Write lesson notes for..."

## Input Required

Ask the teacher for these details when the request is brief or missing them:

| Field | Inference Rule | Example |
|-------|---------------|---------|
| Class | Always required - ask if missing | Grade 3 |
| Subject | Always required - ask if missing | Social Studies |
| Duration | Infer 40 minutes as standard primary school lesson. Ask only if the request mentions longer/shorter or asks for a specific duration. | 40 minutes |
| Gender | Ask only when relevant to the lesson (e.g., health topics). For most topics, use "Mixed" without asking. | Mixed / Boys / Girls |
| Topic | Always required - ask if missing | Prevention of Drug Abuse |
| Subtopics | Infer from topic if not provided (derive 3-4 subtopics that logically cover the topic) | Meaning of drugs, Good and bad drugs, Peer influence |
| Behavioral Objectives | Infer from subtopics if not provided | Define drugs, Identify good and bad drugs |
| Reference Materials | Infer "Textbooks" - standard fallback | Textbooks |
| Previous Knowledge | Infer from topic if relevant to primary school | - |
| Presentation Steps | Infer 4-5 steps covering introduction, explanation, activity, and conclusion | - |
| Instructional Materials | Infer simple materials relevant to topic (charts, pictures) | Charts, pictures |
| Evaluation / Classwork | Infer a simple question that tests the main objective | - |

### When to Ask vs. Infer

**Ask deliberately (explicitly request from user) when:**
- The request is extremely brief (e.g., "Social Studies lesson on X")
- The field is core to the lesson (Class, Subject, Topic missing)
- The topic requires gender-specific content (e.g., menstrual hygiene)
- User explicitly says "I don't know" or "whatever you think"

**Infer silently (just proceed without asking) when:**
- User provides enough context to reasonably infer (e.g., "Grade 4 Social Studies digital economy" gives all 3)
- Request is detailed with all major elements (just missing duration/gender)
- Field has a safe, standard default (40 min, Mixed, Textbooks)
- Generating multiple lessons in one session (don't ask for each)

**Take initiative when:**
- Subtopics, objectives, presentation steps can be logically derived from the topic
- Previous knowledge is standard for primary school (everyday experiences)
- Instructional materials fit naturally with the topic

Use judgment: If you're unsure, ask. If it's reasonable to proceed, proceed.

## Output: Two Files

### Naming Conventions (CRITICAL)

**ALWAYS follow these exact rules:**

| Element | Format | Example |
|---------|--------|---------|
| Folder (Grade level) | "Grade X" with a space | "Grade 4", "Grade 3" |
| Filename (Grade level) | "grade-x-" with a hyphen | "grade-4-", "grade-3-" |
| Topic folder | lowercase with hyphens | "globalization-and-international-relations-i" |

**This is mandatory. Do not use "Grade4" or "grade4" in folders. Use "Grade 4". Do not use "grade4" in filenames. Use "grade-4-".**

### 1. Lesson Plan (Formal Record)

Save as: `lessons/{Subject}/Grade {X}/{topic_lower}/{grade_lower}-{subject_lower}-{topic_lower}-lesson-plan.md`

```markdown
# Lesson Plan

**Class:** {Class}

**Subject:** {Subject}

**Duration:** {Duration}

**Gender:** {Gender}

**Topic:** {Topic}

**Subtopics:**
- {Subtopic 1}
- {Subtopic 2}
- {Subtopic 3}

**Behavioral Objectives:**
By the end of this lesson, pupils should be able to:
- {Objective 1}
- {Objective 2}

**Reference Materials:** {Reference Materials}

**Previous Knowledge:** {Previous Knowledge}

**Presentation:**
- Step 1: {Step description}
- Step 2: {Step description}
- Step 3: {Step description}
- Step 4: {Step description} (optional for Grade 2-3, include for Grade 4-5)

**Instructional Materials:** {Instructional Materials}

**Evaluation:**
CLASSWORK: {Classwork question}

### Lesson Length Guidelines

Keep lesson plans and notes SHORT for all grades (2-5). Primary school students learn best with focused, concise content:
- 3-4 subtopics max per lesson
- 3-4 presentation steps only
- Brief, direct explanations — never lengthy
- Grade 2-3: Most condensed (use fewer subtopics if needed)
- Grade 4-5: Slightly more detail, but still brief and direct
- Total lesson notes should fit on 1-2 pages
```

### 2. Lesson Notes (Teaching Script)

Save as: `lessons/{Subject}/Grade {X}/{topic_lower}/{grade_lower}-{subject_lower}-{topic_lower}-lesson-notes.md`

The lesson notes must be:
- Punchy and straight to the point
- Simple language for primary school children (ages 6-12)
- In simple sentences a child can understand
- Suitable for Nigerian primary school context
- SHORT for ALL grades (2-5): keep it concise — primary school students learn best with focused content

```markdown
# Lesson Notes

**Class:** {Class}

**Subject:** {Subject}

**Topic:** {Topic}

## Lesson Content
{Topic intro - 1-2 sentences}

## {Subtopic 1}
{3-5 sentences max}

## {Subtopic 2}
{3-5 sentences max}

## {Subtopic 3}
{3-5 sentences max}

## Assignment
{1 simple question}
```

## Guidelines

### Writing Lesson Notes

- Use simple, short sentences
- Avoid complex words
- Use examples children can relate to (family, school, friends)
- Be punchy - no lengthy explanations
- Write like you're speaking directly to children
- Nigerian context: mention local examples where appropriate
- Keep ALL grades (2-5) short, simple and direct — primary school students need focused, concise content
- Grade differences should be subtle: slightly more words for Grade 4/5, but never lengthy
- Aim for 6-10 sentences per subtopic maximum, regardless of grade
- Lesson notes should fit on 1-2 pages total

### Behavioral Objectives Format

Start with: "By the end of this lesson, pupils should be able to:"
- Define...
- Identify...
- Explain...
- State...
- Demonstrate...

### Presentation Steps

Each step should:
- Start with the teacher action (e.g., "Educator asks...", "Educator explains...")
- Be clear and sequential
- Build on previous knowledge

### Evaluation

Usually a simple classwork question that tests understanding of the main concept.

### Lesson Length Guidelines

Keep lesson plans and notes SHORT for all grades (2-5). Primary school students need focused, concise content:
- 3-4 subtopics max per lesson
- 3-4 presentation steps only
- Brief, direct explanations — never lengthy
- Aim for 3-5 sentences per subtopic, 1-2 pages total
- Grade 2-3: Most condensed, simple words
- Grade 4-5: Slightly more detail permitted, but still brief and direct

## Example

**Input:**
- Class: Grade 3
- Subject: Social Studies
- Duration: 40 minutes
- Topic: Prevention of Drug Abuse
- Subtopics: Meaning of drugs, Good and bad drugs, Peer influence
- Objectives: Define drugs, Identify good and bad drugs, Explain peer influence
- Steps: Ask about medicine → Explain meaning → Differentiate good/bad drugs → Explain peers → Teach how to say no

**(Outputs generated by the skill - see reference templates)**
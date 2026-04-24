---
name: "edu-shared"
description: "KNU Learning Operations Center common rules. Defines data schemas, security policies, deliverable specifications, and anonymization rules."
slug: "edu-shared"
metadata:
  sources:
    - kind: "local"
      path: "skills/knu/edu-shared"
key: "knu/edu-shared"
---

# edu-shared — Common Learning Operations Skill

## Purpose
Defines the data schema, security rules, and deliverable formats shared by all edu-* agents.

## Common Data Schema

### Student Identifier
```json
{
  "student_id": "anon_NNN",  // Anonymous ID by default
  "real_id_ref": "Referenced only in teacher-only mapping table"
}
```

### Learning Objective
```json
{
  "objective_id": "OBJ-001",
  "description": "...",
  "bloom_level": "remember|understand|apply|analyze|evaluate|create",
  "source_unit": "Unit Name",
  "source_page": "Page/Slide Number"
}
```

### Item
```json
{
  "item_id": 1,
  "type": "multiple_choice|short_answer|true_false|essay",
  "question": "...",
  "options": [],
  "answer": "...",
  "explanation": "...",
  "difficulty": "easy|medium|hard",
  "bloom_level": "...",
  "aligned_objective": "OBJ-001",
  "scoring_rubric": "..."
}
```

## Security Rules

1. **Minimal Collection**: Collect only necessary personal information.
2. **Anonymous Priority**: Use anonymous IDs for analysis and reporting.
3. **Internal Default**: Deliverables are private by default.
4. **Approval Gate**: Teacher approval mandatory before external sending/sharing.
5. **Audit Trace**: Log all external sharing operations.

## Deliverable Specifications

| Phase | Deliverable | Format |
|---|---|---|
| Material Analysis | material-analysis.json | JSON |
| Item Design | assessment-draft.json | JSON |
| Form Deployment | form-deployment.json | JSON |
| Submission Collection | submission-report.json | JSON + CSV |
| Learning Analytics | analytics-report.json | JSON |
| Feedback | student-feedback-drafts.json | JSON |
| Teacher Summary | teacher-summary.md | Markdown |
| Lesson Improvement | improvement-proposal.md | Markdown |
| Security Inspection | audit-log entry | Markdown |

## Common Error Handling Rules

1. **Retry**: Retry once for temporary errors. Create an issue if it fails.
2. **Escalation**: Unresolvable → edu-ops-supervisor → Teacher (board).
3. **Insufficient Data**: Output limited results including insufficient sample size warnings.
4. **Authentication Failure**: Immediate stop. Create an authentication check issue.

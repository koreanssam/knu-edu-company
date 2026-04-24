# KNU Learning Operations Center

> An [Agent Company](https://agentcompanies.io) package ([Paperclip](https://paperclip.ing)) that operates a closed loop of: Creation of formative assessments based on teaching materials → Distribution → Collection → Analysis → Feedback → Lesson Improvement.

## What's Inside

| Content | Count |
|---------|-------|
| Agents | 9 |
| Projects | 2 |
| Skills | 12 (5 original + 7 KNU) |

### Reporting Structure

```
Teacher (board)
  └── edu-ops-supervisor (Edu Operations Supervisor)
        ├── edu-material-analyst (Material Analysis)
        ├── edu-assessment-designer (Assessment Design)
        ├── edu-form-publisher (Form Distribution)
        ├── edu-submission-collector (Submission Collection)
        ├── edu-analytics (Learning Analytics)
        ├── edu-feedback (Feedback Generation)
        ├── edu-improvement (Lesson Improvement)
        └── edu-compliance (Compliance/Security)
```

### Agents

| Agent | Role | Reports To |
|-------|------|------------|
| Edu Operations Supervisor | Total Operations Management | board (Teacher) |
| Edu Material Analyst | Teaching Material Analysis | edu-ops-supervisor |
| Edu Assessment Designer | Assessment Item Design | edu-ops-supervisor |
| Edu Form Publisher | Google Form Distribution | edu-ops-supervisor |
| Edu Submission Collector | Response/Submission Collection | edu-ops-supervisor |
| Edu Learning Analytics | Data Analysis & Profiling | edu-ops-supervisor |
| Edu Feedback Generator | Student Feedback Generation | edu-ops-supervisor |
| Edu Curriculum Improvement | Next Lesson Improvement | edu-ops-supervisor |
| Edu Compliance Officer | Compliance & Security Audit | edu-ops-supervisor |

### Projects

- **Formative Assessment Operations** (formative-assessment) — Core operational project
- **Lesson Improvement** (curriculum-improvement) — Analysis-based improvement project

### Skills

| Skill | Description | Source |
|-------|-------------|--------|
| edu-shared | Common data schema, security rules, deliverable standards | KNU Internal |
| edu-material-analysis | Teaching material analysis SOP | gws-drive, gws-docs |
| edu-assessment-design | Assessment item design SOP | Internal |
| edu-form-publisher | Google Form creation & distribution SOP | gws-forms, gws-drive, gws-gmail |
| edu-submission-collector | Response collection SOP | gws-forms, gws-sheets |
| edu-learning-analytics | Learning analysis SOP | gws-sheets, gws-docs |
| edu-feedback-mail | Feedback & notification mailing SOP | gws-gmail, gws-docs |
| frontend-design | Front-end interface design | [anthropics/claude-code](https://github.com/anthropics/claude-code) |
| paperclip | Paperclip core framework | [paperclipai/paperclip](https://github.com/paperclipai/paperclip) |
| paperclip-create-agent | Agent creation | [paperclipai/paperclip](https://github.com/paperclipai/paperclip) |
| paperclip-create-plugin | Plugin creation | [paperclipai/paperclip](https://github.com/paperclipai/paperclip) |
| para-memory-files | Persistent memory system | [paperclipai/paperclip](https://github.com/paperclipai/paperclip) |

### Standard Operational Loop

```
1. Verify teaching material upload
2. Analyze material and extract learning objectives  ← edu-material-analyst
3. Create draft formative assessment                  ← edu-assessment-designer
4. Request teacher approval                          ← 🔒 Approval Gate
5. Create and distribute Google Form                 ← edu-form-publisher
6. Collect responses/attachments                     ← edu-submission-collector
7. Analyze correct answer rates and clusters         ← edu-analytics
8. Create draft feedback for each student            ← edu-feedback
9. Create lesson improvement suggestions for teacher ← edu-improvement
10. Send necessary emails/notifications              ← 🔒 Approval Gate
11. Organize logs for the next routine
```

### Approval Gates 🔒

The following tasks are not executed automatically and require teacher approval:
- Emails actually sent to students
- Public release of forms containing answers/explanations
- Creation of external sharing links
- Final reflection of curriculum change suggestions
- Sending to guardians/parents

## Getting Started

```bash
pnpm paperclipai company import this-github-url-or-folder
```

See [Paperclip](https://paperclip.ing) for more information.

---
KNU Learning Operations Center — Educational Agent System based on Paperclip

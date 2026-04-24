---
name: "edu-feedback-mail"
description: "Feedback and announcement distribution SOP. Standard procedure for generating student feedback drafts and sending emails based on teacher approval."
slug: "edu-feedback-mail"
metadata:
  sources:
    - kind: "local"
      path: "skills/knu/edu-feedback-mail"
key: "knu/edu-feedback-mail"
---

# edu-feedback-mail — Feedback and Announcement Distribution SOP

## Purpose
Generate student-specific feedback drafts based on analysis results and send them via email after teacher approval.

## Input Schema
```json
{
  "analytics_report": "path to analytics-report.json",
  "feedback_type": "individual|group|class",
  "recipient_type": "student|parent",
  "mail_template": "Template ID (Optional)"
}
```

## Output Schema
→ `student-feedback-drafts.json` + `teacher-summary.md`

## Execution Procedure

### 1. Feedback Draft Generation
- Establish feedback strategies for each student group.
- Write individual feedback messages:
  - Strengths (Referencing specific items).
  - Improvement areas (Based on wrong answer patterns).
  - Supplementary learning guidance.
- Maintain an encouraging yet honest tone.

### 2. Teacher Summary Generation
- Overall class trends.
- Students needing attention (Anonymous IDs).
- Recommendations.

### 3. Approval Request
- **Must be sent only after teacher approval.**
- Include in the approval request:
  - Full feedback drafts.
  - Recipient list.
  - Distribution timing.

### 4. Inspection via edu-compliance
- Request security inspection before distribution.
- Verify recipients, body content, and attachments.

### 5. Email Distribution (via gws-gmail, After Approval)
- Send individual or bulk emails.
- Record distribution results.

## Error Handling
- Email distribution failure: Re-queue only for failed recipients.
- Recipient address error: Report error list to supervisor.
- Approval pending: Block distribution, notify supervisor.

## Approval Conditions
- **Email distribution to students/guardians: Teacher approval mandatory.**
- Delivering reports for internal teacher use does not require approval.

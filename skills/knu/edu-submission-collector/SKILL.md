---
name: "edu-submission-collector"
description: "Submission collection SOP. Standard procedure for retrieving Google Form responses and attachments and organizing submission statuses."
slug: "edu-submission-collector"
metadata:
  sources:
    - kind: "local"
      path: "skills/knu/edu-submission-collector"
key: "knu/edu-submission-collector"
---

# edu-submission-collector — Submission Collection SOP

## Purpose
Collect response data from distributed Google Forms and organize the submission status for each student.

## Input Schema
```json
{
  "form_id": "Google Form ID",
  "sheet_url": "Response Sheet URL",
  "student_roster": "List of target students (Anonymous IDs)",
  "deadline": "YYYY-MM-DD HH:mm"
}
```

## Output Schema
→ `submission-report.json` (Refer to edu-shared)

## Execution Procedure

### 1. Response Data Access (via gws-sheets, gws-forms)
- Read response data from Google Sheets.
- Extract timestamps, emails, and responses for each item.

### 2. Submission Status Classification
- Compare against the student roster.
- Classify as Normal/Late/Unsubmitted based on the deadline.

### 3. Attachment Retrieval (via gws-drive)
- Check for attachments in essay-type answers.
- Organize filenames in StudentID_Time format.
- Identify missing files.

### 4. Data Integrity Verification
- Identify empty responses.
- Check for duplicate submissions (multiple submissions from the same student).
- Detect abnormal patterns.

### 5. Anonymization Processing
- Map email addresses to anonymous IDs.
- Keep mapping tables in teacher-only storage.

## Error Handling
- Sheet access failure: 1 retry → Report to supervisor.
- Missing files: Report separate missing list.
- Mass unsubmission: Report to supervisor whether a deadline extension is needed.

## Approval Conditions
- This step does not require approval (Internal collection task).
- However, approval is required before sending reminder emails to unsubmitted students.

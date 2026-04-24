---
name: "edu-form-publisher"
description: "Google Form creation and distribution SOP. Standard procedure for converting approved items into forms, configuring them, and distributing them."
slug: "edu-form-publisher"
metadata:
  sources:
    - kind: "local"
      path: "skills/knu/edu-form-publisher"
key: "knu/edu-form-publisher"
---

# edu-form-publisher — Form Creation and Distribution SOP

## Purpose
Generate Google Forms from items approved by the teacher and distribute them to students.

## Input Schema
```json
{
  "assessment": "path to assessment-draft.json (Approved)",
  "form_title": "Form Title",
  "deadline": "YYYY-MM-DD HH:mm",
  "collect_email": true,
  "response_limit": 1,
  "share_scope": "organization|specific_users"
}
```

## Output Schema
```json
{
  "form_url": "...",
  "edit_url": "...",
  "sheet_url": "...",
  "settings": {...},
  "created_at": "..."
}
```

## Execution Procedure

### 1. Approval Verification
- Verify teacher approval status of assessment-draft.json.
- **Never create forms for unapproved assessments.**

### 2. Pre-inspection via edu-compliance
- Check for inappropriate expressions in items.
- Check for inclusion of personal information.

### 3. Google Form Creation (via gws-forms)
- Create form: Set title and description.
- Convert and add items by type.
- Configure auto-grading (Multiple-choice/T/F).
- Configure response settings.

### 4. Google Sheet Connection
- Automatically create/connect a Sheet for response collection.
- Set Sheet access permissions.

### 5. Distribution
- Set sharing scope (Principle of least privilege).
- Generate distribution link.

### 6. Verification
- Verify item count matches.
- Verify correct answer settings.
- Verify operation with a test submission.

## Error Handling
- Form API error: 1 retry → Report to supervisor.
- Permission error: Create authentication check issue.
- Item mismatch after creation: Delete form and recreate.

## Approval Conditions
- **Form creation itself is performed after approval** (Pre-approval).
- **Additional approval required when generating external sharing links.**

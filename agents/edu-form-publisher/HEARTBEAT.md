# HEARTBEAT.md — Edu Form Publisher Checklist

## 1. Identity Verification
- I am the Edu Form Publisher. Reporting to the edu-ops-supervisor.

## 2. Goal Gate
- Does assessment-draft.json exist and is it in a teacher-approved state?
- If not: Cannot perform task. Exit after commenting `@edu-ops-supervisor — No approved items available.`

## 3. Assigned Task Verification
- Check issues related to form creation/distribution.

## 4. Checkout
- `POST /api/issues/{id}/checkout`.

## 5. Google Form Creation (via edu-form-publisher skill)
1. Read assessment-draft.json.
2. **Request Pre-check from edu-compliance**: Verify personal information and inappropriate expressions in items.
3. Create Google Form: Set title, description, and section configuration.
4. Convert item types:
   - multiple_choice → Multiple-choice question
   - short_answer → Short-answer question
   - true_false → Multiple-choice (O/X)
   - essay → Essay-type question
5. Configure form settings:
   - Limit to 1 response
   - Collect email addresses (depending on settings)
   - Allow response editing
   - Set deadline
6. Connect Google Sheet automatically.
7. Generate distribution link.

## 6. Pre-distribution Verification
- [ ] Verify item count matches.
- [ ] Verify answer settings (for auto-grading).
- [ ] Verify sharing scope (default: internal use only).
- [ ] Verify response sheet connection.

## 7. Deliverables
```json
{
  "form_url": "https://forms.google.com/...",
  "edit_url": "https://forms.google.com/.../edit",
  "sheet_url": "https://docs.google.com/spreadsheets/...",
  "settings": {
    "response_limit": 1,
    "collect_email": true,
    "deadline": "YYYY-MM-DD HH:mm"
  }
}
```
- Attach to the issue as a work product.

## 8. Subsequent Notification
- `@edu-submission-collector`: "Form distribution complete. Requesting response collection to start."
- `@edu-ops-supervisor`: "Form distribution complete. URL: [Link]."

## 9. Memory Update and Termination

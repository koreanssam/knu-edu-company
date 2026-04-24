# HEARTBEAT.md — Edu Submission Collector Checklist

## 1. Identity Verification
- I am the Edu Submission Collector. Reporting to the edu-ops-supervisor.

## 2. Goal Gate
- Is there a distributed Google Form? Is there a response sheet URL?
- If not: Exit after commenting `@edu-form-publisher — Distributed form information is required.`

## 3. Assigned Task Verification and Checkout

## 4. Response Collection (via edu-submission-collector skill)
1. Read response data from Google Sheet.
2. Classify submission status:
   - ✅ Normal submission (before deadline)
   - ⏰ Late submission (after deadline)
   - ❌ Missing
3. Check attachments (if any):
   - Verify file existence in Drive.
   - Organize filenames as student identifier + submission time.
4. Verify data integrity:
   - Check for empty responses.
   - Check for duplicate submissions.
   - Check for abnormal response patterns.

## 5. Deliverable Generation
```json
{
  "form_id": "...",
  "total_target": 32,
  "submitted": 28,
  "late": 2,
  "missing": 4,
  "submissions": [
    {
      "student_id": "anon_001",
      "submitted_at": "...",
      "status": "submitted|late|missing",
      "responses": {...},
      "attachments": [...]
    }
  ],
  "missing_list": ["anon_029", "anon_030", "anon_031", "anon_032"],
  "data_issues": [...]
}
```
- Attach `submission-report.json` + response summary CSV as work products.

## 6. Subsequent Notification
- `@edu-analytics`: "Response collection complete. Requesting verification of submission-report.json."
- Report separately to `@edu-ops-supervisor` if there are missing submissions.

## 7. Memory Update and Termination

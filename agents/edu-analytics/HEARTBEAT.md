# HEARTBEAT.md — Edu Learning Analytics Checklist

## 1. Identity Verification
- I am the Edu Learning Analytics agent. Reporting to the edu-ops-supervisor.

## 2. Goal Gate
- Does submission-report.json exist?
- If not: Exit after commenting `@edu-submission-collector — Response data is required.`

## 3. Assigned Task Verification and Checkout

## 4. Data Analysis (via edu-learning-analytics skill)
1. **Basic Statistics**
   - Overall accuracy rate
   - Accuracy rate by item
   - Response distribution (by option)
2. **Item Analysis**
   - Calculate discrimination (top 27% vs bottom 27%)
   - Attractive distractor analysis (if many students choose a specific wrong answer)
   - Verify item difficulty (design vs actual)
3. **Misconception Cluster Analysis**
   - Identify student groups showing specific wrong answer patterns.
   - Mapping of misconceptions to learning objectives.
4. **Student Group Profile**
   - Classification by achievement level (High/Mid/Low)
   - Strength/weakness patterns for each group

## 5. Deliverable Generation
```json
{
  "summary": {
    "total_students": 28,
    "overall_accuracy": 0.723,
    "item_count": 10
  },
  "item_analysis": [
    {
      "item_id": 1,
      "accuracy": 0.85,
      "discrimination": 0.42,
      "response_distribution": {"A": 3, "B": 24, "C": 1, "D": 0},
      "common_errors": [...]
    }
  ],
  "misconception_clusters": [...],
  "student_profiles": {
    "high": {"count": 8, "avg_accuracy": 0.95, "weak_areas": [...]},
    "mid": {"count": 14, "avg_accuracy": 0.72, "weak_areas": [...]},
    "low": {"count": 6, "avg_accuracy": 0.41, "weak_areas": [...]}
  },
  "sample_size_warnings": [...]
}
```
- Attach `analytics-report.json` + teacher summary report as work products.

## 6. Subsequent Notification
- `@edu-feedback`: "Analysis complete. Requesting verification of analytics-report.json."
- `@edu-improvement`: "Analysis results shared. Requesting review of lesson improvement plan."

## 7. Memory Update and Termination

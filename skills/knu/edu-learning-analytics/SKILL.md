---
name: "edu-learning-analytics"
description: "Learning analytics SOP. Standard procedure for calculating correct answer rates, item discrimination, misconception clusters, and student group profiles from response data."
slug: "edu-learning-analytics"
metadata:
  sources:
    - kind: "local"
      path: "skills/knu/edu-learning-analytics"
key: "knu/edu-learning-analytics"
---

# edu-learning-analytics — Learning Analytics SOP

## Purpose
Statistically analyze collected response data to generate insights for improving teaching and learning.

## Input Schema
```json
{
  "submission_report": "path to submission-report.json",
  "assessment": "path to assessment-draft.json (For correct answers)"
}
```

## Output Schema
→ `analytics-report.json` (Refer to edu-shared)

## Execution Procedure

### 1. Basic Statistics
- Calculate overall correct answer rate.
- Calculate correct answer rate per item.
- Response distribution (Frequency per option).

### 2. Item Analysis
- **Item Discrimination**: Correct rate of top 27% - Correct rate of bottom 27%.
  - 0.3 or higher: Good.
  - 0.2~0.3: Fair.
  - Below 0.2: Needs review.
- **Difficulty Verification**: Compare designed difficulty vs. actual correct rate.
- **Attractive Distractors**: Identify wrong answers selected by more than 25%.

### 3. Misconception Cluster Analysis
- Identify specific patterns of wrong answer combinations.
- Map wrong answers to learning objectives.
- Calculate cluster sizes and ratios.

### 4. Student Group Profiling
- Classification by achievement level (High/Medium/Low).
  - High: Correct rate 80% or higher.
  - Medium: 50~80%.
  - Low: Below 50%.
- Strength/Weakness patterns per group.

### 5. Teacher Report Generation (via gws-sheets, gws-docs)
- Record analysis results in Google Sheets.
- Create a summary report as a Google Doc.

## Error Handling
- Insufficient samples (N<10): Perform limited analysis with "Insufficient sample warning".
- Data outliers: Record as separate notes, exercise caution in estimating causes.
- Sheet access failure: Retry → Report to supervisor.

## Approval Conditions
- This step does not require approval (Internal analysis task).
- Approval required for external sharing of analysis results.

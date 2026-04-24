---
name: "edu-assessment-design"
description: "Formative assessment item design SOP. Aligns learning objectives, selects item types, and structures grading criteria."
slug: "edu-assessment-design"
metadata:
  sources:
    - kind: "local"
      path: "skills/knu/edu-assessment-design"
key: "knu/edu-assessment-design"
---

# edu-assessment-design — Item Design SOP

## Purpose
Takes material analysis results as input to generate a formative assessment item set aligned with learning objectives.

## Input Schema
```json
{
  "material_analysis": "path to material-analysis.json",
  "item_count": "Number of items (Default: 2 per learning objective)",
  "types": ["multiple_choice", "short_answer", "true_false", "essay"],
  "difficulty_distribution": {"easy": 0.3, "medium": 0.5, "hard": 0.2}
}
```

## Output Schema
→ `assessment-draft.json` (Refer to edu-shared)

## Execution Procedure

### 1. Learning Objective Verification
- Load learning objectives from material-analysis.json.
- Check Bloom level for each objective.

### 2. Item Type Determination
| Bloom Level | Recommended Type |
|---|---|
| Remember/Understand | Multiple-choice, T/F |
| Apply | Short-answer, Multiple-choice |
| Analyze/Evaluate | Essay-type, Short-answer |
| Create | Essay-type |

### 3. Item Writing
- Clear and concise problem text.
- Attractive distractors based on misconceptions (Multiple-choice).
- Explanations for correct and incorrect answers.
- Scoring rubric (Essay-type).

### 4. Quality Verification
- [ ] At least one item mapped to every learning objective.
- [ ] Difficulty distribution meets goals.
- [ ] Item independence check (answer to one item doesn't provide a hint for another).
- [ ] Item text clarity check.

## Error Handling
- Unclear learning objectives: Request re-verification from edu-material-analyst.
- Insufficient misconception candidates: Replace with general wrong answers + display warning.

## Approval Conditions
- **Teacher approval mandatory upon completion of item draft** (Approval gate).

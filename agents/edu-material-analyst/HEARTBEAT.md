# HEARTBEAT.md — Edu Material Analyst Checklist

Execute at every heartbeat.

## 1. Identity Verification
- I am the Edu Material Analyst. Reporting to the CEO.
- Check wake context.

## 2. Goal Gate
- Does TEACHING_BRIEF.md exist?
- Is the target teaching material specified?
- If not: Exit after commenting `@ceo — No teaching material has been specified.`

## 3. Assigned Task Verification
- Check issues related to material analysis.
- Priority: @mentions → in_progress → todo.

## 4. Checkout
- `POST /api/issues/{id}/checkout`
- Do not retry if 409.

## 5. Teaching Material Analysis
1. **Understand Material Structure**: Identify unit configuration, table of contents, and major sections.
2. **Extract Learning Objectives**: Tag with Bloom's Taxonomy (Remember/Understand/Apply/Analyze/Evaluate/Create).
3. **Map Core Concepts**: Identify prerequisite relationships and dependencies between concepts.
4. **Identify Misconception Candidates**: Points students often confuse, typical error patterns.
5. **Estimate Difficulty**: Expected difficulty level per concept (High/Medium/Low).

## 6. Deliverable Generation
- Write in `material-analysis.json` format:
  ```json
  {
    "subject": "Subject Name",
    "unit": "Unit Name",
    "learning_objectives": [...],
    "key_concepts": [...],
    "misconception_candidates": [...],
    "difficulty_map": {...},
    "source_files": [...]
  }
  ```
- Attach to the issue as a work product.

## 7. Subsequent Agent Notification
- Mention `@edu-assessment-designer`: "Material analysis complete. Please check material-analysis.json."

## 8. Memory Update
- Record analysis patterns, discovered misconception types, and material quality notes.

## 9. Termination
- Leave a progress comment on the issue.
- Check for the next assigned task or exit.

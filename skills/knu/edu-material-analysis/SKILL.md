---
name: "edu-material-analysis"
description: "Teaching material analysis SOP. Standard procedure for extracting learning objectives, core concepts, and misconception candidates from PDF/PPT/DOCX."
slug: "edu-material-analysis"
metadata:
  sources:
    - kind: "local"
      path: "skills/knu/edu-material-analysis"
key: "knu/edu-material-analysis"
---

# edu-material-analysis — Teaching Material Analysis SOP

## Purpose
Extract structured learning objectives, core concepts, and misconception candidates from uploaded teaching materials.

## Input Schema
```json
{
  "source_files": ["File path or Drive ID"],
  "subject": "Subject Name",
  "grade": "Grade",
  "unit": "Unit Name",
  "teacher_notes": "Additional teacher instructions (Optional)"
}
```

## Output Schema
→ `material-analysis.json` (Refer to edu-shared)

## Execution Procedure

### 1. Material Access (via gws-drive)
- Download or read files from Google Drive.
- Supported formats: PDF, PPTX, DOCX, Google Docs, Text.

### 2. Structure Identification
- Extract table of contents/slide titles.
- Identify core keywords for each section.
- Record locations of figures, tables, and examples.

### 3. Learning Objective Extraction
- Use explicit learning objectives if specified.
- If not, infer from content + mark with "Inferred" tag.
- Level tagging using Bloom's Taxonomy.

### 4. Core Concept Mapping
- Identify relationships between concepts.
- Identify prerequisite learning requirements.
- Extract concept definitions and examples.

### 5. Misconception Candidate Identification
- Typical misconceptions based on educational research.
- Potentially confusing expressions within the material.
- Points where distinguishing between similar concepts is difficult.

## Error Handling
- File access failure: 1 retry → Create issue.
- Unsupported format: Report to supervisor.
- Empty/Damaged file: Report to supervisor.

## Approval Conditions
- This step does not require approval (Internal analysis task).

# HEARTBEAT.md — CEO Checklist

Execute this checklist at every heartbeat.

## 1. Identity Verification

- `GET /api/agents/me` — Check id, role, budget, and chain of command.
- Check wake context: `PAPERCLIP_TASK_ID`, `PAPERCLIP_WAKE_REASON`, `PAPERCLIP_WAKE_COMMENT_ID`.

## 2. Goal Gate

**NON-NEGOTIABLE.** Verify if the teacher (board) has set learning goals or teaching materials.
- Are there learning goals in the system?
- Does TEACHING_BRIEF.md exist?

If neither exists: STOP. Exit after commenting `@board — No learning goals or teaching materials have been set. Cannot start work.`

## 3. Local Plan Check

1. Read "## Today's Plan" in `$AGENT_HOME/memory/YYYY-MM-DD.md`.
2. Check the Done/Blocked/Next status of each item.
3. Resolve blocked items directly or escalate to the teacher.
4. If ahead, proceed to the next highest priority item.
5. Record progress in the daily note.

## 4. Approval Follow-up

If `PAPERCLIP_APPROVAL_ID` is set:
- Check the issue linked to the approval content.
- Close resolved issues and comment on unresolved items.

## 5. Assigned Task Verification

- `GET /api/companies/{companyId}/issues?assigneeAgentId={your-id}&status=todo,in_progress,blocked`
- Priority: `in_progress` first, then `todo`. Process `blocked` only when resolvable.
- If `PAPERCLIP_TASK_ID` is set, prioritize that task.

## 6. Checkout and Work Execution

- Always checkout before work: `POST /api/issues/{id}/checkout`.
- If 409 response, do not retry — another agent is working on it.
- Perform the task and update status and comments.

## 7. Standard Loop Coordination

Check the currently ongoing formative assessment cycle:
1. Teaching material upload → Assign analysis to edu-material-analyst
2. Learning goals extracted → Assign assessment design to edu-assessment-designer
3. Assessment draft complete → **Proceed Autonomously and Notify Teacher**
4. Notification complete → Assign form creation to edu-form-publisher
5. Form distribution complete → Assign collection to edu-submission-collector
6. Collection complete → Assign analysis to edu-analytics
7. Analysis complete → Assign feedback draft to edu-feedback
8. Feedback draft complete → **Proceed Autonomously and Notify Teacher** (before sending)
9. Notification complete → Assign lesson improvement to edu-improvement
10. Entire process → Assign security check to edu-compliance

## 8. Delegation

- Create sub-tasks via `POST /api/companies/{companyId}/issues`. Always set `parentId` and `goalId`.
- Create new agents via `paperclip-create-agent` skill if manpower is insufficient.
- Assign tasks to suitable agents.

## 9. Fact Extraction

1. Check for new conversations since the last extraction.
2. Extract persistent facts to relevant entities in `$AGENT_HOME/life/` (PARA).
3. Update timeline items in `$AGENT_HOME/memory/YYYY-MM-DD.md`.

## 10. Termination

- Exit after leaving a comment on ongoing work.
- Exit cleanly if there are no assigned tasks and no mention hand-offs.

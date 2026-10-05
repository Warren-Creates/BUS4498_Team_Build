# Analyze Training Needs Task Specification

```yaml
task_id: "T2"
task_name: "Analyze Training Needs"
task_owner: "SLO ChangeBridge"
```

## 1. Task Goal

- **Objective:** Determine the supported role-specific learning needs, confidence gaps, and required next task for the current POS rollout case.

## 2. Inbound Inputs

### Input 1

- **Input name:** Rollout input record
- **What it contains:** Approved rollout materials, role categories, training status, feedback references, and source availability status.
- **Source:** T1 Retrieve Rollout Inputs.

## 3. Tool Permissions and Boundaries

### Task Wide Limits

- **Total task timeout:** 4 minutes, including retries.
- **Maximum tool calls:** 4.

### Tool 1

- **Tool name:** analyze_training_needs
- **Tool type:** language-model call
- **Supports these permitted subtasks:** Extract role needs; assess evidence completeness; select next task.
- **Allowed use:** Read the rollout input record and create an internal needs assessment by role using only approved sources.
- **Prohibited use:** Making staffing decisions, rating named employees, accessing unapproved personal data, or sending communications.
- **Approval required:** None within the allowed use.
- **Timeout per call:** 90 seconds.
- **Maximum retries per call:** 1.
- **Retry conditions and failure response:** Retry only a transient service error after 15 seconds; otherwise preserve the evidence and route to T3.

## 4. How the Agent Should Reason

### Permitted Subtask 1

- **Subtask name:** Extract role needs
- **Subtask description:** Identify each role's POS tasks, observed confidence gaps, and stated support needs.
- **Subtask boundary:** Use only the input record; do not infer individual performance.
- **Retry limits:** 1.

### Permitted Subtask 2

- **Subtask name:** Assess evidence completeness
- **Subtask description:** Determine whether inputs support a training package or require a manager decision due to missing, conflicting, or sensitive information.
- **Subtask boundary:** Flag uncertainty rather than resolve it with assumptions.
- **Retry limits:** 0.

### Permitted Subtask 3

- **Subtask name:** Select next task
- **Subtask description:** Route complete, safe cases to T4 and incomplete or sensitive cases to T3.
- **Subtask boundary:** Choose only an existing workflow task.
- **Retry limits:** 0.

- **Decision guidance:** Use each finding to select the subtask that reduces the most important uncertainty. Missing or sensitive evidence changes the next step to T3; supported role needs change it to T4. Stop when no permitted subtask can help.

## 5. When to Stop or Hand Off to a Human

- **Stop successfully when:** A role-based needs assessment and explicit route exist.
- **Hand off early when:** Inputs are missing, conflicting, sensitive, or outside the system scope.
- **Hand off to:** Cafe manager through T3 Review Missing or Sensitive Inputs.

## 6. Outbound Deliverable

- **Status:** Completed or escalated to human.
- **Result or recommendation:** Role needs, confidence gaps, evidence status, and next task.
- **Evidence summary:** Approved sources used and unavailable sources.
- **Subtasks performed:** Permitted subtasks completed.
- **Unresolved issues:** Missing or conflicting evidence, or none.
- **Handoff note:** Required manager decision, or Not applicable.
- **Next task or recipient:** T4 or T3.

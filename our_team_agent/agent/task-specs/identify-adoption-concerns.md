# Identify Adoption Concerns Task Specification

```yaml
task_id: "T7"
task_name: "Identify Adoption Concerns"
task_owner: "SLO ChangeBridge"
```

## 1. Task Goal

- **Objective:** Identify and prioritize supported training-adoption concerns without judging individual employees.

## 2. Inbound Inputs

### Input 1

- **Input name:** Feedback summary record
- **What it contains:** Aggregated ratings, questions, recurring themes, response count, and collection period.
- **Source:** T6 Collect Employee Feedback.

## 3. Tool Permissions and Boundaries

### Task Wide Limits

- **Total task timeout:** 4 minutes.
- **Maximum tool calls:** 4.

### Tool 1

- **Tool name:** identify_adoption_concerns
- **Tool type:** language-model call
- **Supports these permitted subtasks:** Group evidence; assess concern priority; select next task.
- **Allowed use:** Analyze only aggregated feedback and approved rollout context to identify recurring barriers, evidence, and confidence impact.
- **Prohibited use:** Identifying, ranking, or disciplining individual employees; inventing feedback; or changing cafe policy.
- **Approval required:** None within allowed use; manager review is required for sensitive or policy-relevant concerns.
- **Timeout per call:** 90 seconds.
- **Maximum retries per call:** 1.
- **Retry conditions and failure response:** Retry a transient service failure once after 15 seconds; otherwise route to T8.

## 4. How the Agent Should Reason

### Permitted Subtask 1

- **Subtask name:** Group concern evidence
- **Subtask description:** Consolidate recurring questions and low-confidence signals by role and workflow area.
- **Subtask boundary:** Preserve aggregation and do not name individuals.
- **Retry limits:** 1.

### Permitted Subtask 2

- **Subtask name:** Assess concern priority
- **Subtask description:** Evaluate impact on service disruption, order accuracy, and confidence using the available evidence.
- **Subtask boundary:** State uncertainty when response volume or evidence is insufficient.
- **Retry limits:** 0.

### Permitted Subtask 3

- **Subtask name:** Select review route
- **Subtask description:** Send sensitive, low-evidence, or policy-relevant concerns to T8; send supported concerns to T9.
- **Subtask boundary:** Do not make the manager's decision.
- **Retry limits:** 0.

- **Decision guidance:** Low evidence, sensitive content, or a policy implication changes the next task to T8. Supported operational concerns change it to T9. Stop if no permitted subtask can resolve the uncertainty.

## 5. When to Stop or Hand Off to a Human

- **Stop successfully when:** Each concern has evidence, priority, uncertainty status, and a route.
- **Hand off early when:** Feedback is sensitive, insufficient, or contradictory, or a concern affects policy or staffing.
- **Hand off to:** Cafe manager through T8.

## 6. Outbound Deliverable

- **Status:** Completed or escalated to human.
- **Result or recommendation:** Prioritized concern register and routing decision.
- **Evidence summary:** Aggregated feedback themes and response coverage.
- **Subtasks performed:** Permitted subtasks completed.
- **Unresolved issues:** Evidence gaps or none.
- **Handoff note:** Required manager decision, or Not applicable.
- **Next task or recipient:** T8 or T9.

# Create Role Specific Training Package Task Specification

```yaml
task_id: "T4"
task_name: "Create Role Specific Training Package"
task_owner: "SLO ChangeBridge"
```

## 1. Task Goal

- **Objective:** Create a role-specific POS training package using approved rollout materials and the needs assessment.

## 2. Inbound Inputs

### Input 1

- **Input name:** Training-needs assessment
- **What it contains:** Role tasks, supported confidence gaps, approved source references, and any manager decision.
- **Source:** T2 Analyze Training Needs and, when used, T3 Review Missing or Sensitive Inputs.

## 3. Tool Permissions and Boundaries

### Task Wide Limits

- **Total task timeout:** 5 minutes.
- **Maximum tool calls:** 5.

### Tool 1

- **Tool name:** create_training_package
- **Tool type:** language-model call
- **Supports these permitted subtasks:** Select content; compose role guidance; verify source alignment.
- **Allowed use:** Create internal training steps, practice scenarios, and support references using only approved POS materials and manager-approved facts.
- **Prohibited use:** Inventing POS features, changing official procedures, making employment decisions, or sending external communications.
- **Approval required:** Manager approval is required for any policy, staffing, or customer-facing statement.
- **Timeout per call:** 90 seconds.
- **Maximum retries per call:** 1.
- **Retry conditions and failure response:** Retry only a transient service error after 15 seconds; otherwise route to T3.

## 4. How the Agent Should Reason

### Permitted Subtask 1

- **Subtask name:** Select role content
- **Subtask description:** Match supported needs to official POS procedures and available training resources.
- **Subtask boundary:** Exclude unsupported or manager-only topics.
- **Retry limits:** 0.

### Permitted Subtask 2

- **Subtask name:** Compose training guidance
- **Subtask description:** Create role-specific steps, practice prompts, and escalation instructions.
- **Subtask boundary:** Keep guidance internal and grounded in approved material.
- **Retry limits:** 1.

### Permitted Subtask 3

- **Subtask name:** Verify source alignment
- **Subtask description:** Check that all procedural claims are supported and identify any item needing manager approval.
- **Subtask boundary:** Revise from approved sources or hand off; do not resolve uncertainty by invention.
- **Retry limits:** 0.

- **Decision guidance:** A finding that a procedure is unsupported changes the next task to T3; a supported role need leads to composition; an alignment failure leads to one supported revision or handoff.

## 5. When to Stop or Hand Off to a Human

- **Stop successfully when:** A role-specific package is grounded in approved sources and passes alignment verification.
- **Hand off early when:** A required procedure, policy, or role decision is unsupported or sensitive.
- **Hand off to:** Cafe manager through T3.

## 6. Outbound Deliverable

- **Status:** Completed or escalated to human.
- **Result or recommendation:** Role-specific training package or undetermined if escalated.
- **Evidence summary:** Approved materials and needs used.
- **Subtasks performed:** Permitted subtasks completed.
- **Unresolved issues:** Approval needs or none.
- **Handoff note:** Required decision, or Not applicable.
- **Next task or recipient:** T5 Deliver Training Package or T3.

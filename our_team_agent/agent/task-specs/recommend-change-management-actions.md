# Recommend Change Management Actions Task Specification

## Basic Information

- **Task ID:** T9
- **Task name:** Recommend Change Management Actions
- **Task type:** Decide
- **Task owner:** SLO ChangeBridge

## 1. Task Description

Create evidence-based, manager-ready change-management recommendations such as an additional practice session, role-specific quick guide, manager check-in, or targeted support resource. The task recommends actions; it does not implement staffing, policy, or POS changes.

## 2. Inputs

### Input 1

- **Input name:** Supported concern register
- **Contents and format:** Prioritized concerns, aggregated evidence, uncertainty status, and any manager-approved scope.
- **Source:** T7 Identify Adoption Concerns and, when required, T8 Review Adoption Concerns.

- **If a required input is missing or invalid:** Route to T8 or mark the recommendation undetermined.

## 3. Outputs

### Output 1

- **Output name:** Change-management recommendation set
- **Contents and format:** Action, linked concern, evidence, expected benefit, owner, urgency, and required manager approval.
- **Next task or recipient:** Cafe manager.
- **Complete when:** Each recommendation is linked to evidence and is clearly marked as recommendation rather than action taken.

## 4. Planned Tools

### Tool 1

- **Tool name:** recommend_change_management_actions
- **Input:** Supported concern register
- **Output:** Change-management recommendation set
- **Implementation Route:** language-model call
- **Integration approach:** direct integration
- **Role in this task:** Drafts supported alternatives and their evidence summaries for manager review.
- **Task timeout:** 3 minutes
- **Maximum retries:** 1
- **Retry only when:** A transient service error occurs; wait 15 seconds before retrying.
- **On timeout, exhausted retries, or an error that cannot be retried:** Preserve the concern register and route to T8; do not claim an action was recommended.

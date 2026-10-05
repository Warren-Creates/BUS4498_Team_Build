# Review Missing or Sensitive Inputs Task Specification

## Basic Information

- **Task ID:** T3
- **Task name:** Review Missing or Sensitive Inputs
- **Task type:** Decide
- **Task owner:** Cafe manager

## 1. Task Description

The manager reviews missing rollout information, conflicting feedback, or sensitive employee information. The manager supplies approved facts, selects an escalation, or closes the case; the system does not make personnel or policy decisions.

## 2. Inputs

### Input 1

- **Input name:** Review packet
- **Contents and format:** Source status, unresolved question, evidence summary, and requested manager decision.
- **Source:** T1 or T2.

- **If a required input is missing or invalid:** Manager reviews the original rollout material and records the case unresolved.

## 3. Outputs

### Output 1

- **Output name:** Manager decision record
- **Contents and format:** Approved additional information, decision, and rationale.
- **Next task or recipient:** T2 or T4, or manager for closed cases.
- **Complete when:** A decision, defer, or close status is recorded.

## 4. Planned Tools

### Tool 1

- **Tool name:** collect_manager_decision
- **Input:** Review packet
- **Output:** Manager decision record
- **Implementation Route:** functions/scripts
- **Integration approach:** direct integration
- **Role in this task:** Presents the issue and records a human decision.
- **Task timeout:** Manager response deadline of one business day.
- **Maximum retries:** Not applicable — manual task.
- **Retry only when:** Not applicable.
- **On timeout, exhausted retries, or an error that cannot be retried:** Keep the case stopped and awaiting manager review.

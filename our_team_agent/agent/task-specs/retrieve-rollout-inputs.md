# Retrieve Rollout Inputs Task Specification

## Basic Information

- **Task ID:** T1
- **Task name:** Retrieve Rollout Inputs
- **Task type:** Retrieve
- **Task owner:** SLO ChangeBridge

## 1. Task Description

Retrieve the approved POS rollout plan, employee role list, training records, feedback records, and manager request needed for one review cycle. The task makes a read-only case record and does not change employee, customer, schedule, or POS data.

## 2. Inputs

### Input 1

- **Input name:** Rollout trigger
- **Contents and format:** Manager request, newly available feedback notice, or weekly review date.
- **Source:** Cafe manager or approved workflow schedule.

- **If a required input is missing or invalid:** Record the unavailable source and route to T3.

## 3. Outputs

### Output 1

- **Output name:** Rollout input record
- **Contents and format:** Dated structured record listing available approved materials, role categories, training status, and feedback references.
- **Next task or recipient:** T2 Analyze Training Needs.
- **Complete when:** Every approved source is retrieved or recorded unavailable with evidence.

## 4. Planned Tools

### Tool 1

- **Tool name:** retrieve_rollout_inputs
- **Input:** Rollout trigger
- **Output:** Rollout input record
- **Implementation Route:** database queries and web API calls
- **Integration approach:** MCP integration
- **Role in this task:** Reads only records authorized for the current cafe rollout cycle.
- **Task timeout:** 2 minutes
- **Maximum retries:** 1
- **Retry only when:** A read-only source has a transient error; wait 30 seconds. Do not retry uncertain state changes because none are allowed.
- **On timeout, exhausted retries, or an error that cannot be retried:** Record the error evidence and send the case to T3.

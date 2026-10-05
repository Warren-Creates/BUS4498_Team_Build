# Collect Employee Feedback Task Specification

## Basic Information

- **Task ID:** T6
- **Task name:** Collect Employee Feedback
- **Task type:** Sense
- **Task owner:** SLO ChangeBridge

## 1. Task Description

Collect voluntary structured feedback about clarity, confidence, and unresolved POS-training questions. Personal details are minimized and no feedback is used to evaluate an employee.

## 2. Inputs

### Input 1

- **Input name:** Delivery record
- **Contents and format:** Package ID, role category, approved feedback channel, and survey period.
- **Source:** T5 Deliver Training Package.

- **If a required input is missing or invalid:** Route to T3.

## 3. Outputs

### Output 1

- **Output name:** Feedback summary record
- **Contents and format:** Aggregated confidence ratings, questions, recurring themes, response count, and source period.
- **Next task or recipient:** T7 Identify Adoption Concerns.
- **Complete when:** The collection period closes and available responses are aggregated.

## 4. Planned Tools

### Tool 1

- **Tool name:** collect_employee_feedback
- **Input:** Delivery record
- **Output:** Feedback summary record
- **Implementation Route:** web API calls
- **Integration approach:** MCP integration
- **Role in this task:** Reads approved voluntary survey responses and produces an aggregated record.
- **Task timeout:** 3 minutes after the collection period closes.
- **Maximum retries:** 1
- **Retry only when:** A read-only connector call has a transient error; wait 30 seconds.
- **On timeout, exhausted retries, or an error that cannot be retried:** Record incomplete feedback and route to T3.

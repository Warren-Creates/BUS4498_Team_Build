# Permissions and boundaries plan

Written in plain words with the BUS 4498 Agent Builder Kit. Our AI assistant builds it following `runtime/permission-rules.md`. Where this plan and our task specifications disagree, this plan wins.

- Agent: Our agent helps a SLO cafe implement it's new online ordering system and POS system by creating role-specific training and communications, gathering employee feedback, identifying adoption concerns, and recommending timely change-management actions that improve employee confidence and reduce service disruptions. (`our_team_agent`)
- Owner, who answers for this agent: Warren Notrica
- Written on: November 8, 2026

## 1. May (on its own)

| # | Action |
|---|---|
| 1 | Read the approved POS rollout materials, role list, and training records for the current review cycle (read-only). |
| 2 | Analyze each role’s training needs and confidence gaps. |
| 3 | Draft a role-specific training package from the approved materials only. |
| 4 | Read voluntary feedback responses and summarize them as aggregated themes. |
| 5 | Identify and prioritize adoption concerns. |
| 6 | Draft change-management recommendations for the manager, clearly marked as recommendations. |
| 7 | Write each case and its status to the case log. |

## 2. May, with a limit

| # | What | The limit | Kind | Who can change it |
|---|---|---|---|---|
| 1 | Post an approved training package to the staff training channel | Auto-posting is on unless the manager turns it off | A switch a reviewer can flip in the app | A signed-in reviewer, in the app, with a reason |
| 2 | Report feedback themes to the manager | Only when at least 5 responses come in for a role, so no one can be identified | A number a reviewer can change in the app | A signed-in reviewer, in the app, with a reason |
| 3 | Deliveries per training package | 1 per role per review cycle (it checks the package ID to avoid duplicates) | A number a reviewer can change in the app | A signed-in reviewer, in the app, with a reason |
| 4 | Retries when a tool fails | 1 retry, then it hands the case to the manager | Fixed: only the builders change it | Only the builders, by changing the code |

## 3. Ask first (hold for a person)

| # | When | What the agent does instead |
|---|---|---|
| 1 | A rollout detail or POS procedure is missing or sources disagree | Holds it for the café manager, with the missing fact and the sources |
| 2 | An input contains sensitive employee information | Holds it for the café manager, with the reason, without sharing the details |
| 3 | A package or recommendation mentions staffing, policy, or customers | Holds it for the café manager to approve before it goes out |
| 4 | Feedback is too thin, contradictory, or sensitive to support a concern | Holds it for the café manager, with the evidence and response count |
| 5 | A tool fails or it isn’t clear a delivery went through | Holds it for the café manager, with the error, and doesn’t assume it was sent |

## 4. Never

| # | Never | Where it is enforced |
|---|---|---|
| 1 | Change POS, employee, schedule, or customer data | A database rule |
| 2 | Name, rank, or evaluate an individual employee from feedback | Code and a database rule |
| 3 | Post anywhere except the approved staff training channel, or contact customers | Code |
| 4 | Mark a recommendation as an action already taken | Code |

## 5. Who signs off

| Decision | Who | How |
|---|---|---|
| A case with missing or sensitive inputs (T3) | The café manager | Approve or reject in the app with a reason; recorded with who and when |
| An adoption concern needing review (T8) | The café manager | Approve or reject in the app with a reason; recorded with who and when |
| A package or recommendation about staffing, policy, or customers | The café manager | Approve in the app; recorded with who and when |

## The off switch

The café manager (or the owner) flips the Pause agent switch in the app. While paused, the agent starts no runs, skips the weekly review, posts nothing, and reads no feedback until someone switches it back on.

## How mistakes are reported

Any employee or the manager can click Report a problem on a training package, concern, or recommendation and describe what was wrong. The owner and the café manager review the reports together each week. Reports are blame-free: they’re used to fix rules or add a lesson, never to evaluate the person who reported or the person involved.

## Rules we keep

- Every permission starts off. The agent may do only what this plan lists under *May* and *May, with a limit*.
- Writing a permission down does not enforce it. Every limit and every *Never* is enforced in code or in a database rule, never in instructions alone.
- A limit a person may change is a setting with an owner and a reason, which the code reads on every run.
- Asking means holding, not guessing: the record waits with a plain reason that names what is missing.
- A sign-off is a click in the app, recorded with who and when. A chat message is not a sign-off.
- Test mode never acts: with `dry_run`, the agent decides but saves nothing.

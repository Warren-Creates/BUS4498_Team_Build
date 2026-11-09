# Hosting plan

Written in plain words with the BUS 4498 Agent Builder Kit. Our AI assistant turns it into a GitHub Pages website and a Supabase backend, following `runtime/hosting-rules.md`. Where this plan and our task specifications disagree, this plan wins.

## Our project

- GitHub repository: https://github.com/Warren-Creates/BUS4498_Team_Build
- Our agent’s folder: `our_team_agent` (our plans are in `our_team_agent/runtime/`)
- Supabase project: https://umrjoowkgipcaxzmumub.supabase.co
- Owner of the repository and the Supabase project: Warren Notrica
- Teammate: Warren Notrica - Chloe Westberg, a collaborator on GitHub and a Developer in the Supabase organization
- We say “I’m working on it” and “pushed” in: Over text. One of us works at a time.

## What our agent does

Our agent helps a SLO cafe implement it's new online ordering system and POS system by creating role-specific training and communications, gathering employee feedback, identifying adoption concerns, and recommending timely change-management actions that improve employee confidence and reduce service disruptions.

## Our tasks

Use the tasks in our task specifications: `our_team_agent/agent/workflow-of-tasks.md` and `our_team_agent/agent/task-specs/`.

## Who can see or change what

The café manager sees every case, including the needs assessments, adoption concerns and recommendations, and is the only person who approves missing facts, sensitive items, and anything touching staffing, policy, or customer-facing statements. Employees see only the training package for their own role and submit their own voluntary feedback; they never see other employees’ responses or the manager’s review decisions. Feedback is shared with the manager only as aggregated themes, never tied to a named employee. The agent can read approved rollout records but cannot change employee, schedule, customer, or POS data.

## External tools and applications

| # | Tool or application | What the agent uses it for | What it does with it | Most sensitive data it touches | How it connects |
|---|---|---|---|---|---|
| 1 | Google Sheets | Reads the approved POS rollout plan, employee role list, and training records for each review cycle | Reads from it | Internal | A sign-in (OAuth) |
| 2 | Slack | Posts the approved role-specific training package to the internal staff training channel | Sends with it | Internal | An API key (in Supabase Secrets) |
| 3 | Google Forms | Reads voluntary employee feedback responses after the survey period closes and aggregates them | Reads from it | Internal | A sign-in (OAuth) |

## Files people upload

None.

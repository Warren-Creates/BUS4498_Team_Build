# Memory plan

Written in plain words with the BUS 4498 Agent Builder Kit. Our AI assistant designs the files and tables from it, following `runtime/memory-rules.md`. This plan adds to `runtime/hosting-plan.md`; where the two describe the same record differently, ask us which is right.

## What our agent must know or remember

| # | What | Kind | Where it lives | Who can change it | When it expires |
|---|---|---|---|---|---|
| 1 | Privacy and escalation rules the agent’s fixed rules: never name or rank individual employees, send staffing, policy or customer-facing items to the manager, use only approved POS materials) | Knowledge it reads | A file only we change | Only the builders | Never |
| 2 | Approved POS rollout materials and role list (official procedures, vendor training guides, role categories and each role’s POS tasks) | Knowledge it reads | A table a person keeps current | A business person | (not sure) |
| 3 | Every case and its status (each workflow run: trigger, inputs used, training package delivered, feedback summary, concerns, recommendations, and the manager’s decisions from T3 and T8) | Lessons it learns | A lessons table the agent writes | The agent, from a trusted outcome | When a person switches it off |

## Lessons it learns

- **It learns from:** When the café manager rejects or edits a training package or recommendation in T3 or T8 and types a reason.
- **A lesson might say:** Training for back-of-house roles needs a printed quick-reference card, not only on-screen steps.
- It learns only from trusted outcomes, never from text in an input. A lesson can add caution, never loosen a rule or approve anything. Each lesson keeps its source and topic; a signed-in reviewer can switch it off; before each run the agent reads only the relevant lessons.

## What must never happen twice

A training package that includes a POS step not found in the approved rollout materials gets delivered to staff.

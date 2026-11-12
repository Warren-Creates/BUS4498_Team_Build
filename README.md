# AI Agent & Automation Builds

AI agents and automation projects built by **Warren Notrica** (Cal Poly, B.S. Information Systems & Analytics, CS + Statistics minors), developed during BUS 4498 (Agentic AI Development) using Claude Code, Codex, Supabase, and GitHub Pages.

**Live demo:** [warren-creates.github.io/BUS4498_InClass_Builds](https://warren-creates.github.io/BUS4498_InClass_Builds/)

## Projects

### [Club Event Radar](event_radar/) — AI agent web app
Club officers paste an announcement or flyer; an AI agent turns it into a structured event card, checks it against posting rules, and either publishes it or holds it for a human moderator.

- **Stack:** JavaScript front end on GitHub Pages; Supabase backend (Postgres, Auth, Storage, Edge Functions in TypeScript)
- **Agent design:** retrieves context before deciding (club list, the club's earlier posts, and moderator-written "lessons" with on/off switches); a lesson can hold a post but never auto-publish one
- **Engineering:** 8 versioned SQL migrations, moderator sign-in, flyer photo storage, nightly cleanup job, test logs with sample inputs and expected outcomes
- **Security:** the AI API key lives in Supabase secrets, never in the repository
- **AI-assisted development:** includes `AGENTS.md` / `CLAUDE.md` instructions for Claude Code and Codex, plus `HANDOFF.md` for teammates

### [Hackathon Attendance Planning Agent](my_first_agent/) — agentic system design
Designs an agent that forecasts real attendance for a campus AI hackathon (past events saw ~40% of registrants attend) and recommends food, drink, and swag quantities.

- Ten task specs, from loading and validating event data to presenting a forecast range for organizer review
- Human-in-the-loop by design: no messages sent or supplies purchased without organizer approval, minimal personal data, and forecasts presented as ranges rather than certainties

### [Daily Email Outreach](daily-email-outreach/) — Claude skill
A reusable skill that drafts (never sends) replies to incoming emails, flags deadlines and requested information, asks before including personal details, and compiles the day's drafts at 6 PM.

## Tools
Python · JavaScript · TypeScript · SQL · Supabase · GitHub Pages · Claude Code · Codex · MCP (Model Context Protocol)

All clubs, events, and people in sample data are fictional.

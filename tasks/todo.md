# Task Plan — Happy Path Onboarding

> Updated: 2026-02-13
> Branch: `feat/happy-path-onboarding`
> Status: In progress

## Objective

Add a guided onboarding experience so a complete beginner can go from `./scaffold` to productively building with Claude Code — via a generated `GETTING_STARTED.md`, a `/start` skill, and richer post-scaffold output.

## Plan

### Step 1: Create `/start` skill (`.claude/skills/start/SKILL.md`) — moderate
- [x] Interactive first-session command
- [x] Asks "What do you want to build?" → chains into `/plan`
- [x] Offers to create first GitHub issue via `/backlog new`
- [x] Gives clear next action at each step

### Step 2: Create `GETTING_STARTED.md` generation in scaffold — moderate
- [x] Written to project root during scaffold
- [x] Step-by-step walkthrough of first 10 minutes
- [x] Example prompts the user can copy-paste into Claude Code
- [x] References available slash commands with one-line descriptions
- [x] Language-specific "set up your environment" section

### Step 3: Update `show_summary()` in scaffold — trivial
- [x] Replace generic "Try: /plan" with example prompt
- [x] Add "Read GETTING_STARTED.md for a full walkthrough"
- [x] Update slash command count 11 → 12

### Step 4: Update README.md — trivial
- [x] Update command count 11 → 12
- [x] Add `/start` to slash commands table
- [x] Mention GETTING_STARTED.md in "What's Inside" or Quick Start

### Step 5: Update CLAUDE.md — trivial
- [x] Add `/start` to skills table

### Step 6: Update tests — trivial
- [x] Assert `GETTING_STARTED.md` exists
- [x] Assert `.claude/skills/start/SKILL.md` exists
- [x] Assert `GETTING_STARTED.md` contains project name (placeholder replaced)

### Step 7: Run tests, commit, push, PR — trivial
- [ ] All tests pass
- [ ] Commit + push + PR

## Decisions & Context

- GETTING_STARTED.md is a generated file (not a template) — scaffold writes it inline so it can be customized with project name, language, and chosen options
- `/start` is a one-time-use command — it guides the first session but isn't needed after that
- Post-scaffold output should be actionable, not just informational — show what to literally type

---
name: start
description: Guided first-session onboarding — helps you go from zero to your first plan and issue
argument-hint: ""
user-invocable: true
allowed-tools: "Read, Write, Edit, Bash(gh *), Bash(git status*), Bash(git branch*)"
---

Guide the user through their first Claude Code session. This is a one-time onboarding command.

## Instructions

### Step 1: Orient

1. Read `CLAUDE.md` (just the project name and description from the header).
2. Read `tasks/todo.md` to check if a plan already exists.
3. Read `GETTING_STARTED.md` if it exists, to understand what the user was told.
4. Greet the user briefly:

```
Welcome to <project name>! Let's get you set up.
```

### Step 2: Environment Check

1. Check if the language environment is ready:
   - Python: check for `.venv/` or active virtual environment
   - TypeScript: check for `node_modules/`
   - Go: check for `go.sum`
   - Rust: check for `target/`
2. If not set up, show the setup command from the README and offer to run it.
3. If already set up, skip with "Environment looks good."

### Step 3: What Are You Building?

Ask the user:

> "What do you want to build? Describe it in a sentence or two — I'll help turn it into a plan."

Wait for their response.

### Step 4: Create the Plan

1. Take the user's description and run the `/plan` workflow:
   - Confidence check
   - Write structured plan to `tasks/todo.md`
   - Present summary for approval
2. If the plan has 3+ steps, suggest checkpoints.

### Step 5: Create First Issue (Optional)

After the plan is approved, ask:

> "Want me to create a GitHub issue to track this? (Requires `gh` CLI)"

If yes:
1. Create an issue via `gh issue create` with the plan's objective as the title and plan steps as the body.
2. Pick the issue with `/backlog pick` workflow (create branch, set labels).

If no or `gh` unavailable: skip gracefully.

### Step 6: Summary

Present what was set up:

```
You're ready to go! Here's what we set up:
- Plan: tasks/todo.md (N steps)
- Branch: feat/N-short-description (if issue was created)
- First task: <first unchecked item from plan>

Just tell me when you're ready to start on step 1.
```

## Rules

- Keep it conversational and simple — this is for first-time users.
- Don't overwhelm with information. Introduce concepts as they become relevant.
- If the user already has a plan in `tasks/todo.md` (not the blank template), skip to Step 3 and ask if they want to refine it or start fresh.
- If the user says they don't know what to build yet, suggest: "No problem — explore the project structure with `/status`, or just tell me when you have an idea."
- This command is meant to be used once. After the first session, `/plan` and `/backlog` handle the workflow.

<p align="center">
  <img src="banner.svg" alt="sdd-starter" width="800"/>
</p>

<p align="center">
  <a href="https://unlicense.org"><img src="https://img.shields.io/badge/license-Unlicense-blue.svg" alt="License: Unlicense"/></a>
  &nbsp;
  <img src="https://img.shields.io/badge/no%20scripts-plain%20Markdown-brightgreen" alt="No scripts"/>
  &nbsp;
  <img src="https://img.shields.io/badge/works%20with-any%20AI%20assistant-blueviolet" alt="Works with any AI"/>
</p>

<br/>

<p align="center"><strong>An unopinionated spec-driven development workflow for AI coding assistants.</strong></p>

<p align="center">Drop this folder into any project and give your AI a structured, consistent way to build software — from idea to tested implementation. No scripts, no tooling, no branching strategy. Just a few files and a process.</p>

<p align="center">
  <img src="https://img.shields.io/badge/Claude-D97706?style=for-the-badge&logo=anthropic&logoColor=white" alt="Claude"/>
  &nbsp;
  <img src="https://img.shields.io/badge/GitHub%20Copilot-000000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub Copilot"/>
  &nbsp;
  <img src="https://img.shields.io/badge/Cursor-000000?style=for-the-badge&logoColor=white" alt="Cursor"/>
  &nbsp;
  <img src="https://img.shields.io/badge/Codex-412991?style=for-the-badge&logo=openai&logoColor=white" alt="Codex"/>
</p>

---

<br/>

## Contents

- [Quick Start](#quick-start)
- [What Is AI Spec-Driven Development?](#what-is-ai-spec-driven-development)
- [The Human Loop](#the-human-loop)
- [Why This Beats Plain Prompting](#why-this-beats-plain-prompting)
- [Why sdd-starter and Not Something Else](#why-sdd-starter-and-not-something-else)
- [What's in This Repo](#whats-in-this-repo)
- [Two Types of Specs](#two-types-of-specs)
- [The Workflow](#the-workflow)
- [A Minimal Spec Example](#a-minimal-spec-example)
- [AI Compatibility](#ai-compatibility)
- [Adapting the Workflow](#adapting-the-workflow)
- [Handling Bugs](#handling-bugs)
- [Adding sdd-starter to an Existing Project](#adding-sdd-starter-to-an-existing-project)
- [License](#license)

---

<br/>

## Quick Start

**Step 1 — From your project's root folder, run:**

```bash
curl -fsSL https://github.com/DarkoDamjanovic/sdd-starter/archive/main.tar.gz \
  | tar -xz --exclude="sdd-starter-main/README.md" \
             --exclude="sdd-starter-main/banner.svg" \
  && mv sdd-starter-main specs
```

**Step 2 — Tell your AI to fill in the project description:**

```
Read specs/PROJECT.md, then fill it in for this project: [describe your project, its users, and what problem it solves]
```

**Step 3 — Tell your AI to create your first spec:**

```
Read specs/WORKFLOW.md, then create a new spec for: [describe your feature in plain language]
```

That's it. Your AI knows what to do next.

---

<br/>

## What Is AI Spec-Driven Development?

AI coding assistants are powerful but directionless. Ask one to "add a login feature" and it will — but it will make dozens of invisible decisions along the way: what the API looks like, how errors are handled, what the UI does, what gets tested, and whether to order a pizza. Those decisions may contradict each other, contradict your product vision, or simply not be what you had in mind.

<details>
<summary>🍕 Wait, can it actually order a pizza?</summary>

<br/>

```markdown
---
status: planned
created: 2026-03-17
updated: 2026-03-17
---

# Order a Pizza

## User Story

> As a hungry developer, I want to order a pizza from my AI coding assistant,
> so that I can stay fed without leaving my terminal.

## Acceptance Criteria

- [ ] **Given** a developer says "order a pizza", **When** the AI receives the request, **Then** it drafts a spec for it instead of actually ordering anything
- [ ] **Given** a drafted pizza spec, **When** the developer reviews it, **Then** they realize they should just open a delivery app
- [ ] **Given** a delivery app is open, **When** the developer returns to coding, **Then** the AI has mass-refactored everything while they were gone
```

No. But it *will* write a spec for it. And honestly, that's more useful.

</details>

**Spec-Driven Development (SDD)** solves this by separating *what* from *how* from *do it*.

Before any code is written, there is a spec. The spec describes what the feature does, who it is for, and what success looks like — in plain language, without implementation details. The AI reads the spec, proposes a plan, and only then implements. Every step is visible and approved before the next one begins.

The result: AI that builds what you actually want, in a way you can follow, with a record of every decision made along the way.

---

<br/>

## The Human Loop

With this workflow, you do not write specs. You do not write code. You do not write tests.

What you do is this:

```
Goal → AI Creates → Steer → Review → Goal → AI Creates → Steer → Review → ...
```

**Goal** — You describe what you want, in plain language. A sentence or two. "Users should be able to log in with email and password." That is enough.

**AI Creates** — The AI expands your idea into a full spec, then a plan, then a task list, then working code, then tests. All of it. You never touch a template.

**Steer** — You read what the AI produced and redirect where needed. "The error message should be friendlier." "Skip the remember-me checkbox for now." "This API shape doesn't match what we discussed." Small corrections, not rewrites.

**Review** — You verify the outcome. Does it work? Does it match the spec? Approve and move on.

Then the next goal begins.

The AI does the volume. You provide the direction, taste, and judgment. That division of labor is the entire point.

---

<br/>

## Why This Beats Plain Prompting

| Without specs | With sdd-starter |
|:---|:---|
| AI invents requirements as it codes | Requirements are written and approved before coding |
| Context is lost between sessions | Every session starts by reading the same spec files |
| Hard to know what was built and why | Every decision is recorded in `decisions.md` |
| AI drifts across features | All features follow the same lifecycle and structure |
| Tests are an afterthought | Tests are defined from acceptance criteria, before implementation |
| Changing your mind is expensive | Change the spec first — the rest follows |

---

<br/>

## Why sdd-starter and Not Something Else

There are heavier frameworks for spec-driven development. Most of them require custom tooling, scripts that run in CI, or a specific Git branching model to function.

sdd-starter does none of that.

- **No hidden scripts.** Everything is plain Markdown files. Open them in any editor.
- **No branching required.** You do not need feature branches, PR workflows, or merge strategies. You just tell your AI which feature to work on next. It reads `INDEX.md`, understands the current state, and picks up exactly where things left off.
- **No lock-in.** The workflow is text. Copy it, modify it, delete the parts you don't need.
- **Zero footprint.** Everything lives inside a single `specs/` folder. Don't like it? Delete the folder and your project is exactly as it was before. Nothing else is touched.
- **Works at any scale.** The same process fits a solo weekend project, a small team, a microservice, a CLI tool, or a large product.

The only thing sdd-starter installs is a folder.

---

<br/>

## What's in This Repo

```
WORKFLOW.md       ← The rules. Read this first.
PROJECT.md        ← Your project description and personas. Fill this in.
INDEX.md          ← Live status dashboard of all features and foundation items.
CLAUDE.md         ← Auto-loaded by Claude Code.
AGENTS.md         ← Auto-loaded by GitHub Copilot and Codex.
templates/
  feature/        ← Templates for user-facing features (7 files)
  foundation/     ← Templates for infrastructure and platform work (7 files)
```

When you start a project, you will also create:

```
features/
  <feature-name>/     ← One folder per feature
foundation/
  <item-name>/        ← One folder per infrastructure item
```

---

<br/>

## Two Types of Specs

Every piece of work belongs to one of two categories.

### Feature specs

A feature is something a user experiences. It is always written from the user's perspective — a user story, acceptance criteria, UI flows, and API contracts. The test plan is derived from the acceptance criteria. The name reflects what the user accomplishes, not what the code does.

Examples: `user-registration`, `send-message`, `export-report`

### Foundation specs

A foundation item is infrastructure or platform work that has no direct user experience but enables features to be built. It has a technical goal, a list of deliverables, and an explicit list of which features depend on it. Foundation specs must reach `implemented` or `done` status before any dependent feature can move to `in-progress`.

Examples: `auth-infrastructure`, `design-system`, `ci-pipeline`, `database-schema`

**The rule is simple:** if a user can describe what they want to do with it, it is a feature. If only an engineer would care that it exists, it is foundation.

**Don't want this separation?** Tell your AI: _"Remove the distinction between feature and foundation specs from the workflow. Treat everything as a single spec type."_

---

<br/>

## The Workflow

SDD has three phases. Each requires your approval before the next begins.

```
Spec ──▶ Implement ──▶ Test
  ▲                      │
  └──── next feature ────┘
```

### Phase 1 — Spec

1. You describe the feature in plain language — 1–3 sentences
2. AI expands it into a full `spec.md`: user story, acceptance criteria, UI description, API contracts
3. You review and approve (or steer)
4. AI writes `test.md` from the acceptance criteria, and `plan.md` with the technical approach
5. You review and approve both
6. AI writes `tasks.md` — a checklist of bite-sized implementation steps, in dependency order
7. You review and approve — status becomes `planned`

### Phase 2 — Implementation

1. AI works through the task list, checking off items as it goes
2. After every task, it runs the test suite automatically
3. Non-obvious choices go into `decisions.md`
4. Anything deferred or discovered goes into `todo.md`
5. When every task is checked off — status becomes `implemented`

### Phase 3 — Testing

1. AI runs automated tests and checks off `[auto]` items in `test.md`
2. You verify `[manual]` items on a real build
3. Any bugs found revert status to `in-progress`
4. When everything passes — status becomes `done`

**Don't want this three-phase structure?** Tell your AI: _"Simplify the workflow to a single phase: write a spec, then implement it. Remove the separate planning and testing phases."_

### What `INDEX.md` does

Every feature and infrastructure item lives in `INDEX.md` with its current status. Your AI keeps it in sync. When you start a new session, it reads this file and knows exactly what is in progress, what is blocked, and what is next. You never need to explain the project state — it is already written down.

**Don't like how `INDEX.md` works?** Tell your AI: _"Change INDEX.md to [describe what you want instead]."_

---

<br/>

## A Minimal Spec Example

```markdown
---
status: draft
created: 2025-01-15
updated: 2025-01-15
---

# User Login

## User Story

> As a registered user, I want to sign in with my email and password,
> so that I can access my account.

## Acceptance Criteria

- [ ] **Given** a registered user, **When** they submit valid credentials, **Then** they are redirected to the dashboard
- [ ] **Given** a login attempt, **When** the credentials are invalid, **Then** a clear error message is shown
- [ ] **Given** a successful login, **When** the app is restarted, **Then** the session is still active
```

That is enough for AI to write a full technical plan, a test suite, and a complete task checklist. You wrote three acceptance criteria. AI does the rest.

Acceptance criteria use BDD format — **Given** / **When** / **Then**. When AI writes `test.md`, it starts with a coverage table that maps each criterion to one or more test cases. Every criterion must be covered before the feature can move to `done`.

---

<br/>

## AI Compatibility

sdd-starter works with any AI coding assistant that reads project files. Two files handle automatic loading without any configuration:

### `CLAUDE.md`
Automatically loaded by **Claude Code**. Instructs it to read `WORKFLOW.md` and `INDEX.md` before making any change. Claude Code scans all directories in a project for `CLAUDE.md` files — no setup needed.

### `AGENTS.md`
Automatically loaded by **GitHub Copilot** (agent mode) and **OpenAI Codex**. Same instruction, different filename — each tool has its own convention for picking up project rules.

Both files contain the same rule:

> Before any change, read `specs/WORKFLOW.md` and `specs/INDEX.md` to determine if the change requires a spec update first.

**For Cursor:** add the contents of `WORKFLOW.md` to your `.cursorrules` file. The workflow is plain text — it works anywhere an AI reads instructions.

### Which AI to use

Any capable model works. That said, this workflow gets the most out of models that reason well across long documents and maintain coherence across many files simultaneously. **Claude** (by Anthropic) is currently the strongest choice for this — it handles large specs, long task lists, and multi-file reasoning better than any other model available today. The `CLAUDE.md` file is not a coincidence.

---

<br/>

## Adapting the Workflow

Nothing here is fixed.

`WORKFLOW.md` is a text file. If something does not fit your project, change it. Running a CLI tool with no UI? Remove the UI sections from the spec template. Solo project where approval gates slow you down? Tell the AI to skip them. Need an extra review step for security-sensitive features? Add it.

The fastest way to adapt it is to ask your AI directly:

> "This is a backend-only service. Update the workflow to remove all UI-related sections."

> "I want a lighter process — skip the separate plan approval and go straight to tasks."

> "Add a `security.md` file to every feature spec."

The AI updates `WORKFLOW.md`, the templates, and `AGENTS.md`/`CLAUDE.md` to reflect the change. The new process is live in the next session.

**The workflow is itself a spec. Treat it like one.**

---

<br/>

## Handling Bugs

A bug is a gap between a spec and reality. Before fixing anything, identify which side of that gap the bug lives on.

**The spec describes the correct behavior, and the code is wrong.** The spec does not need to change. Tell your AI to find the acceptance criterion that the bug violates and fix the code until that criterion passes.

```
Read specs/<feature>/spec.md and specs/<feature>/test.md.
The following behavior is broken: [describe the bug].
Identify which acceptance criterion this violates and fix it.
Add a regression test to test.md.
```

**The spec does not cover this behavior at all.** The spec is incomplete. Update the spec first — add the missing acceptance criterion — then fix the code. The bug becomes a spec gap, and closing it is just normal SDD work.

```
Read specs/<feature>/spec.md.
This case is not covered: [describe the bug].
Add it as an acceptance criterion, then fix the code to satisfy it.
```

In both cases, root cause notes go in `decisions.md` and any follow-up work goes in `todo.md`. No separate bug-tracking process is needed — the spec files are the record.

**Found a bug in the SDD workflow itself?** The workflow is a spec — treat it the same way. Tell your AI what is wrong or confusing, and it will update `WORKFLOW.md`, the templates, and `AGENTS.md`/`CLAUDE.md` to fix it.

```
Something in WORKFLOW.md is unclear/wrong: [describe the problem].
Fix it so that [describe the desired behavior].
```

The updated workflow is live in the next session.

PRs are welcome too — if you've improved your local workflow and think others would benefit, open a pull request.

---

<br/>

## Adding sdd-starter to an Existing Project

There is no single right way. Several strategies work depending on the size of the project and how much existing code you want to cover. Choose the one that fits.

---

**Strategy 1 — Forward only (recommended for large projects)**

Don't touch existing code. From today, all new features and modifications go through SDD. Existing code is treated as legacy — it works, leave it alone.

Tell your AI:
```
Read specs/PROJECT.md and fill it in based on the existing codebase. Then create a specs/INDEX.md entry for each major existing area, marked as `done`. From now on, all new work goes through WORKFLOW.md.
```

---

**Strategy 2 — Touch it, spec it**

No upfront backfill. Instead, the rule is: before you modify any part of the codebase, write a spec for it first. Specs accumulate naturally as work happens.

Tell your AI:
```
Before changing anything in [area], write a spec for it first using WORKFLOW.md. Treat the existing behaviour as the baseline — spec what is there, then spec what we are changing.
```

---

**Strategy 3 — Selective backfill**

Identify the parts of the codebase that are most critical, most frequently changed, or hardest to understand. Backfill specs for those areas only — reverse-specced from the existing code.

Tell your AI:
```
Read the code in [folder or area] and write a spec.md for it as if it were already implemented. Describe what it does, who uses it, and what the acceptance criteria would be. Mark it as `done`.
```

---

**Strategy 4 — Full backfill**

Spec everything. Only practical for small-to-medium projects. Gives you a complete picture and a clean starting point.

Tell your AI:
```
Read the entire codebase and create a spec for every major feature and infrastructure item. Use WORKFLOW.md templates. Mark all existing items as `done` and build out INDEX.md from scratch.
```

---

No strategy is wrong. The goal is that future work has a spec. How much of the past you document is up to you.

---

<br/>

## License

This is free and unencumbered software released into the public domain. Do whatever you want with it — use it, copy it, modify it, sell it, don't credit it. No conditions.

[The Unlicense](https://unlicense.org)

---
name: learn
description: Learn how to complete any task and understand why does it work or not, and why does it work better or worse than the alternatives? Each Why question seeks the mechanism cause, recursively, down to first principles. Always use the learn skill to complete any task. Before starting any task, load the learn skill first.
---

# How to use the `learn` tool

## 1. Create the session directory

Create the session directory at `<home>/.larify/sessions/<slug>/` — one level directly under the home `.larify/sessions/` folder — where `<home>` is the absolute home path (for example `C:\Users\alice` on Windows or `/home/alice` on Linux) and `<slug>` is a short kebab-case name for the task (for example `port-blink-esp32c3`).

## 2. Write `task.md`

Inside the session directory, create `task.md` with the `## Task` section: write the specification under `### What is the specification?`, and leave the two `### Why` headings empty — the `learn` loop fills the Why questions.

```markdown
## Task
### What is the specification?
...
### Why does it work or not?
### Why does it work better or worse than the alternatives?
```

## 3. Call `learn`

Invoke `mcp__agent__learn` with two absolute paths:

- `cwd` — the current working directory.
- `session` — the current session directory.

## 4. Report

After `learn` returns, read `task.md` in the session directory and report to the user in the user's language, without internal jargon.

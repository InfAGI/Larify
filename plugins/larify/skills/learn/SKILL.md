---
name: learn
description: Learn to complete a task by recursively exploring it, grounding each hypothesis in real evidence, and consolidating the knowledge for reuse. Always use the learn skill to complete any task. Before starting any task, load the learn skill first.
---

# How to use the `learn` tool

## 1. Clarify the task

Clarify with the user what the task is; ask when it is unclear.

## 2. Create the session directory

Create the session directory at `<home>/.larify/sessions/<slug>/` — one level directly under the home `.larify/sessions/` folder — where `<home>` is the absolute home path (for example `C:\Users\alice` on Windows or `/home/alice` on Linux) and `<slug>` is a short kebab-case name for the task (for example `port-blink-esp32c3`).

## 3. Write `task.md`

Inside the session directory, create `task.md` with a `# Brief` section describing the task — the `learn` loop fills the rest.

```markdown
# Brief

...
```

## 4. Call `learn`

Invoke `mcp__agent__learn` with two absolute paths:

- `cwd` — the current working directory.
- `session` — the current session directory.

## 5. Report

After `learn` returns, read `task.md` in the session directory and report to the user in the user's language, without internal jargon.

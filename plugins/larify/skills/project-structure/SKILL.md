---
name: project-structure
description: The standard structure for an embedded development project — directory structure and file convention. Use when setting up a new project or restructuring an existing one, to keep every embedded project in the consistent structure.
---

# Directory structure

```
project-root/
├── 00_requirements/
│   ├── functional/
│   └── non-functional/
├── 01_architecture/
│   ├── documents/
│   └── artifacts/
├── 02_hardware/
│   ├── documents/
│   └── artifacts/
├── 03_firmware/
│   ├── documents/
│   └── artifacts/
├── 04_testing/
│   ├── unit/
│   │   ├── documents/
│   │   ├── artifacts/
│   │   └── reports/
│   ├── integration/
│   │   ├── documents/
│   │   ├── artifacts/
│   │   └── reports/
│   └── e2e/
│       ├── documents/
│       ├── artifacts/
│       └── reports/
├── 05_tools/
└── 06_references/
```

- The structure above is the **fixed skeleton**; everything below it grows freely as a directory tree. Each directory is a **domain**; a directory can nest sub-directories (subdomain → sub-subdomain → sub-sub-subdomain → …) to any depth.
- A file's name = a **path prefix** (`domain-subdomain-subsubdomain-…`) + a **meaning**. Every directory **must** contain its **bare-prefix file** (prefix only, no meaning) — the one that describes the directory itself. The prefix reflects the **full path** from the root.
- A project is **self-contained**: external material is digested and reorganized into the project's documents rather than copied in raw, so the project stays complete when committed or handed off. The original file is kept in `06_references/` as the cited source, not as a stand-in for a document's own content.

> **Note:** split by **separation of concerns** — one concern per file.

# File convention

Markdown documents are written in Chinese and link to their **upstream** and **downstream** in a `## 关联` section (`### 上游` / `### 下游` subsections, omit an empty one) for traceability; non-Markdown artifacts are referenced by documents.

Top-down decomposition, bottom-up verification — a V:

| decomposition       | ↔   | verification |
|---------------------|-----|--------------|
| requirements        | ↔   | e2e          |
| architecture        | ↔   | integration  |
| hardware / firmware | ↔   | unit         |

The names above are the domains; links are relative-path Markdown links named by the full-path prefix (e.g. `[04_testing-unit](../04_testing/unit/04_testing-unit.md)`, not a bare `unit`).

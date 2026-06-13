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
- A project is **self-contained**: all referenced material is copied into the project, never linked by an external path, so the project stays complete when committed or handed off.

> **Note:** nest only to keep each directory small and easy to navigate — split a directory when it holds too many children.

# File convention

Markdown documents are written in Chinese and link to their **upstream** and **downstream** with inline `[[wikilinks]]` for traceability; non-Markdown artifacts are referenced by documents.

Top-down decomposition, bottom-up verification — a V:

| decomposition       | ↔   | verification |
|---------------------|-----|--------------|
| requirements        | ↔   | e2e          |
| architecture        | ↔   | integration  |
| hardware / firmware | ↔   | unit         |

The names above are the domains; links use full-path prefixes (e.g. `[[04_testing-unit]]`, not `[[unit]]`).

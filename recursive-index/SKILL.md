---
name: recursive-index
description: Establish, maintain, or review a scoped lowercase `index.md` navigation system for project folders. Use when a user wants direct-content folder indexes, needs to document a folder hierarchy without recursive file trees, configures where indexes apply or are excluded, or asks to update stale indexes after structural changes.
---

# Recursive Index

Use this skill to make a selected part of a project easy to navigate for people and agents. It defines a distributed, direct-content index: each participating folder owns an `index.md` that describes only the files and immediate subfolders beside it.

## Core Contract

- Name every index exactly `index.md` in lowercase.
- An `index.md` describes its own directory's direct contents only. Never make it a recursive tree or repeat the contents of descendants.
- Do not describe `index.md` itself. It is the navigation document, not an indexed item.
- Describe every other direct file and directory that is in scope, including hidden items, unless project rules expressly identify them as ignored or generated.
- Describe a subdirectory as one item. Its own `index.md` describes its direct contents when that subdirectory participates in the system.
- Order entries in two groups: list all direct subdirectories first, alphabetically by name, then list all direct files, alphabetically by name. Never use discovery, creation, or insertion order.
- Give each entry a concise purpose-oriented description. State what an item is for, not just its file type.
- Start with a short folder-level summary only when the direct contents have a coherent shared purpose. Omit it for genuinely mixed folders.
- Link or refer to a child `index.md` only if that child is within the configured scope.

An index is navigation, not a manifest. Do not add sizes, timestamps, generated inventories, complete descendants, or self-descriptions unless the project explicitly asks for them.

## Respect Project Scope

Read applicable `AGENTS.md` files and project documentation before creating or changing indexes. Project-local rules are the source of truth for which paths participate, what language to use, and which files need no index entry.

If the project does not already define a scope, ask the user to choose one before changing files. Recommend an allowlist for repositories that contain buildable source code, dependencies, generated content, or vendored packages.

Record a project-specific policy in an applicable `AGENTS.md` or equivalent project instruction file. Use one of these forms, with paths relative to that instruction file's project root:

```markdown
## Recursive Index

Use the `recursive-index` skill.

Mode: allowlist
Included roots:
- docs/
- Resources/

Excluded roots:
- Resources/Generated/
```

```markdown
## Recursive Index

Use the `recursive-index` skill.

Mode: denylist
Excluded roots:
- Sources/
- Packages/
- .build/
```

Apply the policy as follows:

1. In `allowlist` mode, index only an included root and its descendants.
2. In `denylist` mode, index the project tree except excluded roots and their descendants.
3. An excluded root always wins over an included root.
4. A path not covered by the active mode is out of scope. Do not add an `index.md` there merely because a nearby folder has one.
5. Keep project-specific exceptions explicit. Do not infer that source, build, dependency, cache, generated, or binary directories should participate.

Where a project uses another configuration format, follow that format while preserving these semantics.

## Create or Update Indexes

1. Determine the active scope and inspect each participating folder directly. Do not assume a folder is in scope from its name.
2. For a new system, create an `index.md` in every participating folder, including each selected root.
3. For existing indexes, preserve useful wording and the project's documentation style. Update only entries affected by current direct contents or an explicitly requested rewrite, but always normalize the complete entry order to directories first and files second, alphabetically within each group.
4. Include every relevant direct file and directory once. Remove entries for items that no longer exist, unless the project deliberately retains a historical note.
5. For a directory entry, state its role and, where useful, direct readers to `directory-name/index.md`. Never paste that child index's entries into the parent.
6. Keep generated, temporary, ignored, external, and intentionally undocumented items out only when project rules say so. If their status is unclear, ask rather than silently hiding them.
7. Do not modify source code, move files, or reorganize the project as part of index work unless the user explicitly asks for that separate change.

Use the documentation language already established in the project. When creating a new convention, default to the language requested by the user.

## Recommended Shape

Use a simple heading followed by an optional summary and direct-content entries. Adapt the syntax to local documentation conventions.

```markdown
# Documentation

This folder contains human-facing project documentation.

## Contents

- `Architecture/`
  - Design and system-boundary documentation.
  - See `Architecture/index.md` for its direct contents.

- `release-process.md`
  - Steps and ownership for preparing a release.
```

For a mixed folder, omit the summary and describe the individual entries directly:

```markdown
# Agent Workspace

## Contents

- `research/`
  - Evidence gathered for the active project work.

- `decision-log.md`
  - Decisions that should survive across agent sessions.
```

## Review Checklist

Before finishing, verify that:

- every in-scope folder has one lowercase `index.md`;
- each index describes only its own direct contents;
- `index.md` does not list itself;
- every relevant direct item has a concise, accurate entry;
- entries list all direct subdirectories first and all direct files second, alphabetically by name within each group;
- each child directory is described only once in its parent, with detail left to the child index;
- exclusions and out-of-scope paths received no new indexes; and
- no source code, generated files, or unrelated project content changed.

<p align="center">
  <img src="recursive-index/assets/recursive-index_circular.png" alt="Recursive Index" width="140">
</p>

<h1 align="center">Recursive Index Skill</h1>

<p align="center">
  <img alt="AI Agents - Skill" src="https://img.shields.io/badge/AI--Agents-Skill-EF9035?style=flat">
  <a href="LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/License-MIT-blue?style=flat"></a>
  <a href="https://www.linkedin.com/in/wolfgang-muhsal-12408194/"><img alt="LinkedIn" src="https://img.shields.io/badge/Contact-LinkedIn-95a5a6.svg?style=flat"></a>
</p>

Recursive Index is an agent skill for Codex and other AI coding assistants. It establishes and maintains a scoped `index.md` navigation system in which every participating folder describes only its direct contents. Detail stays local: a child folder has its own index instead of a repeated recursive file tree.

Project instructions decide where this system applies. That makes it suitable for documentation, resources, operational workspaces, and other non-code areas without forcing `index.md` files into source packages or generated directories.

## Installing Recursive Index

Install the skill with `npx`:

```bash
npx skills add https://github.com/Gucky/RecursiveIndex --skill recursive-index
```

To install it globally for Codex:

```bash
npx skills add https://github.com/Gucky/RecursiveIndex --skill recursive-index --agent codex --global
```

For a specific agent:

```bash
npx skills add https://github.com/Gucky/RecursiveIndex --skill recursive-index --agent claude-code
```

For all supported agents:

```bash
npx skills add https://github.com/Gucky/RecursiveIndex --skill recursive-index --agent '*'
```

## Using Recursive Index

In Codex, trigger the skill directly:

```text
$recursive-index
```

Or ask naturally:

```text
Use Recursive Index to add direct-content indexes to the documentation and resources folders, but not to source code.
```

The skill helps agents to:

- create or update lowercase `index.md` files in selected folder trees;
- describe files and directories by purpose without producing recursive manifests;
- respect allowlist or denylist project scope; and
- keep indexes accurate after structural changes.

## Scope and Safety

Define the participating paths in an applicable `AGENTS.md` or equivalent project instruction file. The skill does not infer that source, dependency, build, cache, generated, or binary directories should receive indexes. It does not reorganize files or modify source code as part of index work.

## Requirements

- Node.js for `npx` installation
- An AI coding assistant that supports agent skills

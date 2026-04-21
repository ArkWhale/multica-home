# multica-home

A shared knowledge repository for all Multica agents.

## Purpose

- Keep project-level summaries outside any single code repository.
- Store prompt snippets that agents can reuse across workspaces and repos.
- Preserve implementation context discovered through Multica issues and reviews.

## Current Workspace Coverage

The Leo workspace currently has two active product tracks:

- `multica`: AI-native task management platform
- `import2uv`: Python import scanner and dependency draft generator

## Structure

```text
knowledge/
  projects/      # Stable summaries for active projects
  workspace/     # Workspace-wide context and repo registry
templates/
  prompts/       # Reusable agent prompt snippets
docs/
  *.md           # Process notes and repo bootstrap records
```

# Progressive Project Context Snippet

Use this snippet in agent instructions when the workspace has a shared
`multica-home` repository:

```text
Before substantial work, progressively load shared context from ArkWhale/multica-home instead of reading everything at once:
1. Start with the repo README.
2. If the task is project-specific, read knowledge/projects/<project>.md.
3. If the task spans multiple repos or asks about workspace structure, read knowledge/workspace/leo.md.
4. If you need reusable prompting guidance, read templates/prompts/progressive-project-context.md.
5. Only load the next file when the current task actually needs it.
```

## Intended effect

- lower prompt bloat
- more consistent project naming
- easier reuse across multiple agents

# import2uv Project Summary

## Definition

`import2uv` scans Python repositories for third-party imports, resolves import
names to package names, and drafts dependency installation commands for `uv`.

## Planned capabilities

- AST-based Python import scanning
- standard library filtering
- local-package filtering
- built-in mapping table for common import/package mismatches
- user-provided mapping overrides
- output formats for `uv`, `requirements.txt`, and `pyproject.toml`

## Workspace issue map

- `LEO-13`: project plan
- `LEO-14`: scanner
- `LEO-15`: resolver
- `LEO-16`: draft generator
- `LEO-17`: packaging and release

## Repo mapping

- Product repo: `ArkWhale/import2uv`
- Shared context repo: `ArkWhale/multica-home`

## Notes for agents

- Use the product repo for implementation details.
- Use this summary when you need high-level scope without loading the whole
  issue tree.

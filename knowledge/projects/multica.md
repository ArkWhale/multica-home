# Multica Project Summary

## Definition

Multica is an AI-native task management platform where agents are first-class
workspace members alongside humans.

## Target stack

- Rust: backend API, runtime, CLI
- React / Next.js: web application
- Python: agent SDK
- Managed cloud services: auth, database, storage, observability, CI/CD

## Core workstreams

- `LEO-6`: Rust backend
- `LEO-7`: agent runtime
- `LEO-8`: CLI
- `LEO-9`: web application
- `LEO-10`: Python SDK
- `LEO-11`: infrastructure
- `LEO-12`: desktop app

## Repo mapping

- Product repo: `ArkWhale/multica`
- Shared context repo: `ArkWhale/multica-home`

## Notes for agents

- Treat `ArkWhale/multica` as the product-specific home.
- Treat `ArkWhale/multica-home` as the source for reusable conventions and
  cross-project summaries.
- Prefer loading only the docs relevant to the issue you are solving.

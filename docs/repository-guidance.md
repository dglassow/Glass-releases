# Repository Guidance

## Context

This repository is public. It publishes public Glass release artifacts, documentation, and support-service infrastructure.

Project documentation belongs in `docs/`. Detailed operating instructions for Codex also belong in `docs/`; keep `AGENTS.md` minimal and use it only as an entry point.

## Prerequisites

- Read `AGENTS.md`.
- Read `docs/index.md`.
- Read `docs/change-management.md` before making file changes, commits, branches, pushes, or PRs.
- Check `git status --short` before editing.
- Identify whether the task also needs AWS or domain guidance from `docs/index.md`.

## Instructions

- Treat local credentials, account identifiers, release secrets, and unpublished infrastructure details as sensitive unless they are already intentionally documented for public use.
- Ensure all code, documentation, and infrastructure changes support documentation or public-facing Glass content.
- Keep changes small, reviewable, and scoped to the task.
- Avoid unrelated formatting churn.
- Do not revert user changes. If existing changes affect the task, work with them.
- Keep public decisions and operational context documented in `docs/`.
- Prefer updating existing docs over creating overlapping guidance.
- Do not merge directly to `main`; all changes must be reviewed through a pull request.

## Follow-Ups

- Re-run `git status --short` after changes.
- Confirm `.env` remains ignored if secret handling was involved.
- Update `docs/index.md` whenever adding, renaming, or repurposing documentation files.

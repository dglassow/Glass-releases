# Change Management

## Context

All changes in this repository must support Glass documentation, release artifacts, infrastructure for public content, or other public-facing services.

`main` represents reviewed, deployable public content. Do not commit directly to `main` for normal work. Every change should move through a branch and pull request before merge.

## Prerequisites

- Read `AGENTS.md`.
- Read `docs/index.md`.
- Read `docs/repository-guidance.md`.
- If the change affects deploy automation, read `docs/deployment-guidance.md`.
- If the change affects AWS resources, read `docs/aws-guidance.md`.

## Instructions

- Review all changes through a GitHub pull request before merging to `main`.
- Keep PRs focused and small enough for practical review.
- Use the latest Glass release identifier when naming branches.
- Prefer the latest repository tag for the release identifier. Strip a leading `v` from the tag before using it in the branch name.
- Branch names must use this format:

```text
<glass-release>-<MMDDYY>-<HASH>
```

Example:

```text
0.14.4-041526-AF0C3
```

- `glass-release` is the latest Glass release, for example `0.14.20`.
- `MMDDYY` is the branch creation date in Eastern time.
- `HASH` is a five-character uppercase branch hash using hexadecimal characters.
- For any file changes, create or use a release-named branch, stage the intended changes, commit them, push the branch, and open a PR against `main`.
- Do not stage unrelated local changes.
- Do not merge the PR directly unless the user explicitly asks and review requirements are satisfied.

## Follow-Ups

- Confirm the branch name follows the release-date-hash convention.
- Confirm the PR targets `main`.
- Confirm public docs or deploy-related changes are represented in the PR description.
- After merge, rely on the `main` deployment workflow described in `docs/deployment-guidance.md`.


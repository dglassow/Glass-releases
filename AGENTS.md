# Glass Releases

Public release artifacts, documentation, and support-service infrastructure
for Glass.
Tracks domain registration status, deployment guidance, AWS configuration,
change management, and repository workflow docs.

## Stack

- Documentation-only (Markdown)
- No code

## Layout

- `docs/` - all documentation
  - `index.md` - task routing
  - `domain-plan.md` - domain registration status
  - `deployment-guidance.md` - deployment instructions
  - `change-management.md` - change process
  - `repository-guidance.md` - repo workflow
  - `aws-guidance.md` - AWS configuration

## Key concepts

- **Release-based branch naming** - e.g. `0.14.20-043026-5F520`
- **Docs-driven workflow** - `docs/index.md` is the task routing hub

## How to test

N/A - documentation-only project.
`git diff --check` for validation.

## Conventions

For every task:

1. Define what the task is trying to achieve.
2. Read `docs/index.md`.
3. Use the index to identify relevant tools, instructions, skills,
   prerequisites, and follow-ups.
4. Read the referenced docs before executing the task.
5. Follow those docs and keep detailed instructions in `docs/`, not in this
   file.

## Forge access

Daniel's Mac has trusted ForgeDevice access at
`~/.config/glass-forge/device-session.json`.
For any `forge.glassow.dev` Git or API operation, use the ForgeDevice session
(for Git, a one-shot `http.extraHeader=Authorization: ForgeDevice <...
Do not create or use Forge PATs, deploy URLs, embedded username/password
remotes, or Basic auth for Forge repository access unless Daniel explicitly
asks for that fallback.
If ForgeDevice auth fails, diagnose the trusted-device session or local Forge
service instead of switching to PATs/user-pass.

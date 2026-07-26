# AWS Guidance

## Context

AWS resources for this repository are intended for the Glass release, documentation, and support-service account.

Local AWS credentials may exist in `.env`. That file must remain untracked and must not be printed, copied into docs, or committed.

The local `.env` currently uses lowercase keys:

- `aws_account_name`
- `aws_account_id`
- `aws_access_key`
- `aws_secret_key`

## Prerequisites

- Read `AGENTS.md`.
- Read `docs/index.md`.
- Read `docs/repository-guidance.md`.
- If the task touches domain registration, hosted zones, DNS, or certificates, read `docs/domain-plan.md`.

## Instructions

- Never print, commit, or summarize secret values from `.env`.
- It is acceptable to list variable names when needed, but not values.
- Map local `.env` values to AWS CLI environment variables only inside the shell process:

```sh
set -a
source .env
set +a
export AWS_ACCESS_KEY_ID="$aws_access_key"
export AWS_SECRET_ACCESS_KEY="$aws_secret_key"
export AWS_DEFAULT_REGION=us-east-1
```

- It is acceptable to confirm the target account with `aws sts get-caller-identity`.
- Do not register domains, create hosted zones, or create other billable AWS resources without explicit user approval in the current conversation.
- Record AWS permission gaps and infrastructure decisions in the relevant `docs/` file.

## Follow-Ups

- Verify `.env` is ignored before finishing work involving local credentials.
- Document any new AWS permissions needed to complete a task.
- If AWS resources are created after approval, document names, regions, purpose, and ownership expectations.


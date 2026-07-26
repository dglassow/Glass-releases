# Deployment Guidance

## Context

Merged changes to `main` should become publicly available as soon as possible through a GitHub Actions deployment to AWS.

The deployment workflow should publish only reviewed content from `main`. Branches and pull requests may run validation checks, but production deployment should happen from `main` after merge.

## Prerequisites

- Read `AGENTS.md`.
- Read `docs/index.md`.
- Read `docs/repository-guidance.md`.
- Read `docs/change-management.md`.
- Read `docs/aws-guidance.md`.
- If domains, DNS, certificates, or public URLs are involved, read `docs/domain-plan.md`.

## Instructions

- Use GitHub Actions for deployment automation.
- Trigger production deployment on pushes to `main`.
- Keep PR workflows focused on validation, preview, or dry-run checks.
- Deploy only the changed public documentation, release artifacts, or supporting service infrastructure needed for the merge.
- Prefer GitHub Actions OIDC with an AWS IAM role for deployment credentials.
- Avoid long-lived AWS access keys in GitHub secrets unless OIDC is not available and the tradeoff is documented.
- Use least-privilege IAM permissions for deploy jobs.
- Fail deployments clearly when required AWS resources, domains, certificates, or permissions are missing.
- Document deployment targets, required secrets or roles, and rollback expectations before enabling a production workflow.

## Follow-Ups

- Add or update `.github/workflows/` only when the AWS deployment target and required permissions are defined.
- After deployment automation is added, document the workflow name, trigger, AWS role, target resources, and expected public URLs.
- If a main-branch deployment fails, fix it through a release-named branch and PR.


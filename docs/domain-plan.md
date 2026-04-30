# Domain Plan

Date checked: 2026-04-30

## Context

Establish a public domain for Glass documentation, release links, and support services. The domain should be managed in AWS Route 53 after registration or delegation.

The preferred DNS provider is AWS Route 53. Registration may happen through Route 53 Domains or through another registrar with DNS delegated to a Route 53 public hosted zone.

## Prerequisites

- Read `AGENTS.md`.
- Read `docs/index.md`.
- Read `docs/repository-guidance.md`.
- Read `docs/aws-guidance.md`.
- Confirm explicit user approval before registering a domain, creating a hosted zone, or creating any other billable AWS resource.

## AWS Status

The local `.env` credentials authenticate to the intended AWS account.

The current IAM user can call STS, but it cannot check Route 53 Domains availability:

```text
route53domains:CheckDomainAvailability denied
```

Before registering a domain through AWS, grant the deployment identity the needed Route 53 Domains permissions or complete the registration manually in the AWS console.

## Instructions

- Verify domain availability close to registration time because availability can change.
- Prefer names that can support docs, releases, support links, and future public services.
- Use Route 53 for DNS after the domain is chosen and approved.
- Do not register domains or create hosted zones without explicit user approval in the current conversation.
- When using AWS CLI, follow `docs/aws-guidance.md` for credential handling.
- Record candidate domains, verification method, AWS permissions, and next steps in this file.

## Availability Checks

AWS Route 53 Domains availability checks could not be run because of the IAM permission above. As a fallback, these `.com` candidates were checked against Verisign RDAP at `https://rdap.verisign.com/com/v1/domain/<domain>`. `not registered in .com RDAP` means no current `.com` registration was found at the registry at check time; it is not a purchase guarantee and does not confirm Route 53 pricing, premium status, or registration eligibility.

| Domain | RDAP status |
| --- | --- |
| glass.com | registered |
| glassdocs.com | registered |
| glassreleases.com | not registered in .com RDAP |
| glasssupport.com | registered |
| glasslinks.com | registered |
| getglassdocs.com | not registered in .com RDAP |
| glassappdocs.com | not registered in .com RDAP |
| glassappreleases.com | not registered in .com RDAP |
| glasspublic.com | registered |
| glassdeployments.com | not registered in .com RDAP |
| glassreleasehub.com | not registered in .com RDAP |
| glassdochub.com | not registered in .com RDAP |
| glassreleasecenter.com | not registered in .com RDAP |
| glassdocsportal.com | not registered in .com RDAP |
| glassdocscloud.com | not registered in .com RDAP |
| glassartifacthub.com | not registered in .com RDAP |
| glassartifactportal.com | not registered in .com RDAP |
| glassversionhub.com | not registered in .com RDAP |
| glassupdatehub.com | not registered in .com RDAP |
| glassapphub.com | not registered in .com RDAP |

## Recommended Candidates

1. `glassapphub.com` - broad enough for docs, releases, support links, and future public services.
2. `glassreleases.com` - strongest fit for this repository and public release artifacts.
3. `glassreleasehub.com` - good fallback if a more descriptive release/support domain is preferred.
4. `glassappdocs.com` - useful if the domain should focus mainly on documentation.

## Follow-Ups

1. Pick the final domain.
2. Re-check availability immediately before purchase using AWS Route 53 Domains or the AWS console.
3. Register the domain in Route 53 Domains, or register it elsewhere and delegate DNS to a Route 53 public hosted zone.
4. Create a Route 53 public hosted zone for the domain.
5. Plan initial records:
   - `docs.<domain>` for public documentation.
   - `releases.<domain>` for release artifacts and metadata.
   - `support.<domain>` for support entry points.
   - `<domain>` for a simple landing or redirect target.
6. Add certificate automation through AWS Certificate Manager before attaching CloudFront, API Gateway, or other HTTPS endpoints.

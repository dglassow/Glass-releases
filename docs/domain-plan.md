# Domain Plan

Date checked: 2026-05-03

## Context

Establish a public domain for Glass documentation, release links, and support services. The domain should be human-friendly, readable, and closely tied to the Glass app. Prefer exact-brand domains such as `glass.<tld>` when available.

The preferred DNS provider is AWS Route 53. Registration may happen through Route 53 Domains or through another registrar with DNS delegated to a Route 53 public hosted zone.

## Prerequisites

- Read `AGENTS.md`.
- Read `docs/index.md`.
- Read `docs/repository-guidance.md`.
- Read `docs/aws-guidance.md`.
- Confirm explicit user approval before registering a domain, creating a hosted zone, or creating any other billable AWS resource.

## AWS Status

The local `.env` credentials authenticate to the intended AWS account.

The current IAM user can call STS, but it cannot complete Route 53 domain discovery or availability checks:

```text
route53domains:CheckDomainAvailability denied
route53domains:ListDomains denied
route53:ListHostedZones denied
```

Before registering a domain through AWS, grant the deployment identity the needed Route 53 and Route 53 Domains permissions or complete the registration manually in the AWS console.

## Instructions

- Verify domain availability close to registration time because availability can change.
- Prefer exact-brand names first: `glass.<tld>`.
- If exact-brand names are not viable, prefer very short Glass-relative names such as `go.glass`.
- Avoid long utility names unless all readable exact-brand options are unavailable.
- Prefer names that can support docs, releases, support links, and future public services.
- Use Route 53 for DNS after the domain is chosen and approved.
- Do not register domains or create hosted zones without explicit user approval in the current conversation.
- When using AWS CLI, follow `docs/aws-guidance.md` for credential handling.
- Record candidate domains, verification method, AWS permissions, and next steps in this file.

## Availability Checks

AWS Route 53 Domains availability checks could not be run because of the IAM permission above. As a fallback, candidates were checked against public RDAP. `not registered in RDAP` means no current registration was found at the registry at check time; it is not a purchase guarantee and does not confirm Route 53 pricing, premium status, or registration eligibility.

AWS Route 53 documentation says Route 53 DNS can be used with any TLD, but Route 53 domain registration is limited to supported TLDs. It also says Route 53 cannot register domains that have special or premium pricing. Source: `https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/registrar-tld-list.html`.

The candidates below still need a final Route 53 check before purchase.

### Exact `glass.<tld>` Candidates

| Domain | RDAP status | Route 53 registration note |
| --- | --- | --- |
| glass.cloud | not registered in RDAP | TLD is listed by Route 53. |
| glass.io | registered | TLD is listed by Route 53, but the domain is already registered. |
| glass.co | not registered in RDAP | TLD is listed by Route 53. |
| glass.help | not registered in RDAP | TLD is listed by Route 53. |
| glass.link | not registered in RDAP | TLD is listed by Route 53. |
| glass.site | not registered in RDAP | TLD is listed by Route 53. |
| glass.fyi | not registered in RDAP | TLD is listed by Route 53. |
| glass.app | registered | Best semantic fit, but already registered in RDAP. |
| glass.dev | registered | Already registered in RDAP and not listed in current Route 53 registration docs. |
| glass.ai | registered | Already registered in RDAP. |
| glass.support | registered | Already registered in RDAP. |
| glass.glass | registered | Already registered in RDAP. |

### Short `.glass` Candidates

Route 53 lists `.glass` as a supported TLD. These names use Glass as the extension and keep the second-level label short.

| Domain | RDAP status | Note |
| --- | --- | --- |
| go.glass | not registered in RDAP | Strong short fallback; reads naturally as a product URL. |
| docs.glass | not registered in RDAP | Good for documentation, but less flexible as the root for releases and support. |
| glassapp.glass | not registered in RDAP | Clear, but more repetitive than `go.glass`. |
| download.glass | not registered in RDAP | Useful for releases, but too narrow for all public services. |
| release.glass | not registered in RDAP | Useful for releases, but too narrow for docs and support. |
| public.glass | not registered in RDAP | Broad, but less product-like. |

### Earlier `.com` Candidates

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

Current preferred candidate: `docs.glass`.

1. `docs.glass` - short, direct, and best aligned with the immediate public documentation goal.
2. `go.glass` - broader short fallback using the `.glass` TLD if documentation is not the only root use case.
3. `glass.cloud` - exact Glass name, readable, broad enough for docs/releases/support, and aligned with AWS-hosted public services.
4. `glass.co` - exact Glass name, short, and company-oriented; verify Route 53 price and registration eligibility before purchase.
5. `glass.help` - exact Glass name and support-friendly, but less flexible for release artifacts.

`docs.glass` is the best fit right now because it is concise, human-readable, and directly communicates the first public service this repository is expected to publish. If releases and support need to share the same root later, use subpaths such as `docs.glass/releases` and `docs.glass/support`, or choose the broader `go.glass` before registration.

## AWS Permission Follow-Up

To complete the selection inside AWS Route 53, the deployment identity needs read access for discovery and availability checks:

```text
route53domains:CheckDomainAvailability
route53domains:ListPrices
route53domains:RegisterDomain
route53domains:ListDomains
route53:ListHostedZones
```

Registration and DNS setup will need additional approval and permissions, including Route 53 Domains registration permissions and Route 53 hosted-zone creation or record-management permissions.

## Registration Attempt Notes

### `docs.glass`

Checked on 2026-05-03 before registration. Public RDAP returned `404 Object not found`, and public DNS returned no NS, A, or SOA records. This suggested `docs.glass` was not registered at that time, but it was not a purchase guarantee.

Route 53 availability and pricing could not be checked from the AWS account because `route53domains:CheckDomainAvailability` and `route53domains:ListPrices` are denied. Registration could not be submitted because the AWS identity still needs Route 53 Domains registration permissions and registrant/admin/tech contact details.

Checked again on 2026-05-03 after registration. Public RDAP shows:

- Domain: `docs.glass`.
- Registrar: Amazon Registrar, Inc.
- Registration date: 2026-05-03T18:02:41.806Z.
- Expiration date: 2027-05-03T18:02:41.806Z.
- Status: `add period`, `inactive`.
- Nameservers: none published in RDAP.

Public DNS still returns no NS, A, or SOA records for `docs.glass`, and the `.glass` parent zone does not currently delegate `docs.glass`. This means the domain appears registered but is not publicly delegated to a hosted zone yet.

The current AWS identity still cannot verify the hosted zone inside the AWS account because `route53:ListHostedZonesByName` is denied, and it cannot inspect the domain registration because `route53domains:GetDomainDetail` is denied.

### `glass.io`

Checked on 2026-05-03. `glass.io` cannot be newly registered because it is already registered. Public DNS returns active name servers and an A record, and WHOIS reports:

- Registrar: Gandi SAS.
- Creation date: 2011-10-19.
- Registry expiry date: 2026-10-19.

Route 53 availability and pricing could not be checked from the AWS account because `route53domains:CheckDomainAvailability` and `route53domains:ListPrices` are denied.

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

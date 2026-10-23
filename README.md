# Deku Linux infrastructure

Public, reviewable infrastructure documentation and future operational configuration for Deku Linux.

## Status

**Bootstrap/documentation stage.** No production release service, package repository, signing service, mirror infrastructure, monitoring stack or backup service is configured here. This repository contains security-boundary and deployment guidance; it is not a running infrastructure control plane.

The public static website and its GitHub Pages workflow live in [Deku-Foundation.github.io](https://github.com/Deku-Foundation/Deku-Foundation.github.io). The website's deployment job uses GitHub Pages and OIDC permissions only for the deployment job. A pull-request validation pass is not proof that a production deployment completed.

## Security rules

- Never commit tokens, passwords, private keys, signing keys, recovery codes or secret environment files.
- Use least-privilege service identities and short-lived credentials where supported.
- Keep release signing and publication credentials away from untrusted pull-request builds.
- Require review for deployment and access-control changes.
- Pin external actions and deployment tools to reviewed immutable versions where practical.
- Document ownership, backup, recovery and incident response before operating critical services.
- Keep build, signing and publishing trust domains separate.

## Scope

Future infrastructure work may include signed package repository publication, mirror health, provenance storage, monitoring and release automation. Each service needs a named owner, access model, update procedure, backup/restore test and incident-response plan before becoming a production dependency.

## Documentation checks

The repository has a read-only GitHub Actions workflow that validates Markdown hygiene. It does not deploy services or grant release credentials to pull-request code.

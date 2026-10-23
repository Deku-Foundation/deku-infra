# Deku Linux infrastructure

Public, reviewable infrastructure configuration for Deku Linux project services.

## Status

Bootstrap stage. No production infrastructure or release service is configured here.

## Security rules

- Never commit tokens, passwords, private keys, signing keys, recovery codes, or secret environment files.
- Use least-privilege service identities and short-lived credentials where supported.
- Keep release signing and publication credentials away from untrusted pull-request builds.
- Require review for deployment and access-control changes.
- Pin external actions and deployment tools to reviewed immutable versions where practical.
- Document ownership, backup, recovery, and incident response before operating critical services.

## Scope

Potential future contents include website deployment configuration, monitoring configuration, and public automation. Secrets must be stored in the relevant service's secret manager, not in Git.

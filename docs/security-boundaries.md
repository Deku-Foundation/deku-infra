# Infrastructure trust boundaries

## Public repository rule

Treat every public repository as public forever. Do not store credentials, deployment tokens, private keys, recovery codes, user data, or confidential incident details in commits, issues, Actions logs, or artifacts.

## Workflow permissions

- Declare explicit minimum permissions in every workflow.
- Use read-only permissions for checks that only inspect source.
- Separate test/build workflows from deployment and signing workflows.
- Do not expose deployment secrets to fork pull requests or untrusted branches.
- Pin third-party Actions to reviewed immutable commit SHAs.
- Review changes to workflows and deployment configuration as security-sensitive code.

## Website deployment boundary

The dedicated website repository is `Deku-Foundation/Deku-Foundation.github.io`. Its `.github/workflows/pages.yml` workflow performs pull-request validation without publishing. The deployment job is gated to pushes to `main` and receives the Pages and OIDC permissions only at job level. Keep that separation intact: pull-request code must never run with deployment permissions. Confirm the default-branch deployment itself succeeds before describing a site revision as published.

## Operational readiness

Before a service is production-facing, document its owner, access model, update process, backup scope, restore test, monitoring, and incident response procedure. If no one can maintain or recover a service, do not make it a critical dependency.

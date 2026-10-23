# Infrastructure trust boundaries

## Public repository rule

Treat every public repository as public forever. Do not store credentials, deployment tokens, private keys, recovery codes, user data, or confidential incident details in commits, issues, Actions logs, or artifacts.

## Workflow permissions

- Declare explicit minimum `permissions` in every workflow.
- Use read-only permissions for checks that only inspect source.
- Separate test/build workflows from deployment and signing workflows.
- Do not expose deployment secrets to fork pull requests or untrusted branches.
- Pin third-party Actions to reviewed immutable commit SHAs.
- Review changes to workflows and deployment configuration as security-sensitive code.

## Operational readiness

Before a service is production-facing, document its owner, access model, update process, backup scope, restore test, monitoring, and incident response procedure. If no one can maintain or recover a service, do not make it a critical dependency.

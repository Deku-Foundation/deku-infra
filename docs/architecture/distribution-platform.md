# Deku Distribution Infrastructure

Status: architecture specification only. No production registry, build farm, signing service or mirror exists.

## Logical services

- Recipe review: immutable source/patch pins, license expression and declared outputs.
- Source fetcher: network access only here, strict redirect/address policy and digest verification.
- Build worker: disposable VM, pinned environment, no credentials, no network by default during compilation.
- Artifact verifier: bounded archive parsing, path validation, manifest/SBOM/provenance checks and tests.
- Repository publisher: immutable content-addressed artifact storage and authenticated, expiring repository metadata.
- Signing authority: separate identities/roles, offline root or external signing service, key rotation/revocation runbooks.
- Client: verifies trust metadata before artifact bytes, solves dependencies, builds a reviewable transaction plan, stages changes and supports recovery.
- Release controller: promotion gates and evidence bundle; no publish permission on package build workers.

## Security boundaries

1. Treat recipe, patch and compiler code as malicious input; review alone is not a sandbox.
2. Keep secrets out of package build jobs, pull request workflows and artifacts.
3. Containers share the host kernel; production isolation should use disposable VMs or an equivalent reviewed boundary.
4. Separate network-enabled source acquisition from offline compilation.
5. Do not mistake checksum integrity for publisher authenticity.
6. Mirrors are transport only. Clients verify metadata and freshness even on an official mirror.
7. Every install/update operation needs a durable transaction journal and an interruption-recovery test.
8. Before production, every service needs an owner, privilege model, failure mode, monitoring signal, backup plan and restore test.

## Source reuse

Record exact upstream revision, license, required notices, copied files, local modifications, dependency licenses, patch rebase procedure and security owner for each imported project. This is especially important for Anaconda (GPL-2.0) and downstream source patches. Code licensing does not automatically license logos or third-party assets.

## Non-goals now

- No Fedora ISO production.
- No public package repository or release service yet.
- No production signing keys or credentials in this repository.
- No reproducibility claim before independent outputs are compared.

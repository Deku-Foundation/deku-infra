# Build, Sign and Publish Trust Boundaries

Status: policy for future CI; not a deployed production service.

## Separate identities
- Pull-request validation: no secrets, no release permissions.
- Package build workers: disposable, unprivileged and without signing credentials.
- Artifact verification: validates hashes, manifests, SBOM and provenance.
- Release approval: protected environment with review and short-lived identity.
- Signing: isolated external key service or offline-controlled process; never store private keys in Git.
- Publication: narrowly scoped permission to upload only approved, verified artifacts.

## Supply-chain evidence
Every release candidate should bind source commit, recipe/profile revision, builder/toolchain versions, package inputs, output digests, test results, SBOM and provenance. Verify upstream signatures where available and preserve license attribution.

## Image-builder privilege exception

Some upstream image tools, including the experimental Lorax no-virt path, may require elevated mount privileges. This is not permission to run untrusted package recipes as root. Such an image job must run on an ephemeral isolated runner, receive no secrets, avoid pull-request triggers, use only reviewed Kickstart/profile inputs, and retain logs. A privileged container is a temporary prototype boundary, not the desired long-term production design; move image assembly into a dedicated disposable VM/worker or a narrower capability set before producing trusted releases.

## Fail-closed behavior
A missing digest, unknown signing identity, unpinned input, failed test, absent provenance or mismatch blocks promotion. A checksum alone proves byte identity, not publisher identity.

## GitHub Actions
Use least-privilege workflow permissions, pin third-party actions to reviewed full commit SHAs where practical, avoid secrets in fork/PR jobs, and require protected-environment approval for publication. This document is a design contract; settings and workflows still need implementation and verification.

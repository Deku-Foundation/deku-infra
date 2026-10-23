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

## Fail-closed behavior
A missing digest, unknown signing identity, unpinned input, failed test, absent provenance or mismatch blocks promotion. A checksum alone proves byte identity, not publisher identity.

## GitHub Actions
Use least-privilege workflow permissions, pin third-party actions to reviewed full commit SHAs where practical, avoid secrets in fork/PR jobs, and require protected-environment approval for publication. This document is a design contract; settings and workflows still need implementation and verification.

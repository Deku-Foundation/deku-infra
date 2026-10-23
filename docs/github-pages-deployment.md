# Standalone Deku Linux website on GitHub Pages

**Status:** The dedicated Pages repository exists at [Deku-Foundation.github.io](https://github.com/Deku-Foundation/Deku-Foundation.github.io). Its main branch contains the static website and a pinned GitHub Actions workflow. The workflow validates pull requests and only publishes from a push to the protected default branch. A successful pull-request check is not, by itself, proof that the production deployment completed.

## Repository and public URL

Use the dedicated organization site repository, `Deku-Foundation.github.io`, so the public website remains separate from package recipes, build automation and infrastructure configuration. The configured canonical hostname in the site source is `https://deku-foundation.github.io/`.

Do not add a custom-domain CNAME until the organization has registered and controls the domain, verified its DNS configuration, and agreed on ownership and recovery.

## Deployment model

- Static site using semantic HTML, CSS and minimal JavaScript; no backend or analytics by default.
- Build-free deployment from the protected default branch.
- The workflow at `.github/workflows/pages.yml` runs link/basic-metadata validation and JavaScript syntax checks for pull requests.
- The deployment job is skipped for pull requests and runs only for a push to `main`, after validation succeeds.
- Use least-privilege permissions: read-only contents for validation, and Pages write plus OIDC token permissions only for the deployment job.
- Pin third-party GitHub Actions to reviewed immutable commit SHAs, with version comments.
- Never expose deployment credentials to untrusted pull-request code. GitHub's Pages OIDC flow should be preferred over long-lived deployment secrets.

## Visual direction and public claims

- Clean, modern, editorial layout with accessible contrast, strong typography and generous whitespace.
- Neutral background, dark ink and a restrained accent color.
- Responsive navigation, clear project status, architecture principles, security approach, roadmap and source links.
- Label the distribution as in development. Do not publish fake download links, version numbers, performance claims, security badges or release dates before the supporting artifacts and test evidence exist.
- Respect reduced-motion preferences and support keyboard navigation, visible focus, semantic landmarks and descriptive link text.

## Deployment verification checklist

- [x] Dedicated `Deku-Foundation.github.io` repository exists.
- [x] Static website and pinned Pages workflow are present on the default branch.
- [x] Pull-request validation and deploy-job gating are defined in the workflow.
- [ ] Verify a default-branch Actions run completes the **Publish to GitHub Pages** job successfully after the latest merge.
- [ ] Open the public URL and check the deployed homepage, documentation, 404 page and static assets.
- [ ] Test mobile and desktop layouts, keyboard navigation, contrast, broken links and 404 behavior.
- [ ] Confirm the sitemap and canonical URL match the intended public host.
- [ ] Configure a custom domain only after DNS ownership and recovery procedures are verified.

Do not mark deployment complete based only on the pull-request CI result. Record the successful default-branch deployment run and the URL that was checked.

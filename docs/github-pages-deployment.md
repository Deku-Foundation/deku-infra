# Standalone Deku Linux website on GitHub Pages

**Status:** Proposed deployment plan. No website repository or live site is configured yet.

## Repository choice

Use a dedicated organization user-site repository named `Deku-Foundation.github.io`. This keeps the public website independent from project governance, package templates, build automation, and infrastructure configuration. The canonical organization Pages hostname will be `https://deku-foundation.github.io/` (GitHub's hostname uses the organization login; confirm exact casing and availability in repository settings).

If the project later adopts a custom domain, configure it only after domain ownership and DNS are verified. Do not commit a `CNAME` file with a domain that has not been registered and controlled by the organization.

## Deployment model

- Static site: semantic HTML, modern CSS, and minimal JavaScript; no backend or analytics by default.
- Build from the website repository's protected default branch.
- Deploy with GitHub Actions using the official Pages deployment flow and least-privilege `contents: read`, `pages: write`, and `id-token: write` permissions only where required.
- Restrict deployment to the protected default branch and use GitHub's Pages environment protection where available.
- Pin third-party actions to reviewed immutable commit SHAs and keep version comments for maintainers.
- Run accessibility, link, and HTML checks before deployment.
- Do not use untrusted pull-request code in jobs that have deployment permissions.

## Visual direction

- Clean, modern, editorial layout with strong typography and generous whitespace.
- Neutral background, dark ink, one restrained green accent, and accessible contrast.
- Responsive navigation, clear primary call to action, concise project status, architecture principles, security approach, roadmap, and links to source repositories.
- Show that the project is early-stage. Do not display download buttons, version numbers, performance claims, security badges, or release dates until those claims are real and verifiable.
- Respect reduced-motion settings and support keyboard navigation, visible focus, semantic landmarks, and descriptive link text.

## Go-live checklist

- [ ] Create the dedicated `Deku-Foundation.github.io` repository and initialize its default branch.
- [ ] Add the reviewed static site and pinned Pages workflow.
- [ ] Enable GitHub Pages with GitHub Actions as the source.
- [ ] Confirm the Actions deployment succeeds and inspect the published URL.
- [ ] Test mobile layout, keyboard navigation, contrast, broken links, and 404 behavior.
- [ ] Add a custom domain only after DNS and ownership are verified.

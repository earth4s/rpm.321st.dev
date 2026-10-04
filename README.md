# rpm.321st.dev

Static website for the 321st RPM repository.

Website: https://rpm.321st.dev/

## Structure

- `index.html`: homepage.
- `packages/index.html`: package listing; add explicit links as packages are published.
- `assets/css/main.css`: shared stylesheet.
- `assets/js/main.js`: optional browser JavaScript.
- `assets/images/` and `assets/fonts/`: local assets.
- `404.html`: custom error page.
- `favicon.svg`: site icon.
- `robots.txt` and `sitemap.xml`: crawler configuration.
- `CNAME`: custom domain.
- `.nojekyll`: serve plain static files without Jekyll.

## Hosting

GitHub Pages should publish the `main` branch from `/(root)`, with custom domain
`rpm.321st.dev` and HTTPS enabled.

Cloudflare DNS for `321st.dev`: CNAME `rpm` pointing to `earth4s.github.io`.
Do not add the repository name to the DNS target.

There is no build step or deployment workflow required for this layout.

## Local preview

From the repository root, use a static HTTP server, for example:

```bash
python3 -m http.server 8000
```

Open http://localhost:8000/ in a browser.

## Publishing packages

Place package files in `packages/` and add download links to
`packages/index.html`. GitHub Pages does not generate directory listings.

This starter structure does not yet provide DNF/YUM metadata or signing keys.
Before advertising it as an installable RPM repository, generate valid
`repodata/` with `createrepo_c`, publish the intended signing key and repository
configuration, and document supported distributions and architectures.

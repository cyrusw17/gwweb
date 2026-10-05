# gwweb: the live groundwork-web.com

This repo is what cPanel deploys. It is a built copy of `public/` from
[cyrusw17/GWAGENCY](https://github.com/cyrusw17/GWAGENCY) (built from 7bfac5e with
`node tools/build-cpanel.mjs`). Don't edit pages here; change them in GWAGENCY and rebuild.

- `site/` is the website.
- `.cpanel.yml` tells cPanel to run `deploy.sh` on "Deploy HEAD Commit".
- `deploy.sh` backs up public_html to ~/site-backups (keeps 10), replaces only the folders
  the site owns, and leaves everything else alone (api/config.php, .well-known, cgi-bin,
  any private folder).
- Every page is a folder on groundwork-web.com (for example /auto-detailing/ and /auto-detailing/blog/). No subdomains are needed.

Undo a deploy in cPanel Terminal:
`cd ~ && rm -rf public_html && tar -xzf site-backups/public_html-YYYYMMDD-HHMMSS.tar.gz`

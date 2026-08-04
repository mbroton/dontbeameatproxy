# dontbeameatproxy.net

Please don't copy-paste AI answers at people.

A [nohello.net](https://nohello.net/)-style single page for the problem described in
["don't be a meat proxy"](https://gruhn.me/blog/2026-08-03/): relaying AI output to
others without reading, understanding, or checking it first.

## Structure

- `index.html` — the whole site: one page, inline CSS, no build step, no dependencies.

## Deploy

Any static host works. For GitHub Pages: push to `main`, enable Pages
(deploy from branch, root), set `dontbeameatproxy.net` as the custom domain, and point
the domain's DNS at GitHub Pages
(A records + `www` CNAME per the [GitHub docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)).

## Scope

Deliberately minimal — one HTML file, no framework, no analytics. Translations or
extra examples can come later if the page gets traction.

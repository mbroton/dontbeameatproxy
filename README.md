# Don't be a meat proxy

https://dontbeameatproxy.com/

## Hosting and fonts

This is a static Cloudflare Pages site. The deployment workflow uploads the
repository, including `fonts/` and `_headers`.

The page loads Bricolage Grotesque and Lato from this site. It makes no requests to
Google Fonts. The three WOFF2 files total 123,508 bytes (about 121 KiB). Their
sources and licenses are in [fonts/README.md](fonts/README.md).

```text
Browser --> Cloudflare Pages
            |-- index.html
            `-- fonts/*.woff2
```

On the Pages free plan, [static asset requests are free and unlimited](https://developers.cloudflare.com/pages/functions/pricing/),
and [bandwidth is unlimited](https://www.cloudflare.com/products/pages/).
These font requests do not use the Workers limit of 100,000 requests per day
because the site has no Functions or Worker. No R2 or KV storage is needed.
The added files are well below the [Pages limits](https://developers.cloudflare.com/pages/platform/limits/)
of 20,000 files per site and 25 MiB per file. These limits were checked on
2026-09-28.

`_headers` lets browsers cache the fonts for one year. Font filenames contain
the first 12 characters of their SHA-256 hash. When you replace a font, update
its filename and the URL in `index.html` so browsers load the new version.

## Local preview

Run `python3 -m http.server 8000` and open <http://localhost:8000>.
To also check the Cloudflare cache headers, use `npx wrangler pages dev .`.
In browser developer tools, reload with the Network tab open. The document and
three font requests must use the local origin, with no Google Fonts requests.

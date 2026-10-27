# orangesai.com

The homepage of Orange Feng — a single static page served by GitHub Pages.

```
index.html   the whole site (edit this)
CNAME        custom domain: orangesai.com
.nojekyll    serve files as-is, skip Jekyll
```

## Edit

Everything lives in `index.html`. The page started as pandoc output, so the CSS is
inline in `<head>` and there is no build step.

Add a project by appending one `<li>` to the matching list:

```html
<li><p><strong><a href="https://example.com">Name</a></strong> — one line about it.</p></li>
```

Push to `main` and GitHub Pages redeploys in ~30s.

## DNS (Cloudflare)

| Type  | Name         | Content                | Proxy    |
|-------|--------------|------------------------|----------|
| CNAME | `orangesai.com` | `orange2ai.github.io` | DNS only |
| CNAME | `www`        | `orangesai.com`        | DNS only |

Keep the proxy **off** (grey cloud) so GitHub can issue and renew the Let's Encrypt
certificate for the custom domain. Proxying can be turned back on afterwards — set
SSL/TLS mode to **Full (strict)** before you do.

# 8-bit Obscura

A Hugo-powered archive of obscure 8-bit games, bootlegs, and mostly Taiwan related video game articles.

Built with [Hugo](https://gohugo.io/) and the [Blowfish](https://github.com/nunocoracao/blowfish) theme.


## Getting Started

### 1. Clone the repo (with theme)

```bash
git clone --recurse-submodules https://github.com/daveflynn/8bitobscura.com.git
cd 8bitobscura.com
```

If you already cloned it without submodules:

```bash
git submodule update --init --recursive
```

---

## Build the Site

You’ll need [Hugo Extended](https://github.com/gohugoio/hugo/releases) installed.

```bash
hugo
```

The site will be generated in the `public/` directory.

---

## Deployment

Hosted on Cloudflare Workers (static assets), configured by `wrangler.jsonc`.
Every push to `main` builds and deploys automatically; other branches get preview URLs.

Cloudflare project settings (Workers & Pages → `8bitobscura-com` → Settings → Build):

| Field | Value |
| :-- | :-- |
| Build command | `git submodule update --init --recursive && hugo --gc --minify` |
| Deploy command | `npx wrangler deploy` |
| Build variable | `HUGO_VERSION` = `0.148.2` (Blowfish v2.88 supports Hugo 0.137–0.148) |

Emergency / local deploy:

```bash
hugo --gc --minify && npx wrangler deploy
```

`www.8bitobscura.com` 301-redirects to the apex via a zone Redirect Rule
(Rules → Redirect Rules), so only the apex is a custom domain.

Roll back: Workers & Pages → `8bitobscura-com` → Deployments → Rollback.

> `routes` in `wrangler.jsonc` is authoritative: every hostname the site serves on
> must be listed there, or the next deploy deletes its custom domain and DNS record.

---

## 🔐 License

All content © 2025 Dave Flynn. All rights reserved.

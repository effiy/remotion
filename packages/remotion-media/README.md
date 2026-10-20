---
title: "@remotion/remotion-media"
tags: [remotion, media, test-fixtures, catalog, cloudflare]
category: tools
created: 2026-10-20
updated: 2026-10-20
source: external
type: index
status: stable
lifecycle: active
---

# @remotion/remotion-media

Private package hosting [remotion.media](https://remotion.media): test media fixtures and a catalog UI.

---

## 💡 概述

Private package hosting [remotion.media](https://remotion.media): test media fixtures and a catalog UI. Provides a web-based catalog of test media files used by Remotion's rendering pipeline, hosted on Cloudflare R2.

---

## ⚡ 功能

- **Development server**: Bun-based local dev server (`src/index.tsx`)
- **Test media generation**: Renders base compositions from `src/compositions/` and writes variants to `files/` (gitignored), then updates `variants.json`
- **Build and deploy**: Bundles catalog UI, generates `llms.txt`, `robots.txt`, and `sitemap.xml`, uploads to Cloudflare R2
- **Content negotiation**: Serves both HTML (browsers) and Markdown (AI agents) from the same URL via Cloudflare Rules

---

## 📊 指标

「待补充」

---

## 🏛️ 设计

Production is served directly from the Cloudflare R2 bucket `parser-media`; the Bun server in `src/index.tsx` is only used locally. Cloudflare Rules mirror its content negotiation for requests to `https://remotion.media/`.

The conditional URL Rewrite Rule runs after the existing `/` to `/index.html` rewrite and rewrites the path to `/llms.txt` when this expression matches:

```txt
raw.http.request.uri.path eq "/" and http.request.method in {"GET" "HEAD"} and (http.user_agent contains "Claude-User" or http.user_agent contains "opencode" or any(http.request.headers["accept"][*] contains "text/markdown") or any(http.request.headers["accept"][*] contains "text/x-markdown") or (any(http.request.headers["accept"][*] contains "text/plain") and not any(http.request.headers["accept"][*] contains "text/html")))
```

Additional Cloudflare Rules for the root path:
- A Response Header Transform Rule sets `Vary: Accept, User-Agent`
- A Response Header Transform Rule sets `Content-Type: text/markdown; charset=utf-8` using the negotiation expression above
- A Cache Rule bypasses caching to avoid collisions between HTML and Markdown representations

---

## 📁 目录

「待补充」

---

## 🔗 资源

- [remotion.media](https://remotion.media)

---

## 🚀 快速开始

### Development

```bash
bun install
cd packages/remotion-media
bun run dev
```

### Generate test media

Requires `ffmpeg` on your PATH. Renders base compositions from `src/compositions/` and writes variants to `files/` (gitignored), then updates `variants.json`.

```bash
bun run generate
```

Place `multiple-audio-streams.mov` in the package root before running `generate` if you want that edge-case fixture included in the catalog.

### Build and deploy

Bundles and pre-renders the catalog UI, generates `llms.txt`, `robots.txt`, and `sitemap.xml`, and uploads everything to Cloudflare R2 when `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` are set:

```bash
bun run build
```

HLS files are uploaded through the AWS CLI so their MIME types are preserved.

### Verify deployment

```bash
curl -I -H 'Accept: text/html' https://remotion.media/
curl -I -H 'Accept: text/markdown' https://remotion.media/
curl -I -A 'Claude-User' https://remotion.media/
curl -I https://remotion.media/llms.txt
curl -I https://remotion.media/robots.txt
curl -I https://remotion.media/sitemap.xml
```

---

## ⚙️ 技术栈

- **Runtime**: Bun
- **Hosting**: Cloudflare R2 (`parser-media` bucket)
- **Content negotiation**: Cloudflare Rules
- **Test media generation**: ffmpeg
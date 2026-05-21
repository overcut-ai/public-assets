# overcut-ai/public-assets

Publicly hosted assets for Overcut. Files in this repo are served via
[jsDelivr](https://www.jsdelivr.com/) at a stable, cacheable CDN URL.

Anything checked in here is **publicly readable**. Don't add secrets,
unbuilt source, or anything you wouldn't put behind a `view-source` lookup.

## Catalog

| File | Description |
|---|---|
| `hero-embed.global.js` | Self-contained IIFE JavaScript bundle of the Overcut hero animation. ~466 KB raw / ~152 KB gzipped. |

## jsDelivr URLs

```text
# Pinned to a release tag (immutable, cached ~1 year)
https://cdn.jsdelivr.net/gh/overcut-ai/public-assets@<tag>/<file>

# Floating on main (cached ~7 days; can be purged via purge.jsdelivr.net)
https://cdn.jsdelivr.net/gh/overcut-ai/public-assets@main/<file>
```

Always prefer a pinned tag for production references.

## Releases

| Tag | Date | Notes |
|---|---|---|
| `v1.1.0` | 2026-05-21 | `hero-embed.global.js` composition canvas shrunk from 1920×1080 to 1280×720 so the animation reads at a larger size inside small page containers. |
| `v1.0.0` | 2026-05-21 | Initial release. `hero-embed.global.js`. |

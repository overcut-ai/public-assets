# overcut-ai/public-assets

Publicly hosted assets for Overcut. Files in this repo are served via
[jsDelivr](https://www.jsdelivr.com/) at a stable, cacheable CDN URL.

## Catalog

| Path | Description |
|---|---|
| `hero-embed.global.js` | Self-contained IIFE JavaScript bundle of the Overcut hero animation. ~478 KB raw / ~155 KB gzipped. All brand logos used by the hero are inlined as base64 data URLs inside the bundle — no sibling assets required. |

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
| `v1.4.0` | 2026-05-21 | Brand logos are now **inlined into the bundle** as base64 data URLs. Removes the need for a separate `static/brand-logos/` directory and any version-pinned `window.*` overrides — the bundle is fully self-contained and ships with zero external asset dependencies. `static/brand-logos/` removed from this repo (still present in older tags' history). |
| `v1.3.0` | 2026-05-21 | Earlier attempt at the brand-logo fix — introduced a `window.__overcut_brandLogoBase` override pinned to this repo's tag. Superseded by v1.4.0's inlining, which avoids the cross-version URL coupling. |
| `v1.2.0` | 2026-05-21 | Adds `static/brand-logos/` so MCP card icons resolve when the bundle runs on a non-Webflow / non-CDN-aware host. Bundle now sets `window.remotion_staticBase` to this repo's `static/` URL before mounting. **Note:** brand logos still 404 under `@remotion/player` due to the upstream staticFile bug — fixed in v1.3.0. |
| `v1.1.1` | 2026-05-21 | Re-tag of v1.1.0 at the rebased HEAD (v1.1.0 ended up on an orphan commit). Bundle content identical to v1.1.0. |
| `v1.1.0` | 2026-05-21 | `hero-embed.global.js` composition canvas shrunk from 1920×1080 to 1280×720 so the animation reads at a larger size inside small page containers. |
| `v1.0.0` | 2026-05-21 | Initial release. `hero-embed.global.js`. |

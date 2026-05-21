# overcut-ai/public-assets

Public CDN-hosted assets for the Overcut website. Files in this repo are
served via [jsDelivr](https://www.jsdelivr.com/) so they can be embedded
into Webflow (or any other site) by a `<script>` or `<link>` tag.

Anything checked in here is **publicly readable**. Don't add secrets,
unbuilt source, or anything you wouldn't put behind a `view-source` lookup.

## Contents

| File | Source | Use |
|---|---|---|
| `hero-embed.global.js` | `overcut-videos` → `dist/hero-embed.global.js` (built with `npm run build:hero-embed`) | Website hero animation. Self-contained IIFE bundle: React + ReactDOM + `@remotion/player` + the v2 component library + the `HeroJourney` scene. Auto-mounts into any `#overcut-hero` placeholder div on the host page. |

## jsDelivr URLs

Pin to a specific tag for production embeds — `@main` will follow `main`
and break if a future change is incompatible.

```text
# Pinned to a release (recommended for production)
https://cdn.jsdelivr.net/gh/overcut-ai/public-assets@v1.0.0/hero-embed.global.js

# Floating on main (fine for development, risky for production)
https://cdn.jsdelivr.net/gh/overcut-ai/public-assets@main/hero-embed.global.js
```

## Embedding in Webflow

In Site Settings → Custom Code → Footer Code (loads on every page):

```html
<script src="https://cdn.jsdelivr.net/gh/overcut-ai/public-assets@v1.0.0/hero-embed.global.js" defer></script>
```

Then, on any page where you want the hero to appear, drop a Custom Embed
block containing:

```html
<div id="overcut-hero" style="width:100%;aspect-ratio:16/9;"></div>
```

The bundle auto-mounts the animation into the div. If a page doesn't
include the placeholder, the script silently no-ops.

For manual mounts into a non-default selector:

```js
window.OvercutHero.mount({ selector: "#my-hero" });
window.OvercutHero.unmount("#my-hero");
```

## Updating the hero bundle

The source for `hero-embed.global.js` lives in the `overcut-videos` repo.
To ship a new version:

1. In `overcut-videos`, edit whatever needs changing (scene, components,
   timing, etc.) and run `npm run build:hero-embed` to regenerate
   `dist/hero-embed.global.js`.
2. Copy the new file over `hero-embed.global.js` in this repo.
3. Commit + tag a new version (`git tag v1.x.y && git push origin v1.x.y`).
4. Update the version in the Webflow Custom Code footer snippet.

jsDelivr caches each tag for ~12 months and `@main` for ~7 days. To force
a refresh while testing on `@main`, use the purge endpoint:
`https://purge.jsdelivr.net/gh/overcut-ai/public-assets@main/hero-embed.global.js`

# UKD Jellyfin for Skin Manager

Legacy integration. The recommended path is now JellyFrame using `jellyframe/themes.json`.

Use this theme repository URL in the updated Jellyfin-PG Skin Manager:

```text
https://raw.githubusercontent.com/TorrelUKD/UKD-Jellyfin-skin/main/skin-manager/skins.json
```

This URL only reflects local changes after the repository is pushed to GitHub.

CSS URL used by the theme entry:

```text
https://cdn.jsdelivr.net/gh/TorrelUKD/UKD-Jellyfin-skin@main/dist/ukd-jellyfin.css
```

The local `Elms Sans` files are referenced from the CSS with absolute jsDelivr URLs pointing to this repository. This avoids broken relative paths after Skin Manager caches and serves the CSS through its local resource endpoint.

After changing the theme repository or updating CSS:

1. Open `Dashboard > Skin Manager`.
2. Set/select `UKD Jellyfin`.
3. Click `Save & Apply`.
4. Clear Skin Manager offline cache if needed.
5. Hard-refresh Jellyfin Web with `Ctrl+Shift+R`.

Notes:

- `Colecciones` should stay hidden through Jellyfin configuration, not CSS.
- Library names baked into library images cannot be removed by CSS. Replace the library artwork in Jellyfin with clean images.
- The CSS fallbacks for `A continuacion` and `ANADIDOS RECIENTES` are structural/visual only until a future API/plugin home replaces Jellyfin's native home sections.

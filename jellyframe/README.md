# UKD Jellyfin for JellyFrame

Use this theme repository URL in JellyFrame:

```text
https://raw.githubusercontent.com/TorrelUKD/UKD-Jellyfin-skin/main/jellyframe/themes.json
```

This URL only reflects local changes after the repository is pushed to GitHub.

Theme CSS URL:

```text
https://cdn.jsdelivr.net/gh/TorrelUKD/UKD-Jellyfin-skin@main/dist/ukd-jellyfin.css
```

Install and apply:

1. Install `File Transformation` and `JellyFrame`.
2. Restart Jellyfin.
3. Open `Dashboard > Themes > Marketplace`.
4. Paste the `themes.json` URL above.
5. Click `Load Themes`.
6. Click `Apply` on `UKD Jellyfin`.
7. Adjust variables if desired.
8. Click `Save & Apply`.
9. Hard-refresh Jellyfin Web with `Ctrl+Shift+R`.

If changes do not appear, purge the theme cache:

```text
Dashboard > Themes > Settings > Theme Cache > Purge
```

Notes:

- JellyFrame uses `themes.json`, not `skins.json`.
- Variables use `SCREAMING_SNAKE_CASE` keys. JellyFrame exposes them as CSS custom properties such as `--ukd-card-scale`.
- `Hide Next Up` and `Rename recent rails` are optional addons controlled by boolean variables.
- `Colecciones` should stay hidden through Jellyfin configuration, not CSS.
- Library names baked into library images cannot be removed by CSS. Replace the library artwork in Jellyfin with clean images.

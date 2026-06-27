# UKD Jellyfin - Project Handoff

## Project Summary

UKD Jellyfin is a custom Jellyfin skin/theme project for Jellyfin Server/Web `10.11.10`, running as a TrueNAS app. The target experience is a serious, cinematic interface for a media library containing movies, series, anime movies and anime series.

Primary target:

- Jellyfin Web.
- TV browser usage.
- Remote-control navigation.

Secondary target:

- Android TV, with limited confidence because Android TV may not consume Jellyfin Web CSS in the same way.

## User Preferences

- Project name: `UKD Jellyfin`.
- Visual tone: serious/cinematic.
- Content types: movies, series, anime movies, anime series.
- Background behavior: use Jellyfin backdrop imagery.
- Card density: middle ground between large posters and many visible items.
- TV input: remote control.
- Animations: almost none.
- CSS aggressiveness: aggressive, but stable.
- Assets: `Elms Sans` is local under `assets/fonts/elms-sans/`, extracted from the Google Fonts zip provided by the user. The CSS references those repo files through absolute jsDelivr URLs to avoid broken relative paths when JellyFrame serves cached CSS from its local endpoint. It does not use Google Fonts.
- Initial delivery: organized project plus one paste-ready CSS file.

## Current Project Location

```text
/home/ukd-studio-ubuntu/Documentos/SKIN CUSTOM JELLYFIN
```

## Current Structure

```text
SKIN CUSTOM JELLYFIN/
  README.md
  PROJECT-HANDOFF.md
  ai-skills/
    accessibility-reviewer.md
    css-maintainer.md
    jellyfin-theme-engineer.md
    responsive-tv-qa.md
    visual-identity-designer.md
  assets/
    fonts/
    icons/
    images/
  dist/
    ukd-jellyfin.css
  docs/
    ai-skills.md
    compatibility.md
    feature-limits.md
    install.md
  themes/
    anime-cinema.css
    arcade-minimal.css
    base.css
    neon-noir.css
```

## Current Version

Current CSS version: `0.4.0`.

Paste-ready CSS:

```text
dist/ukd-jellyfin.css
```

Source CSS:

```text
themes/base.css
themes/neon-noir.css
themes/anime-cinema.css
themes/arcade-minimal.css
```

The active build uses the `Neon Noir` direction with a `Projection Room` identity pass layered on top.

## Visual Directions

Three visual variants were created:

- `Neon Noir`: recommended/current direction. Black cinematic UI with cyan/violet accents and later Crunchyroll-like orange accents.
- `Anime Cinema`: warmer, anime-friendly, pink/orange accents.
- `Arcade Minimal`: more geometric, green/cyan accents, cleaner visual weight.

## Current CSS Goals

The CSS currently attempts to:

- Use backdrop imagery as atmosphere.
- Darken the UI heavily.
- Improve readability on TV.
- Add stronger focus states for remote navigation.
- Increase card presence.
- Use a Crunchyroll-inspired home layout style.
- Make hover/focus effects larger and more visible.
- Reduce clipped hover/focus effects in carousels.
- Hide `A continuacion` / Next Up.
- Make `Mis contenidos` library labels larger below each image.
- Hide possible text overlays inside library images.

## Important CSS Notes

The `0.2.0` override block starts near the end of `dist/ukd-jellyfin.css` and is labeled:

```css
/* UKD 0.2.0 - Crunchyroll-inspired home refinements. */
```

It includes rules for:

- Crunchyroll-like orange accent.
- Larger home section headings.
- Bigger card hover/focus scale.
- Library cards scaling more aggressively.
- `overflow: visible` to avoid clipped hover/focus states.
- No longer hides home sections in the base CSS.

The `0.3.0` override block is layered after `0.2.0` and is labeled:

```css
/* UKD 0.3.0 - Projection room identity pass. */
```

It adds:

- A projector-room palette: near-black ink, deep screen blue, velvet violet, projector amber, soft amber and cyan cue light.
- Condensed display typography using local/system font stacks only, no CDN.
- A fixed left projector slit as the main visual signature.
- Section-title slits and rail divider lines.
- Asymmetric card corners and stronger remote-focus treatment with a left amber light bar.
- A warmer progress/play accent while preserving the existing Jellyfin backdrop atmosphere.

The `0.3.1` stabilization block is layered after `0.3.0` and is labeled:

```css
/* UKD 0.3.1 - Browser stability fixes before theme packaging. */
```

It adds:

- Header/tab overflow fixes to avoid clipped focus pills and icons in browser.
- Extra spacing for section-title slits so `MIS CONTENIDOS` does not clip the visual marker.
- Broader HTML-overlay hiding for library cards in `Mis contenidos`.
- Structural fallbacks for `A continuacion` and recent rail titles were moved to JellyFrame addons in `0.4.0`.

Important stabilization decision:

- The user successfully removed `Colecciones` from the home/list using Jellyfin configuration. Do not hide `Colecciones` with CSS unless explicitly requested later.
- If library names still appear inside images after the HTML-overlay rules, the text is likely baked into the library images and must be fixed by replacing library artwork in Jellyfin.
- Renaming `Reciente en <library>` is not semantically solved by CSS; the `0.3.1` fallback is visual only and should be replaced by API/plugin rendering later.
- In `0.4.0`, both of those CSS fallbacks are optional JellyFrame addons instead of base theme behavior.

The `0.3.2` block adapts the theme for Jellyfin-PG JellyFrame:

- `jellyframe/themes.json` contains a JellyFrame compatible theme repository entry for `UKD Jellyfin`.
- Legacy `skin-manager/skins.json` exists but JellyFrame should be preferred.
- `dist/ukd-jellyfin.css` is intended to be served from jsDelivr at `https://cdn.jsdelivr.net/gh/TorrelUKD/UKD-Jellyfin-skin@main/dist/ukd-jellyfin.css`.
- Font URLs are absolute jsDelivr URLs pointing to `assets/fonts/elms-sans/` because JellyFrame serves cached CSS from a local API endpoint, where relative font URLs would resolve incorrectly.
- Focus styling on home cards was changed from full outer rings to a lateral projector bar to avoid crossing card titles.

The `0.4.0` JellyFrame pass corrected the theme format and packaging:

- The correct JellyFrame manifest is `jellyframe/themes.json`.
- The theme id is `ukd-jellyfin`.
- JellyFrame variables use `SCREAMING_SNAKE_CASE` keys.
- Fragile CSS-only behavior was moved out of the base theme and into optional addons:
  - `jellyframe/addons/hide-next-up.css`
  - `jellyframe/addons/recent-title.css`
- The base theme keeps the visual identity and focus treatment only.

## Known Screenshot Context

The user provided a screenshot of the Jellyfin home page showing:

- Header with Jellyfin logo, Inicio, Favoritos, user/search/cast icons.
- Section `Mis contenidos` containing libraries:
  - Anime - Peliculas
  - Anime - Series
  - Colecciones
  - Peliculas
  - Series
- Section `Seguir viendo`, currently showing repeated episodes from the same series.
- Section `A continuacion`, which the user wants removed.
- Later sections named `Reciente en <library>`.

Observed issue from screenshot after first CSS version:

- The visual result still looked close to stock Jellyfin.
- Text inside `Mis contenidos` images appeared duplicated with text below the image.
- Hover/focus rings were clipped or visually broken.

## Functional Requirements Not Solvable With CSS Alone

These are critical if continuing in another framework:

### Continue Watching Grouped By Series

Requirement:

- `Seguir viendo` should show one item per series, not multiple episodes from the same series.

Reason CSS cannot solve it:

- Jellyfin renders `Seguir viendo` from resume/playback items, usually episodes. CSS cannot group multiple items by `SeriesId`.

Recommended implementation:

- Query Jellyfin API for resume items.
- Group episode items by `SeriesId`.
- Select the best representative item per series, likely the next/resume episode.
- Render one card per series with resume metadata.

Likely data fields to investigate:

- `Id`
- `SeriesId`
- `SeriesName`
- `ParentIndexNumber`
- `IndexNumber`
- `UserData.PlaybackPositionTicks`
- `UserData.PlayedPercentage`
- `ImageTags`
- `BackdropImageTags`

### Recently Added For 20 Days

Requirement:

- Rename `Reciente` to `Recientemente añadido` per library.
- Show this section only for 20 days, then disappear.

Reason CSS cannot solve it:

- CSS cannot calculate item age or decide whether a section should exist.

Recommended implementation:

- Query recently added items per library.
- Filter by `DateCreated >= now - 20 days`.
- If no items match, do not render the section.
- Display title: `Recientemente añadido en <library>` or `Recientemente añadido` depending on UX decision.

### Text Inside Library Images

Requirement:

- Remove text inside library images while keeping larger text below the image.

Important distinction:

- If the text is HTML overlay, CSS can hide it.
- If the text is baked into the actual library image, the library images must be replaced in Jellyfin.

Recommended implementation in another framework:

- Do not render overlay title inside image tiles.
- Render library title below the image as dedicated text.

## Recommended Framework Approach

If moving away from plain CSS, use the framework to build a Jellyfin front-end shell or companion UI that consumes the Jellyfin API.

Recommended architecture:

- Auth against Jellyfin API.
- Fetch user views/libraries.
- Fetch resume items and group by series.
- Fetch recently added items with 20-day filtering.
- Render custom home layout inspired by Crunchyroll.
- Preserve deep links back into Jellyfin items if not replacing playback.

Recommended UI sections:

1. Header/navigation.
2. `Mis contenidos` library rail.
3. `Seguir viendo` grouped by series.
4. `Recientemente añadido` per library, filtered to 20 days.
5. Optional genre or collection rails later.

## Design Requirements For New Framework

### Layout

- Use horizontal rails/carousels similar to Crunchyroll.
- Large section titles with a vertical accent mark.
- Cards should have medium-large size.
- Avoid overcrowding.
- Home should feel curated, not like a grid dashboard.

### Library Cards

- Use image on top.
- No title text inside the image.
- Title below image.
- Larger readable font.
- On hover/focus, card should scale up noticeably.
- Focus state must not be clipped by parent containers.

### Focus And Remote Navigation

- Every actionable element needs a visible focus ring.
- Focus ring should use both white and accent color, not just color alone.
- Avoid clipped shadows/rings by using visible overflow or padding around rails.
- Selected library/card should scale up.
- Avoid long animations.

### Motion

- Keep transitions under roughly `150ms`.
- Respect `prefers-reduced-motion`.
- No autoplaying heavy effects.

### Color Direction

Current preferred palette:

```css
--ukd-bg: #040509;
--ukd-text: #f7f4ef;
--ukd-text-muted: rgba(247, 244, 239, 0.70);
--ukd-accent: #7c4dff;
--ukd-accent-2: #00d5ff;
--ukd-crunch-accent: #f47521;
--ukd-crunch-accent-2: #ffb15f;
```

The orange accent is useful for the Crunchyroll-inspired feel. The violet/cyan keeps the UKD/Neon Noir identity.

## Jellyfin API Investigation Needed

The next framework should inspect Jellyfin API endpoints for:

- User libraries/views.
- Latest media per library.
- Resume/continue watching.
- Item images/backdrops.
- Playback links or deep links.

Useful implementation goals:

- Build an API adapter layer, do not scatter Jellyfin endpoint calls in UI components.
- Normalize Jellyfin items into app-specific models such as `LibraryCard`, `ResumeSeriesCard`, `RecentItemCard`.
- Keep grouping/filtering logic testable.

## Suggested Data Models

```ts
type LibraryCard = {
  id: string;
  name: string;
  imageUrl: string;
  href: string;
};

type ResumeSeriesCard = {
  seriesId: string;
  seriesName: string;
  nextItemId: string;
  seasonNumber?: number;
  episodeNumber?: number;
  episodeTitle?: string;
  progressPercent?: number;
  imageUrl: string;
  href: string;
};

type RecentItemCard = {
  id: string;
  libraryId: string;
  title: string;
  subtitle?: string;
  dateCreated: string;
  imageUrl: string;
  href: string;
};
```

## Suggested Resume Grouping Logic

```ts
function groupResumeBySeries(items) {
  const grouped = new Map();

  for (const item of items) {
    const key = item.SeriesId || item.Id;
    const current = grouped.get(key);

    if (!current) {
      grouped.set(key, item);
      continue;
    }

    const currentProgress = current.UserData?.PlaybackPositionTicks || 0;
    const itemProgress = item.UserData?.PlaybackPositionTicks || 0;

    if (itemProgress > currentProgress) {
      grouped.set(key, item);
    }
  }

  return Array.from(grouped.values());
}
```

This is only a starting point. The correct representative item may need to consider episode order and next-unplayed logic.

## Suggested Recently Added Logic

```ts
function filterRecentWithinDays(items, days = 20) {
  const cutoff = Date.now() - days * 24 * 60 * 60 * 1000;

  return items.filter((item) => {
    const created = new Date(item.DateCreated).getTime();
    return Number.isFinite(created) && created >= cutoff;
  });
}
```

## Current AI Skills Context

The project includes Markdown skill files under `ai-skills/`. They are not installed system skills; they are reusable prompt/context files.

Most useful skills:

- `jellyfin-theme-engineer.md`
- `visual-identity-designer.md`
- `responsive-tv-qa.md`
- `css-maintainer.md`
- `accessibility-reviewer.md`

When continuing in another framework, add new skills if useful:

- `jellyfin-api-engineer.md`
- `tv-navigation-engineer.md`
- `frontend-architecture-reviewer.md`

## Open Questions For The Next Phase

- Which framework will be used?
- Will this be a full Jellyfin Web replacement, a companion web app, or a plugin-served custom page?
- Should playback happen inside the new app, or should cards deep-link into Jellyfin playback?
- How will authentication/session handling be managed?
- Should the UI be optimized for 1080p first, 4K first, or both equally?

## Recommended Next Steps

1. Choose framework and deployment model.
2. Implement Jellyfin API authentication and item image helpers.
3. Build the custom home page with static mock data.
4. Replace mock data with Jellyfin libraries.
5. Implement `Seguir viendo` grouped by series.
6. Implement `Recientemente añadido` with 20-day filtering.
7. Test remote-control focus on TV browser.
8. Iterate visual polish from screenshots.

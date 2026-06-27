# UKD Jellyfin

Skin cinematografica para Jellyfin 10.11.10, pensada para TV navegador, control remoto y bibliotecas mixtas de peliculas, series, anime y series de anime.

## Objetivo

UKD Jellyfin busca una interfaz seria, oscura y cinematografica, con lectura comoda desde TV, foco visible para control remoto, uso del backdrop como atmosfera visual y cambios agresivos pero relativamente estables.

## Estructura

```text
themes/
  base.css
  neon-noir.css
  anime-cinema.css
  arcade-minimal.css
dist/
  ukd-jellyfin.css
docs/
  install.md
  compatibility.md
  ai-skills.md
  feature-limits.md
ai-skills/
  jellyfin-theme-engineer.md
  visual-identity-designer.md
  responsive-tv-qa.md
  css-maintainer.md
  accessibility-reviewer.md
assets/
  fonts/
  images/
  icons/
```

## Uso Rapido

Metodo recomendado con JellyFrame:

```text
https://raw.githubusercontent.com/TorrelUKD/UKD-Jellyfin-skin/main/jellyframe/themes.json
```

En `Dashboard > Themes > Marketplace`, usa esa URL como repositorio/lista de temas, selecciona `UKD Jellyfin` y pulsa `Save & Apply`.

Metodo fallback con CSS manual:

1. Abre `dist/ukd-jellyfin.css`.
2. Copia todo el contenido.
3. En Jellyfin ve a `Dashboard > Branding > Custom CSS`.
4. Pega el CSS y guarda.
5. Recarga Jellyfin Web en el navegador/TV.

## Variantes

- `Neon Noir`: base recomendada para UKD. Negro profundo, acento cian/violeta y presencia cinematografica.
- `Anime Cinema`: mas calida y expresiva, manteniendo sobriedad.
- `Arcade Minimal`: mas limpia, geometrica y contenida.

El archivo `dist/ukd-jellyfin.css` usa actualmente la direccion `Neon Noir` como variante principal.

## Notas

- Android TV puede no aplicar todos los estilos si no carga Jellyfin Web desde el servidor.
- El skin usa `Elms Sans` desde `assets/fonts/elms-sans/` servido por jsDelivr desde este repositorio. No usa Google Fonts.
- Las animaciones son minimas para preservar rendimiento en TV.

## Version actual

`0.4.0` adapta la skin al formato correcto de JellyFrame: usa `jellyframe/themes.json`, mueve los parches fragiles (`A continuacion` y titulo de recientes) a addons opcionales, mantiene `Elms Sans` desde archivos del repo servidos por jsDelivr y refina el foco de cards como ranura lateral de proyector.

Los pedidos de `Seguir viendo` agrupado por serie y `Recientemente anadido` con caducidad de 20 dias estan documentados en `docs/feature-limits.md` porque requieren logica de Jellyfin, no solo CSS.

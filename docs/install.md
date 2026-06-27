# Instalacion

## Metodo recomendado: JellyFrame

Requisitos instalados en Jellyfin:

- `File Transformation`
- `JellyFrame` de Jellyfin-PG

Usa este repositorio de temas en JellyFrame:

```text
https://raw.githubusercontent.com/TorrelUKD/UKD-Jellyfin-skin/main/jellyframe/themes.json
```

Importante: esta URL solo tendra los ultimos cambios despues de subir el repositorio a GitHub.

Pasos:

1. En Jellyfin entra como administrador.
2. Ve a `Dashboard > Themes > Marketplace`.
3. Busca el campo de URL/repositorio de temas.
4. Pega la URL anterior.
5. Pulsa `Load Themes`.
6. Pulsa `Apply` en `UKD Jellyfin`.
7. Ajusta variables si quieres. Los parches `Hide Next Up` y `Rename recent rails` son toggles/addons.
8. Pulsa `Save & Apply`.
9. Si no ves cambios, usa `Dashboard > Themes > Settings > Theme Cache > Purge`.
10. Recarga Jellyfin Web con `Ctrl+Shift+R`.

El CSS se carga desde:

```text
https://cdn.jsdelivr.net/gh/TorrelUKD/UKD-Jellyfin-skin@main/dist/ukd-jellyfin.css
```

## Metodo fallback: Custom CSS

1. Abre `dist/ukd-jellyfin.css`.
2. Copia todo el contenido.
3. En Jellyfin entra como administrador.
4. Ve a `Dashboard > Branding > Custom CSS`.
5. Pega el CSS completo.
6. Guarda.
7. Recarga Jellyfin Web con cache limpia si no ves cambios.

## TrueNAS

Si Jellyfin corre como app en TrueNAS, el campo de CSS personalizado sigue estando en la administracion de Jellyfin, no en la configuracion de TrueNAS.

## Assets y fuentes

La fuente `Elms Sans` esta en `assets/fonts/elms-sans/` y el CSS la carga desde jsDelivr apuntando a este repositorio. No usa Google Fonts.

Si usas `Custom CSS` pegado manualmente, la fuente tambien puede cargar mientras el navegador tenga acceso a jsDelivr.

## Volver atras

Con JellyFrame:

1. Ve a `Dashboard > Themes`.
2. Quita o cambia el tema activo a `Default`.
3. Pulsa `Save & Apply`.
4. Purga cache si hace falta y recarga con `Ctrl+Shift+R`.

Con Skin Manager legado:

1. Selecciona `Default`.
2. Pulsa `Save & Apply`.
3. Limpia cache si hace falta y recarga con `Ctrl+Shift+R`.

Con Custom CSS:

1. Copia el CSS actual a un archivo de respaldo si quieres conservarlo.
2. Borra el contenido de `Custom CSS`.
3. Guarda y recarga Jellyfin.

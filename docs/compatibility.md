# Compatibilidad

## Objetivo probado

- Jellyfin Server/Web: 10.11.10.
- JellyFrame: Jellyfin-PG JellyFrame con File Transformation instalado.
- Uso principal: TV navegador con control remoto.
- Contenido: peliculas, series, peliculas de anime y series de anime.

## Esperado

- Jellyfin Web: compatible.
- Jellyfin Media Player: probablemente compatible si carga Jellyfin Web.
- Navegador en TV: compatible, pendiente de validar foco real con control remoto.

## Riesgo

- Android TV: compatibilidad parcial o nula si el cliente no aplica el CSS de Jellyfin Web de la misma forma.
- Selectores internos: Jellyfin puede cambiar nombres de clases entre versiones.
- JellyFrame cachea CSS en disco; al cambiar version o CSS puede ser necesario usar `Dashboard > Themes > Settings > Theme Cache > Purge`.
- Cambios agresivos: cuanto mas se altere layout, mas mantenimiento requerira.

## Politica de estabilidad

- Usar variables CSS para paleta y radios.
- Preferir clases estables y patrones generales antes que selectores `nth-child`.
- Usar `!important` cuando Jellyfin lo requiera, pero evitar selectores demasiado especificos.
- No ocultar elementos en la primera version para evitar perdida accidental de funcionalidad.
- Mantener animaciones minimas.

## Checklist de prueba

- Home: bibliotecas, seguir viendo y recientes.
- Bibliotecas: grid de posters/backdrops, filtros y orden.
- Detalle de pelicula/serie: backdrop, titulo, botones, metadatos y capitulos.
- Player/OSD: controles, barra de progreso, subtitulos y botones.
- Control remoto: foco visible en tarjetas, tabs, menu lateral y botones.
- Pantallas: 1080p y 4K si es posible.

## Limites que no resuelve CSS

- `Seguir viendo` por serie en lugar de por capitulo requiere cambiar la logica que entrega los items de Jellyfin. CSS solo puede mostrar, ocultar o estilizar lo que Jellyfin ya renderiza.
- Cambiar `Reciente` a `Recientemente anadido` de forma robusta requiere modificar traducciones/interfaz o el cliente web. CSS no puede reemplazar parcialmente texto dinamico de forma estable.
- Mostrar `Recientemente anadido` solo durante 20 dias requiere logica con fechas. CSS no puede calcular edad de contenido ni consultar metadatos.

## Opciones tecnicas para esos limites

- Plugin o script que consulte la API de Jellyfin y genere una seccion personalizada.
- Fork/parche de Jellyfin Web para cambiar la consulta de `Resume` y los titulos de secciones.
- Automatizacion externa que marque/organice colecciones recientes durante 20 dias.

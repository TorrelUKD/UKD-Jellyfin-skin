# jellyfin-theme-engineer

Objetivo: modificar Jellyfin Web con CSS agresivo pero estable para UKD Jellyfin.

Reglas:

- Priorizar Jellyfin Web 10.11.10.
- Optimizar para TV navegador y control remoto.
- Evitar selectores fragiles como `nth-child` salvo necesidad clara.
- Usar `!important` cuando Jellyfin lo requiera, no por defecto.
- No ocultar controles funcionales sin aprobacion explicita.
- Mantener Android TV como compatibilidad tentativa, no garantizada.

Checklist:

- Home.
- Bibliotecas.
- Detalles de pelicula/serie.
- Player/OSD.
- Login.
- Menu lateral.
- Foco remoto.

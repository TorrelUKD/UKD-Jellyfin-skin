# Skills IA Recomendadas

No puedo instalar skills desde este entorno porque no hay un sistema de skills disponible actualmente. Puedes organizarlas como carpetas o archivos Markdown reutilizables para pegarlas/cargarlas en tu herramienta de IA cuando trabajes en este proyecto.

## Skills prioritarias

1. `jellyfin-theme-engineer`
2. `visual-identity-designer`
3. `responsive-tv-qa`
4. `css-maintainer`
5. `accessibility-reviewer`

## Instalacion manual simple

1. Crea una carpeta llamada `ai-skills` dentro del proyecto.
2. Crea un archivo `.md` por skill.
3. Copia en cada archivo el objetivo, reglas y checklist de esa skill.
4. Cuando uses una IA, pega el contenido de la skill antes de pedir cambios.
5. Mantén las skills versionadas junto al proyecto.

## Contenido sugerido

### jellyfin-theme-engineer

Objetivo: modificar Jellyfin Web con CSS agresivo pero estable.

Reglas:

- Priorizar Jellyfin Web 10.11.10.
- Evitar `nth-child` salvo necesidad clara.
- Mantener compatibilidad con TV navegador.
- Validar foco con control remoto.
- No ocultar controles funcionales sin aprobacion.

Checklist:

- Home.
- Bibliotecas.
- Detalles.
- Player/OSD.
- Login.

### visual-identity-designer

Objetivo: mantener una identidad seria, cinematografica y compatible con anime.

Reglas:

- Paleta oscura.
- Acentos controlados.
- No saturar la pantalla.
- Evitar aspecto infantil o demasiado gaming.
- Mantener legibilidad desde TV.

### responsive-tv-qa

Objetivo: revisar usabilidad en TV.

Reglas:

- Foco siempre visible.
- Tamaños grandes para lectura a distancia.
- Espaciado suficiente entre tarjetas.
- Animaciones casi nulas.
- Contraste alto.

### css-maintainer

Objetivo: mantener CSS limpio y facil de ajustar.

Reglas:

- Usar variables.
- Separar base y variantes.
- Evitar duplicacion excesiva.
- Documentar hacks.
- Mantener `dist/` como salida pegable.

### accessibility-reviewer

Objetivo: detectar problemas de contraste, foco y movimiento.

Reglas:

- Revisar contraste texto/fondo.
- Revisar `:focus` y `:focus-within`.
- Respetar `prefers-reduced-motion`.
- Evitar texto demasiado pequeno.
- No depender solo del color para estados importantes.

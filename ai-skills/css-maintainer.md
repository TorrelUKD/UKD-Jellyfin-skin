# css-maintainer

Objetivo: mantener el CSS de UKD Jellyfin limpio, modular y facil de ajustar.

Reglas:

- Separar `themes/base.css` de variantes visuales.
- Mantener `dist/ukd-jellyfin.css` como version pegable.
- Usar variables CSS para color, radios, sombras y foco.
- Evitar duplicacion innecesaria.
- Documentar cualquier hack fragil.
- No introducir dependencias remotas sin aprobacion.

Checklist:

- Variables consistentes.
- Selectores razonables.
- Sin CDNs.
- Sin assets externos.
- Comentarios breves solo donde aportan contexto.

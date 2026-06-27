# Limites Funcionales

Estos pedidos no pertenecen a una skin CSS pura porque requieren datos, fechas o cambios en la logica de Jellyfin.

## Seguir viendo por serie

Pedido: mostrar una sola tarjeta por serie, no varios capitulos de la misma serie.

Motivo: Jellyfin entrega `Seguir viendo` como items reproducibles, normalmente episodios. CSS no puede agrupar episodios por serie.

Soluciones posibles:

- Plugin que genere una seccion personalizada agrupada por `SeriesId`.
- Modificar Jellyfin Web para agrupar la respuesta del endpoint de resume.
- Script externo que consuma la API y publique una vista propia.

## Recientemente anadido durante 20 dias

Pedido: cambiar `Reciente` a `Recientemente anadido` y ocultarlo luego de 20 dias.

Motivo: CSS no puede calcular fechas ni saber cuando fue agregado cada item.

Soluciones posibles:

- Plugin con filtro `DateCreated >= hoy - 20 dias`.
- Cambio en Jellyfin Web para ajustar el titulo y filtro.
- Automatizacion externa que genere colecciones temporales.

## Texto dentro de imagenes de bibliotecas

Pedido: quitar el texto grande dentro de las imagenes de `Mis contenidos`.

Motivo: si el texto es overlay HTML, el CSS agregado lo oculta. Si el texto esta incrustado en la propia imagen de la biblioteca, hay que reemplazar esa imagen desde Jellyfin.

# EST19 — Registro de Lotes de Fermentación

> Este es un archivo de ejemplo. No representa trabajo real. Sirve como referencia
> de cómo debe verse un archivo de tarea bien completado.
> Elimina este bloque en tu archivo real.

| Campo       | Valor              |
|-------------|--------------------|
| Ticket Jira | EST19              |
| Diseñador   | Ana García         |
| Fecha       | 2025-05-15         |
| Estado      | Completado         |
| Plataforma  | Móvil              |

---

## Descripción

Se diseñó la pantalla de registro de nuevos lotes de fermentación. Desde aquí el usuario ingresa los parámetros iniciales del proceso: nombre del lote, variedad de café, peso en kilogramos, fecha de inicio y método de fermentación (húmedo, seco o honey). Esta pantalla es el punto de entrada a todo el monitoreo posterior del lote.

---

## Figma

[Ver frame en Figma](https://www.figma.com/design/gXA9g3ioQeuq5uGOoKDtmE/Nich-Borrador?node-id=0-1&p=f&t=cLXypTo0WkSJzZJy-0)

---

## Decisiones de diseño

### Formulario en una sola columna

Se descartó el layout de dos columnas que se usa en la versión web. En móvil, con un ancho mínimo de 360px, los campos en dos columnas resultarían demasiado angostos y difíciles de tocar con el pulgar. Los productores usan la app en campo, frecuentemente con guantes o una sola mano.

### Selector de método como chips, no dropdown

El método de fermentación tiene exactamente 3 opciones (húmedo, seco, honey). Un dropdown requeriría un tap extra para abrirlo y otro para seleccionar, además de ocultar las opciones por defecto. Los chips muestran las tres opciones de un vistazo y reducen la interacción a un solo tap.

### Campo de fecha con selector nativo del SO

Se decidió usar el date picker nativo en lugar de un componente personalizado para aprovechar el comportamiento ya familiar del usuario y no agregar dependencias de UI. La desventaja es que el estilo varía entre iOS y Android, pero se priorizó la usabilidad sobre la consistencia visual en este caso.

---

## Componentes

| Componente     | Acción       | Notas                                        |
|----------------|--------------|----------------------------------------------|
| Input Field    | Reutilizado  | Variante con label flotante                  |
| Chip Selector  | Creado nuevo | Frame: Components/ChipGroup — informar a dev |
| Primary Button | Reutilizado  | Texto: "Iniciar lote"                        |
| Top App Bar    | Reutilizado  | Con botón de retroceso                       |

---

## Flujo de usuario

```
Dashboard principal → FAB "+" → [Esta pantalla: Registro de lote] → Pantalla de confirmación del lote
```

---

## Pendientes

- [ ] Estado de error cuando el nombre del lote ya existe en el sistema (abre EST23)
- [ ] Validación de peso mínimo/máximo — pendiente confirmar rangos con el equipo de negocio

---

## Notas de accesibilidad

- Todos los campos tienen label visible (no solo placeholder) para que no desaparezcan al escribir.
- El chip selector usa un borde de 2px en el estado activo además del cambio de color, para no depender únicamente del color como indicador.
- El botón "Iniciar lote" tiene altura de 56px para cumplir con el mínimo de 48px de área de toque recomendado por Material Design y Apple HIG.

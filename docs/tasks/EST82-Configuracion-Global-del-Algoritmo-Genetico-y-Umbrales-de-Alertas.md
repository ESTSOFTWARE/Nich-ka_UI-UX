# EST82— interfaz web de Configuración Global del Algoritmo Genético y Umbrales de Alertas

> Este es un archivo de ejemplo. No representa trabajo real. Sirve como referencia
> de cómo debe verse un archivo de tarea bien completado.
> Elimina este bloque en tu archivo real.

| Campo       | Valor              |
|-------------|--------------------|
| Ticket Jira | EST82              |
| Diseñador   | Lyz Solar         |
| Fecha       | 2026-06-21         |
| Estado      | Completado         |
| Plataforma  | Web            |

---

## Descripción

Se diseñó la interfaz de Configuración Global para la consola de administración del sistema Nich-Ká. Se diseñó la interfaz de Configuración Global para la consola de administración del sistema Nich-Ká. Esta pantalla permite gestionar de forma centralizada los parámetros del algoritmo genético de optimización, definir las restricciones operativas de los procesos de fermentación (temperatura, pH y tiempo), configurar los umbrales críticos de las alertas de sensores e inspeccionar visualmente los niveles de criticidad del sistema. Además, incluye un historial de cambios para auditorías, controles maestros de acción y un flujo de confirmación integrado tras el guardado exitoso de los datos.

---

## Figma

[Ver frame en Figma](https://www.figma.com/design/gXA9g3ioQeuq5uGOoKDtmE/Nich-Borrador?node-id=0-1&p=f&t=cLXypTo0WkSJzZJy-0)

---

## Decisiones de diseño

### Layout modular oscuro y enfocado
Se estructuró la pantalla sobre un fondo totalmente negro (`#000000`) con un ancho de 1536px para entornos de escritorio industriales. Los bloques se segmentan mediante tarjetas con bordes sutiles de baja opacidad (`#D9D9D9` al 25%), lo que mitiga la fatiga visual de los operadores y organiza la configuración en secciones verticales claramente identificables.

### Distribución adaptativa de parámetros y rangos
Para optimizar el escaneo de datos numéricos en pantalla ancha:
* **Parámetros AG:** Organizados en una rejilla de 2 columnas para campos individuales (ej. Tamaño de población y Máx. generaciones).
* **Restricciones de proceso:** Diseñadas en 3 columnas anchas, integrando internamente pares de valores "mínimo" y "máximo" de lectura paralela.
* **Umbrales de alerta:** Distribuidos en una fila compacta de 5 columnas para visualizar la salud de todos los sensores en un solo plano horizontal.

### Código cromático de estatus y criticidad
Se utiliza el color verde (`#2ECC71`) para acentuar la navegación activa, los valores óptimos (como el 80% en probabilidad de cruce) y las alertas informativas rutinarias. Para la escala de alertas, se asignó un indicador circular diferenciado: Verde para estados Informativos, Gris Claro para Advertencias y Blanco Puro para estados Críticos, asegurando una rápida interpretación sin saturar de color la interfaz.
---

## Componentes

| Componente     | Acción       | Notas                                                                |
|----------------|--------------|----------------------------------------------------------------------|
| Sidebar Left   | Reutilizado  | Ancho de 220px con el elemento "Parámetros AG" en estado activo (`#2ECC71`). |
| Input Field    | Reutilizado  | Variantes oscuras (`fill-opacity: 0.08`) para lectura y edición de valores únicos. |
| Tooltip Icon   | Creado nuevo | Icono circular (`i`) con borde atenuado para desplegar ayudas contextuales. |
| Range Field    | Creado nuevo | Entrada doble horizontal para gestionar mínimos y máximos en una sola celda. |
| Action Bar     | Creado nuevo | Fila inferior con tres botones maestros de control (Cancelar, Guardar, Restaurar). |
| Dialog Modal   | Creado nuevo | Pop-up central de confirmación con check de éxito (`path` vectorizado). |
---

## Flujo de usuario

```
[Cualquier pantalla de la consola]
       │
       ▼ (1. Clic en Sidebar izquierdo)
[Pestaña: Parámetros AG]
       │
       ▼ (2. Carga de la interfaz)
[Pantalla: Configuración Global] ─── (Revisión de parámetros actuales)
       │
       ├───► (Modificación de datos en campos de texto)
       │
       ▼ (3. Clic en botón principal)
[Botón: Guardar configuración]
       │
       ▼ (4. Disparo de acción / Interrupción en pantalla)
[Modal de Confirmación (Estado de éxito)] ─── (Bloquea fondo con los datos guardados)
       │
       ▼ (5. Clic en botón del Modal)
[Botón: Entendido]
       │
       ▼ (6. Cierre de Modal)
[Pantalla: Configuración Global (Estado Base)]
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

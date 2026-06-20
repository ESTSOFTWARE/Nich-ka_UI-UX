# EST82— interfaz web de Configuración Global del Algoritmo Genético y Umbrales de Alertas

> Este es un archivo de ejemplo. No representa trabajo real. Sirve como referencia
> de cómo debe verse un archivo de tarea bien completado.
> Elimina este bloque en tu archivo real.

| Campo       | Valor              |
|-------------|--------------------|
| Ticket Jira | EST82              |
| Diseñador   | Lyz Solar         |
| Fecha       | 2026-06-19         |
| Estado      | Completado         |
| Plataforma  | Web            |

---

## Descripción

Se diseñó la interfaz administrativa centralizada para la Configuración Global del sistema. Desde esta pantalla el usuario administrador gestiona y calibra los parámetros avanzados del algoritmo genético que optimiza la fermentación de café, establece restricciones de entorno y define los umbrales críticos de alerta para los cinco sensores integrados (pH, Temperatura, Alcohol, Conductividad y Turbidez).

---

## Figma

[Ver frame en Figma](https://www.figma.com/design/gXA9g3ioQeuq5uGOoKDtmE/Nich-Borrador?node-id=0-1&p=f&t=cLXypTo0WkSJzZJy-0)

---

## Decisiones de diseño

### Layout modular de tres bloques funcionales

Se estructuró la pantalla mediante una jerarquía vertical e independiente para evitar la sobrecarga cognitiva: una sección para el comportamiento matemático del algoritmo, una tarjeta lateral para límites físicos del entorno y un contenedor inferior exclusivo para la salud de los sensores.

### Visualización de rangos mediante inputs dobles paralelos

Para optimizar el espacio en la sección de Restricciones (Temperatura, pH, Tiempo), se descartaron las listas verticales complejas y se implementaron pares de campos mínimos y máximos en formato horizontal unidos por la palabra "to". Esto reduce el scroll vertical y facilita la lectura comparativa.

### Estructura horizontal escalable para tarjetas de sensores

Los cinco sensores obligatorios se ordenaron en un layout de rejilla horizontal por columnas independientes. Si en el futuro el sistema integra nuevos tipos de sensores, la interfaz puede crecer de forma natural hacia abajo o transformarse en un carrusel sin alterar la estructura base del módulo.

---

## Componentes

| Componente     | Acción       | Notas                                        |
|----------------|--------------|----------------------------------------------|
| Sidebar Left   | Reutilizado  | Con estado activo en la pestaña "Genetic Config". |
| Input Field    | Reutilizado  | Variante Dark con tipografía activa en verde brillante (#00FF00). |
| Slider Control | Creado nuevo | Frame: `Components/Slider` — aplicado para Prob. de Cruce y Mutación. |
| Dropdown Select| Reutilizado  | Modificado para las variantes de selección única (`Torneo Binario`). |
| Alert Level Bar| Creado nuevo | Contenedor de niveles con estados fijo: Informativo, Advertencia y Crítico. |
| Primary Button | Reutilizado  | Botón sólido verde con el texto "GUARDAR CONFIGURACIÓN". |

---

## Flujo de usuario

```
Cualquier pantalla → Sidebar lateral (Menú: Genetic Config) → [Esta pantalla: Configuración Global] → Botón "Guardar Configuración" → Notificación flotante de éxito (Toast)
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

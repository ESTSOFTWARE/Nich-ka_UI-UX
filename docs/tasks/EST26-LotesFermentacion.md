# EST26 Lotes de Fermentación


| Campo       | Valor                        |
|-------------|------------------------------|
| Ticket Jira | EST26                        |
| Diseñador   | Lyz Solar                    |
| Fecha       | 2023-10-25                   |
| Estado      | En revisión                  |
| Plataforma  | Móvil                        |

---

## Descripción

Diseño de la vista completa de "Lotes de fermentación" para la aplicación móvil, incluyendo soporte para modo claro y oscuro. El objetivo es permitir a los usuarios visualizar, buscar y filtrar los lotes activos y procesados, manteniendo la consistencia con el sistema de diseño del proyecto.

---

## Figma

[Ver frame en Figma](https://www.figma.com/design/gXA9g3ioQeuq5uGOoKDtmE/Nich-Borrador?node-id=48-931&t=HMJJkMJ6fze2if3j-4)


---

## Decisiones de diseño

### Sincronización de contenido entre modos
Se decidió mantener una paridad exacta de información entre el modo claro y el modo oscuro (mismos lotes, mismos contadores). Esto garantiza una experiencia de usuario predecible al cambiar de tema, evitando la desorientación.

### Radio de borde pronunciado (Border Radius)
A petición de la consistencia con el trabajo de otros compañeros del equipo, se incrementó el redondeo de las tarjetas y componentes. Esto alinea la interfaz con la estética "amigable y moderna" del resto de la aplicación Nich-Ká.

### Uso de colores técnicos para estados
Para los indicadores de progreso y etiquetas de estado (Activo, Secado), se optó por una paleta de colores semántica (verde, naranja) con alto contraste. Esto facilita la lectura rápida del estado del lote sin necesidad de leer el texto descriptivo.

---

## Componentes


| Componente | Acción | Notas |
|------------|--------|-------|
| TopAppBar | Reutilizado | Adaptado con título "Lotes" y navegación. |
| Summary Card | Creado nuevo | Para visualización rápida de totales (Total, Activos, Secado). |
| Search Bar | Reutilizado | Componente base de búsqueda del sistema. |
| Chip Filter | Reutilizado | Implementado para filtros de estado: Todos, Activos, Secado, Completados. |
| Batch Card | Creado nuevo | Tarjeta compleja con barras de progreso y metadata del lote. |
| FAB (+) | Reutilizado | Botón de acción principal para crear nuevos lotes. |
| BottomNavBar | Reutilizado | Navegación principal de la app. |


---

## Flujo de usuario

<!-- De dónde viene el usuario y a dónde va. Usa flechas para mostrar la secuencia. -->

```
[Dashboard Principal] → [Botón Lotes / FAB] → [Esta pantalla (Lotes)] → [Detalle de Lote / Nuevo Lote]
```

---

## Pendientes *(opcional)*

<!-- Tareas incompletas o deuda de diseño. Linka al ticket de Jira si existe. -->

- [ ] 

---

## Notas de accesibilidad *(opcional)*

<!-- Decisiones de contraste, tamaño mínimo de toque (48x48px), jerarquía de headings, etc. -->

---

## Cambios respecto a versión anterior *(opcional)*

<!-- Solo si esta tarea modificó algo que ya existía. Explica qué cambió y por qué. -->

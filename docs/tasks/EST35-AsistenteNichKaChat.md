# EST26 Lotes de Fermentación (actualizado)


| Campo       | Valor                        |
|-------------|------------------------------|
| Ticket Jira | EST35                       |
| Diseñador   | Lyz Solar                    |
| Fecha       | 2026-05-27                   |
| Estado      | En revisión                  |
| Plataforma  | Móvil                        |

---

## Descripción

Diseño de la interfaz de chat del "Asistente Nich-Ká", una IA en tiempo real integrada para el monitoreo de fermentaciones. La vista permite al usuario recibir alertas críticas, recomendaciones técnicas y predicciones de sabor a través de una conversación fluida y moderna.

---

## Figma

[Ver frame en Figma](https://www.figma.com/design/gXA9g3ioQeuq5uGOoKDtmE/Nich-Borrador?node-id=124-599&t=GkABuWyGdIbV8zX2-4)  


---

## Decisiones de diseño

### Burbujas de chat con jerarquía visual
Se utilizaron burbujas de fondo neutro (gris claro/oscuro) para el asistente para transmitir objetividad, mientras que los mensajes del usuario utilizan el verde institucional (#00C853) para resaltar su intervención y acción.

### Tarjeta de predicción destacada
Para los datos técnicos complejos como la "Predicción de Sabor", se optó por un componente tipo card dentro del flujo del chat en lugar de una burbuja de texto simple. Esto permite incluir indicadores visuales como barras de progreso y puntajes destacados (8.5/10), facilitando la lectura de KPIs.

### Acciones rápidas (Chips)
Se implementaron chips de acción sobre la barra de entrada para reducir la carga cognitiva del usuario, permitiendo consultas frecuentes (Comparar lotes, predicciones) con un solo toque.

---

## Componentes


| Componente | Acción | Notas |
|------------|--------|-------|
| TopAppBar (Chat) | Modificado | Variante con estado "ACTIVO" e IA en tiempo real. |
| Chat Bubble (User) | Creado nuevo | Color verde con bordes redondeados. |
| Chat Bubble (AI) | Creado nuevo | Fondo neutro con tipografía Inter. |
| Prediction Card | Creado nuevo | Incluye barra de progreso y puntaje. |
| Action Chips | Reutilizado | Estilo consistente con filtros de lotes. |
| Chat Input Bar | Creado nuevo | Con soporte para voz y envío rápido. |



---

## Flujo de usuario

<!-- De dónde viene el usuario y a dónde va. Usa flechas para mostrar la secuencia. -->

```
[Cualquier Pantalla] → [Botón Asistente / Notificación] → [Esta pantalla (Chat)] → [Detalle de Recomendación]
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

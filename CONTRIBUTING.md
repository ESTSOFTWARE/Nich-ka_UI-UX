# Guía de contribución — Diseñadores Nich-Ká

Esta guía explica cómo documentar tu trabajo de diseño cada vez que terminas una tarea de Jira. El objetivo es que cualquier miembro del equipo —ahora o en el futuro— pueda entender qué se hizo, por qué se decidió así y cómo encontrarlo en Figma.

---

## Por qué documentamos

- El equipo de desarrollo necesita contexto para implementar correctamente cada pantalla.
- Las decisiones de diseño se olvidan. Documentarlas evita repetir el mismo análisis meses después.
- Cuando alguien retoma una tarea incompleta, el archivo le da un punto de partida claro.
- Sirve como entregable formal que demuestra que la tarea fue completada y revisada.

---

## Cuándo crear el archivo

Cuando tu tarea de Jira pase a estado **Done** o **En revisión**, antes de moverla debes crear y subir su archivo de documentación al repositorio.

---

## Dónde guardar el archivo

Todos los archivos de tareas van dentro de la carpeta:

```
docs/tasks/
```

Si la carpeta no existe en tu rama, créala.

---

## Cómo nombrar el archivo

El nombre del archivo debe seguir exactamente este formato:

```
[TICKET-JIRA]-[NombreDescriptivo].md
```

**Reglas:**
- El ticket de Jira va primero, en mayúsculas, tal como aparece en el tablero.
- El nombre descriptivo usa PascalCase (sin espacios, cada palabra en mayúscula).
- Usa guion `-` para separar el ticket del nombre.
- Sin acentos en el nombre del archivo para evitar problemas de compatibilidad.
- Máximo 50 caracteres en total.

**Ejemplos válidos:**

```
EST19-LotesFermentacion.md
EST7-LoginOnboarding.md
EST34-DashboardPrincipal.md
EST12-AlertasNotificaciones.md
```

**Ejemplos incorrectos:**

```
lotes fermentación.md          ❌ espacios y sin ticket
est19_lotes.md                 ❌ ticket en minúscula y guión bajo
EST19.md                       ❌ sin nombre descriptivo
mi-tarea-de-hoy.md             ❌ sin ticket de Jira
```

---

## Qué incluir en el archivo

Copia la plantilla de `docs/tasks/TEMPLATE.md` y completa cada sección. A continuación se describe qué debe ir en cada una y por qué.

### Secciones obligatorias

#### 1. Encabezado y metadata

Indica de un vistazo de qué trata la tarea y quién la hizo.

```md
# [TICKET] Nombre de la tarea

| Campo        | Valor                          |
|--------------|--------------------------------|
| Ticket Jira  | EST19                          |
| Diseñador    | Tu nombre                      |
| Fecha        | YYYY-MM-DD                     |
| Estado       | En revisión / Completado       |
| Plataforma   | Web / Móvil / Ambas            |
```

#### 2. Descripción de la tarea

Explica en 2-4 oraciones qué pedía la tarea. Copia o parafrasea el enunciado de Jira para que quede registrado aquí también.

```md
## Descripción

Se diseñó la pantalla de registro de lotes de fermentación, donde el usuario
puede ingresar los parámetros iniciales del proceso: nombre del lote, variedad
de café, peso, fecha de inicio y método de fermentación.
```

#### 3. Link a Figma

El link directo al frame o sección en Figma. No al archivo general, sino al frame específico de esta tarea.

```md
## Figma

[Ver frame en Figma](https://www.figma.com/design/gXA9g3ioQeuq5uGOoKDtmE/Nich-Borrador?node-id=XXXX)
```

> Cómo obtener el link exacto: en Figma, selecciona el frame, clic derecho → **Copy link to selection**.

#### 4. Decisiones de diseño

Esta es la sección más importante. Aquí explicas **por qué** tomaste las decisiones que tomaste, no solo qué hiciste. Sin esta sección, el resto del equipo solo ve el resultado pero no entiende el razonamiento.

Documenta al menos 2-3 decisiones. Para cada una responde: ¿qué opciones consideraste? ¿por qué elegiste esta?

```md
## Decisiones de diseño

### Formulario de una sola columna en móvil
Se optó por una columna en lugar de dos para evitar que los campos queden
demasiado angostos en pantallas de 360px. Los productores usarán la app
principalmente en campo con una sola mano.

### Selector de método de fermentación como chips, no dropdown
Los chips permiten ver todas las opciones de un vistazo (húmedo, seco, honey)
sin necesidad de abrir un menú. Son solo 3 opciones, por lo que caben sin
problema y reducen un paso de interacción.
```

#### 5. Componentes usados o creados

Lista los componentes del sistema de diseño que usaste, y si creaste alguno nuevo o modificaste uno existente, indícalo explícitamente para que el equipo de desarrollo lo sepa.

```md
## Componentes

| Componente        | Acción                  | Notas                              |
|-------------------|-------------------------|------------------------------------|
| Input Field       | Reutilizado             | Variante con label flotante        |
| Chip Selector     | Creado nuevo            | Ver frame "Components/ChipGroup"   |
| Primary Button    | Reutilizado             | —                                  |
```

#### 6. Flujo de usuario

Describe brevemente el flujo que cubre esta pantalla: de dónde viene el usuario y a dónde va.

```md
## Flujo de usuario

Dashboard principal → FAB "Nuevo lote" → **[esta pantalla]** → Pantalla de confirmación
```

### Secciones opcionales

Agrégalas solo si aplican a tu tarea.

#### Notas de accesibilidad

Si tomaste decisiones específicas de contraste, tamaño de toque, jerarquía de encabezados o soporte para lectores de pantalla.

#### Pendientes / Deuda de diseño

Si quedó algo incompleto o decidiste dejar algo para después, documéntalo aquí en lugar de en comentarios de Figma que se pierden.

```md
## Pendientes

- [ ] Validación del estado de error cuando el nombre del lote ya existe (EST23)
- [ ] Versión web del formulario pendiente de definir con el equipo
```

#### Cambios respecto a la versión anterior

Si esta tarea modificó algo que ya existía, anota qué cambió y por qué.

---

## Flujo completo de entrega

```
1. Terminas el diseño en Figma
2. Copias docs/tasks/TEMPLATE.md
3. Renombras el archivo con el formato [TICKET]-[Nombre].md
4. Completas todas las secciones obligatorias
5. Haces commit en tu rama de trabajo:
      git add docs/tasks/EST19-LotesFermentacion.md
      git commit -m "docs(EST19): documentación de pantalla Lotes Fermentación"
6. Abres un Pull Request hacia main
7. Mueves el ticket en Jira a "En revisión"
```

### Mensaje de commit

Usa este formato para los commits de documentación:

```
docs([TICKET]): descripción breve en español
```

Ejemplos:
```
docs(EST19): documentación de pantalla Lotes Fermentación
docs(EST7): agrega decisiones de diseño para Login
docs(EST34): actualiza flujo del Dashboard tras revisión
```

---

## Revisión del archivo

Otro diseñador del equipo debe revisar el Pull Request antes de hacer merge. La revisión debe verificar:

- [ ] El archivo tiene el nombre correcto
- [ ] Todas las secciones obligatorias están completas
- [ ] El link de Figma abre al frame correcto
- [ ] Las decisiones de diseño explican el *por qué*, no solo el *qué*
- [ ] Si se crearon componentes nuevos, están listados

---

## Plantilla

Encuentra la plantilla lista para copiar en:

```
docs/tasks/TEMPLATE.md
```

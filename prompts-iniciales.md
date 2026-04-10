# Prompts Iniciales

Este documento consolida los prompts utilizados durante el desarrollo y análisis de la historia de usuario relacionada con la funcionalidad de alta de candidatos en el sistema ATS.

## Objetivo del documento

- Dejar trazabilidad de las instrucciones dadas al asistente.
- Mostrar el orden real en que se usaron los prompts.
- Explicar el propósito de cada prompt dentro del flujo de trabajo.

## Secuencia de prompts

### 1. Análisis inicial del repositorio

**Prompt utilizado**

```text
Analiza este repositorio completo y dame un resumen claro de:

1. Stack tecnológico (frontend, backend, base de datos)
2. Estructura de carpetas
3. Cómo se ejecuta el proyecto (backend, frontend, DB)
4. Qué partes ya están implementadas y cuáles están vacías
5. Dónde debería implementar una funcionalidad nueva siguiendo buenas prácticas

No generes código aún, solo análisis.
```

**Objetivo**

Entender el estado real del repositorio antes de comenzar cambios, identificar el stack, la estructura base y los puntos de extensión recomendados.

### 2. Explicación de ejecución local

**Prompt utilizado**

```text
Lee el README.md y explícame paso a paso cómo levantar el proyecto localmente.

Incluye:
- instalación de dependencias
- variables de entorno
- base de datos
- comandos exactos

Si algo falta o está incompleto, propón cómo solucionarlo.
```

**Objetivo**

Traducir la documentación existente a una guía operativa concreta para ejecución local y detectar inconsistencias o huecos en el `README.md`.

### 3. Diseño técnico de la historia de usuario

**Prompt utilizado**

```text
Voy a implementar la historia de usuario: "Añadir candidato al sistema ATS".

Ayúdame a diseñar la solución completa antes de programar.

Necesito:

1. Modelo de datos del candidato (tabla y campos)
2. Relación con otros posibles modelos
3. Diseño de API backend (endpoints, request, response)
4. Flujo completo desde frontend → backend → DB
5. Manejo de errores
6. Validaciones necesarias
7. Manejo de subida de archivos (CV PDF/DOCX)

No generes código aún. Solo diseño técnico claro y profesional.
```

**Objetivo**

Definir la solución de extremo a extremo antes de implementar, alineando modelo de datos, contratos API, validaciones y manejo de archivos.

### 4. División en tickets técnicos

**Prompt utilizado**

```text
Divide esta solución en 3 tickets técnicos bien definidos:

1. Base de datos
2. Backend
3. Frontend

Cada ticket debe incluir:
- descripción
- tareas detalladas
- criterios de aceptación técnicos
- archivos que se deben crear/modificar

Esto es para usarlo como input en un asistente de código.
```

**Objetivo**

Descomponer la solución en unidades de trabajo ejecutables y reutilizables, facilitando implementación incremental y delegación por capas.

### 5. Implementación del modelo de base de datos

**Prompt utilizado**

```text
Genera el modelo de base de datos para "Candidate" en PostgreSQL.

Debe incluir:
- id (uuid o serial)
- nombre
- apellido
- email (único)
- teléfono
- dirección
- educación
- experiencia
- ruta del archivo CV
- timestamps (created_at, updated_at)

Además:
- genera script SQL de creación
- genera migración si el proyecto usa ORM
- buenas prácticas (índices, constraints)

Adapta el código al stack del proyecto.
```

**Objetivo**

Crear la base persistente de la funcionalidad de candidatos adaptada al stack real del proyecto, incluyendo ORM y SQL explícito.

### 6. Implementación del backend de candidatos

**Prompt utilizado**

```text
Implementa el backend para crear candidatos.

Requisitos:
- endpoint POST /candidates
- validación de datos (email válido, campos obligatorios)
- manejo de errores
- guardar información en DB
- soportar subida de archivo (CV PDF/DOCX)
- devolver respuesta clara

Incluye:
- controller
- service
- repository/model
- validaciones

Sigue la estructura del proyecto existente.
```

**Objetivo**

Construir la API backend necesaria para registrar candidatos, guardar datos en base de datos y soportar subida de CV.

### 7. Refuerzo de seguridad del backend

**Prompt utilizado**

```text
Refuerza la implementación anterior agregando:

- validación robusta de inputs
- sanitización de datos
- límite de tamaño de archivos
- validación de tipo de archivo (pdf/docx)
- manejo de errores HTTP adecuados

No cambies la estructura, solo mejora seguridad.
```

**Objetivo**

Elevar la robustez de la implementación backend sin reestructurar el proyecto, enfocándose en seguridad, validación y respuestas HTTP correctas.

### 8. Creación del formulario frontend

**Prompt utilizado**

```text
Crea un formulario de "Añadir candidato" en el frontend.

Debe incluir:
- nombre
- apellido
- email
- teléfono
- dirección
- educación
- experiencia
- upload de CV

Requisitos:
- validación en frontend
- mensajes de error claros
- botón de envío
- diseño simple e intuitivo

Usa el framework del proyecto (React/Vue/etc).
```

**Objetivo**

Construir la interfaz de captura de candidatos en el frontend, con validación cliente y un diseño usable alineado con el stack existente.

### 9. Conexión del formulario con el backend

**Prompt utilizado**

```text
Conecta el formulario con el backend:

- llamada a POST /candidates
- manejo de loading
- manejo de errores
- mensaje de éxito

Incluye:
- manejo de estado
- buenas prácticas de UX
```

**Objetivo**

Conectar la UI con la API de candidatos y garantizar una experiencia clara durante envío, error y confirmación exitosa.

### 10. Acción principal desde el dashboard

**Prompt utilizado**

```text
Agrega un botón en el dashboard principal del reclutador:

- texto: "Añadir candidato"
- navegación al formulario
- visible y accesible

Sigue el diseño actual del proyecto.
```

**Objetivo**

Incorporar una entrada visible a la funcionalidad dentro de la pantalla principal del reclutador, mejorando descubribilidad y accesibilidad.

### 11. Documentación de prompts utilizados

**Prompt utilizado**

```text
Genera un archivo llamado prompts-iniciales.md que documente:

- todos los prompts utilizados
- en qué orden se usaron
- objetivo de cada prompt

Formato claro y profesional para entrega.
```

**Objetivo**

Consolidar la trazabilidad del trabajo realizado en un documento final de entrega.

## Resumen del flujo

El proceso siguió una secuencia lógica:

1. Comprensión del repositorio.
2. Revisión de ejecución local.
3. Diseño técnico de la solución.
4. División en tickets.
5. Implementación por capas: base de datos, backend y frontend.
6. Refuerzo de seguridad y UX.
7. Documentación final del proceso.

## Archivo de referencia

Este documento fue creado como soporte de entrega y trazabilidad del desarrollo guiado por prompts.

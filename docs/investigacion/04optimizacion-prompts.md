# Optimización de prompts técnicos

## Estructura base de un prompt efectivo

La calidad del código generado es directamente proporcional a la calidad del prompt. Un prompt técnico bien estructurado tiene cuatro elementos:

```
[ROL] Eres un desarrollador frontend especializado en Astro y componentes web.

[CONTEXTO] Estoy trabajando en un portafolio personal con Astro 4.
El componente `ProjectCard.astro` recibe props: title (string), description (string), 
imageUrl (string), tags (string[]).

[TAREA] Genera el componente con estilos en CSS módulo.
El diseño debe ser una tarjeta con imagen arriba, texto abajo y los tags como pills.

[FORMATO] Responde solo con el código del componente. Sin explicaciones adicionales.
```

Estos cuatro elementos (Rol, Contexto, Tarea, Formato) reducen las iteraciones necesarias hasta en un 70% comparado con prompts vagos como "crea una tarjeta de proyecto".

---

## Prompts para tareas comunes en desarrollo

### Debugging

**Estructura para errores:**
```
Tengo este error en [nombre del archivo]:

ERROR:
[pegar el error exacto]

CÓDIGO RELEVANTE:
[pegar el fragmento de código donde ocurre el error]

CONTEXTO:
- Tecnología: [Astro / React / Vanilla JS]
- Versión: [versión del framework]
- Qué intenté: [lo que ya probé]

¿Cuál es la causa y cómo la corrijo?
```

**Para errores de consola del navegador:**
```
En la consola del navegador aparece este error al [acción que lo dispara]:
[error]

El componente involucrado es [nombre]. ¿Qué lo está causando y cómo lo resuelvo?
```

### Refactorización

```
Refactoriza este código para mejorar su legibilidad y mantenibilidad.
No cambies la funcionalidad, solo la estructura.

CÓDIGO ACTUAL:
[código]

CRITERIOS:
- Separar responsabilidades
- Nombres de variables descriptivos
- Eliminar código duplicado
```

### Arquitectura

```
Estoy construyendo [descripción del proyecto en 2-3 líneas].
Stack: [tecnologías que usas]

¿Qué estructura de carpetas recomiendas y por qué?
Muestra el árbol de directorios y una breve justificación de cada carpeta principal.
```

### Generación modular

En lugar de pedir todo a la vez, dividir en pasos:

```
Paso 1: "¿Qué interfaces/tipos TypeScript necesito para [componente]?"
Paso 2: "Genera el esqueleto del componente sin lógica"
Paso 3: "Agrega la lógica de [funcionalidad específica]"
Paso 4: "Agrega el manejo de errores y estados de carga"
```

---

## Cuándo usar prompts conversacionales vs estructurados

**Conversacional** (corto, sin estructura formal):
- Preguntas rápidas de concepto: *"¿Cuál es la diferencia entre `getStaticProps` y `getServerSideProps`?"*
- Dudas simples: *"¿Por qué usaría `const` en lugar de `let` aquí?"*
- Exploración inicial: *"¿Qué opciones tengo para manejar estado global en Astro?"*

**Estructurado** (con Rol + Contexto + Tarea + Formato):
- Generación de componentes o funciones completas
- Debugging de errores difíciles
- Refactorización de código existente
- Decisiones de arquitectura

---

## Técnicas avanzadas

**Chain-of-thought (razonamiento paso a paso)**
Pedir al modelo que piense antes de responder:
```
Antes de generar el código, explica:
1. Qué estructura vas a usar y por qué
2. Qué casos edge estás considerando
Luego genera el código.
```

**Restricción de incertidumbre**
```
Si no estás seguro de algo, dilo explícitamente en lugar de inventar.
Prefiero "no sé" a una respuesta incorrecta.
```

**Verificación cruzada**
Después de recibir una respuesta importante:
```
Genera 3 preguntas que alguien debería hacer para verificar si tu respuesta anterior es correcta.
Luego respóndelas.
```

---

## Errores comunes en prompts técnicos

| Error | Problema | Solución |
|---|---|---|
| "Arregla mi código" | Sin contexto del error | Incluir el error exacto |
| "Haz que sea mejor" | "Mejor" es subjetivo | Definir criterios: velocidad, legibilidad, etc. |
| "Genera todo el proyecto" | Tarea demasiado grande | Dividir en módulos |
| No indicar el stack | El modelo asume | Siempre mencionar framework y versión |
| Prompt en una sola línea | Difícil de procesar | Usar saltos de línea y secciones |

---

## Reutilización de prompts

Guardar como plantillas los prompts que funcionan bien. Una biblioteca de prompts personal evita reescribir desde cero y asegura consistencia en la calidad de las respuestas a lo largo del proyecto.

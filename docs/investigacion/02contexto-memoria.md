# Contexto y memoria en modelos de lenguaje

## Qué es la ventana de contexto

La ventana de contexto es la cantidad máxima de texto que un modelo puede procesar en una sola solicitud, medida en tokens. Todo lo que el modelo "ve" en ese momento —el historial de la conversación, las instrucciones del sistema, los archivos que se le adjuntan y su propia respuesta— compite por ese espacio.

Un token equivale aproximadamente a 0.75 palabras en inglés (en español suelen ser un poco más tokens por la misma cantidad de texto). Una ventana de 128,000 tokens equivale a unas 96,000 palabras, o alrededor de 300 páginas de texto.

---

## Cómo funciona realmente la "memoria"

El modelo **no recuerda** conversaciones anteriores. Lo que parece memoria es una ilusión generada por el software cliente: cada vez que envías un mensaje, la aplicación adjunta automáticamente todo el historial de la conversación al nuevo prompt. El modelo no está recordando, está siendo recordado.

Cuando la conversación crece demasiado y supera la ventana de contexto, las partes más antiguas simplemente se descartan o se comprimen. Es como una pizarra de tamaño fijo: cuando se llena, se borra lo más viejo para escribir lo nuevo.

---

## Ventanas de contexto por modelo (2025-2026)

| Modelo | Ventana de contexto |
|---|---|
| GPT-4.1 | 128,000 tokens |
| Claude Sonnet 4.6 | 1,000,000 tokens |
| Gemini 1.5 / 2.0 | hasta 2,000,000 tokens |
| Claude Haiku 4.5 | 200,000 tokens |

Una ventana grande no garantiza mejor calidad. Un estudio de Liu et al. (2024) publicado en *Transactions of the Association for Computational Linguistics* documentó el fenómeno "lost in the middle": los modelos rinden bien con información al inicio o al final del contexto, pero su rendimiento cae cuando la información relevante está en el medio. Más contexto no siempre es mejor.

---

## Degradación del contexto en práctica

A medida que la conversación se alarga, se observan estos síntomas:

- El modelo repite preguntas que ya fueron respondidas
- Genera respuestas contradictorias con lo que dijo antes
- Ignora instrucciones que se dieron al inicio de la conversación
- Pierde detalles específicos del código o arquitectura discutida

Esto no es un error del modelo sino una limitación arquitectónica. La solución más práctica es **iniciar una nueva conversación** cuando el tema cambia significativamente, llevando un resumen de los acuerdos importantes.

---

## Estrategias para manejar el contexto

**Resumir antes de cambiar de tema**
Antes de empezar una tarea nueva en la misma conversación, pedir al modelo que haga un resumen de los puntos clave acordados. Ese resumen se puede copiar al inicio de la siguiente conversación.

**Separar conversaciones por tarea**
Una conversación por componente o módulo del proyecto funciona mejor que una conversación larga que mezcla todo.

**Dar contexto explícito al inicio**
En lugar de depender del historial, incluir en cada prompt el contexto relevante: nombre del archivo, tecnología usada, fragmento de código involucrado.

**No asumir que el modelo "sabe" el estado actual**
Si se hicieron cambios en el código después del último mensaje, indicarlo explícitamente antes de hacer la siguiente pregunta.

---

## Diferencias entre modelos principales

| Característica | GPT (OpenAI) | Claude (Anthropic) | Gemini (Google) |
|---|---|---|---|
| Fortaleza en código | Alta | Muy alta | Media-alta |
| Contexto largo | 128K | 1M | 2M |
| Disponible gratis | Sí (limitado) | Sí (claude.ai) | Sí (limitado) |
| Alucinaciones en código | Moderadas | Bajas-moderadas | Moderadas |

Las diferencias en calidad de respuesta varían según el tipo de tarea. Para código y razonamiento técnico, Claude Sonnet y GPT-4 class models se consideran los más confiables actualmente.
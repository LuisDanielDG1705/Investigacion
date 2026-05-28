# Uso estratégico de modelos

## Familias de modelos y para qué sirven

Los proveedores principales (Anthropic, OpenAI, Google) organizan sus modelos en tres niveles:

| Nivel | Ejemplo | Cuándo usarlo |
|---|---|---|
| **Ligero / rápido** | Claude Haiku, GPT-5 Mini | Autocompletado, preguntas simples, tareas repetitivas |
| **Balanceado** | Claude Sonnet, GPT-4o | Desarrollo diario, debugging, generación de componentes |
| **Avanzado** | Claude Opus, GPT-5 | Arquitectura compleja, razonamiento multi-paso, refactorizaciones grandes |

En la práctica, el nivel balanceado cubre el 90% de las necesidades de desarrollo con un costo o consumo mucho menor que el nivel avanzado.

---

## Cuándo usar un modelo rápido

- Autocompletado de líneas mientras escribes código
- Preguntas con respuesta corta y predecible: *"¿Cómo se llama el hook de React para estado?"*
- Formateo o limpieza de código
- Conversión de formato: JSON a TypeScript interface, CSV a array, etc.
- Tareas que se repiten muchas veces (sub-agentes en pipelines automatizados)

Los modelos ligeros como Claude Haiku 4.5 responden casi instantáneamente y tienen rendimiento muy cercano a los modelos grandes en tareas estructuradas y bien definidas.

---

## Cuándo usar un modelo avanzado

- Diseño de arquitectura de un sistema nuevo
- Debugging de errores complejos con múltiples archivos involucrados
- Refactorización de código heredado o difícil de entender
- Decisiones de tecnología con trade-offs no obvios
- Generación de código que requiere mantener coherencia a lo largo de muchos archivos

Reservar los modelos avanzados para estas tareas específicas optimiza el consumo disponible en cuentas gratuitas o de bajo costo.

---

## Cuándo iniciar una nueva conversación

- Al cambiar de módulo o componente del proyecto
- Cuando el modelo empieza a repetir preguntas ya respondidas (señal de contexto lleno)
- Cuando las respuestas empiezan a contradecir decisiones tomadas antes en la conversación
- Al iniciar una tarea completamente diferente (de frontend a configuración de CI/CD, por ejemplo)
- Cuando la conversación lleva más de 30-40 mensajes

**Antes de cerrar una conversación larga**, pedir un resumen:
```
Resume en 5 puntos las decisiones técnicas más importantes que tomamos en esta conversación.
```
Ese resumen se pega al inicio de la siguiente conversación para mantener el contexto.

---

## Cuándo resumir el contexto en lugar de iniciar nuevo

Si la tarea aún no terminó pero la conversación ya está larga, resumir en lugar de cerrar:
```
El contexto de esta conversación está creciendo. Resume el estado actual del problema 
y los avances hechos en 3-4 líneas, como si fuera el inicio de una nueva conversación.
```
Copiar ese resumen, iniciar conversación nueva, pegarlo al inicio.

---

## Optimizar el consumo en cuentas gratuitas

**GitHub Copilot Free**: 2,000 completaciones + 50 chats al mes
- Usar el autocompletado con criterio, no activarlo para todo
- Reservar el chat para tareas que realmente lo requieren
- Si se agota, cambiar a Codeium como respaldo para completaciones

**Claude.ai gratuito**: límite de mensajes diarios (varía)
- Usar para tareas de razonamiento donde Copilot no es suficiente
- Conversaciones focalizadas: un problema por conversación
- No gastar mensajes en preguntas que se pueden responder con documentación

**Estrategia combinada recomendada:**
1. Copilot para autocompletado y preguntas rápidas mientras se codifica
2. Claude.ai para diseño, debugging complejo y decisiones de arquitectura
3. Documentación oficial siempre como verificación final

---

## Diferencia entre usar IA bien y usarla mal

| Uso improductivo | Uso estratégico |
|---|---|
| Pedir que genere todo el proyecto | Pedir módulos individuales con contexto claro |
| Copiar el código sin entenderlo | Revisar, preguntar y adaptar |
| Depender del historial de conversación largo | Iniciar conversaciones focalizadas |
| Usar el modelo avanzado para todo | Escalar el modelo según la complejidad |
| Asumir que el código generado funciona | Verificar, ejecutar y probar siempre |

El objetivo no es generar código automáticamente sino acelerar el proceso de desarrollo mientras se mantiene comprensión y control sobre el código del proyecto.
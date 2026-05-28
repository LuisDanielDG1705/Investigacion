# Investigacion# Etapa 0 — Workflows IA para Desarrollo

Documentación del workflow técnico para el uso de asistentes de inteligencia artificial integrados en Visual Studio Code, como parte del proyecto de migración del portafolio a Astro con CI/CD.

---

## Objetivo

Establecer criterios de uso, organización de contexto y buenas prácticas de integración IA dentro del flujo de desarrollo, evitando el uso improvisado de estos asistentes como simples generadores automáticos de código.

---

## Índice de documentos

| Archivo | Contenido |
|---|---|
| [01-entorno-vscode.md](./01entorno-vscode.md) | Extensiones IA disponibles, instalación y capacidades por plan |
| [02-contexto-memoria.md](./02contexto-memoria.md) | Cómo funciona la ventana de contexto y estrategias de manejo |
| [03-alucinaciones.md](./03alucinaciones.md) | Tipos de errores, señales de alerta y cómo mitigarlos |
| [04-optimizacion-prompts.md](./04optimizacion-prompts.md) | Estructura de prompts efectivos y técnicas avanzadas |
| [05-uso-modelos.md](./05uso-modelos.md) | Cuándo usar cada modelo y cómo optimizar el consumo gratuito |
| [06-biblioteca-prompts.md](./06biblioteca-prompts.md) | Plantillas reutilizables por categoría: debug, refactor, arquitectura, docs |

---

## Resumen de conclusiones

1. La calidad de los resultados del modelo depende casi enteramente de la calidad del prompt.
2. Los modelos no tienen memoria real: todo el historial se inyecta en cada solicitud, lo que consume el contexto disponible.
3. Entre el 20-45% del código generado puede contener errores o referencias a APIs inexistentes. Verificar siempre.
4. Para cuentas gratuitas, la estrategia óptima combina Copilot para autocompletado y Claude.ai para razonamiento y arquitectura.
5. Iniciar conversaciones nuevas y focalizadas produce mejores resultados que conversaciones largas y generales.

---

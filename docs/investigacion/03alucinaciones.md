# Limitaciones y alucinaciones técnicas

## Qué son las alucinaciones

Una alucinación ocurre cuando el modelo genera información que parece correcta y está redactada con confianza, pero es factualmente incorrecta o completamente inventada. En código, esto se traduce en:

- Funciones de una librería que no existen
- Nombres de paquetes npm o pip que nunca existieron
- Versiones de APIs que ya no son válidas
- Configuraciones que parecen legítimas pero generan errores en runtime
- Referencias a documentación que no existe en esa URL

Un estudio de 2025 encontró que entre el 29% y 45% del código generado por IA contiene vulnerabilidades de seguridad, y cerca del 20% de las recomendaciones de paquetes apuntan a librerías que no existen.

---

## Por qué ocurre

Los modelos están entrenados para producir respuestas que suenen correctas y coherentes, no para verificar si son verdad. Cuando el modelo no sabe algo con certeza, su comportamiento por defecto es generar la respuesta más plausible, no admitir la incertidumbre. Este comportamiento fue documentado por OpenAI (Kalai et al., 2025): los modelos aprenden que la confianza paga mejor que la duda durante el entrenamiento.

Hay dos tipos de alucinaciones:
- **Intrínsecas**: vienen de los datos de entrenamiento incompletos o sesgados
- **Extrínsecas**: el modelo genera algo que no está soportado por el contexto dado

---

## Señales de alerta en código generado

Desconfiar de la respuesta cuando:

- El modelo cita una función con parámetros muy específicos en una librería poco común
- Sugiere instalar un paquete con un nombre que nunca has visto
- Genera código para una versión de API muy específica sin haberla mencionado
- Explica con mucho detalle algo que no pudo haber aprendido bien (tecnología muy nueva o muy de nicho)
- Al preguntar "¿estás seguro?", cambia su respuesta sin justificación

---

## Estrategias de mitigación

**Verificar siempre antes de usar**
Cualquier nombre de función, paquete o endpoint que el modelo sugiera debe verificarse contra la documentación oficial antes de usarlo en el proyecto.

**Pedir al modelo que admita incertidumbre**
Incluir en el prompt frases como: *"Si no estás seguro, dímelo en lugar de inventar"*. Esto reduce (no elimina) las alucinaciones porque activa un comportamiento diferente en el modelo.

**Chain-of-thought para reducir errores**
Pedir al modelo que explique su razonamiento paso a paso antes de dar la respuesta final. Los errores se vuelven más visibles cuando el modelo muestra su trabajo. Ejemplo: *"Primero explica qué está causando el error, luego propón la solución"*.

**Usar el modelo como punto de partida, no como fuente de verdad**
El código generado es un borrador. Siempre revisarlo, entenderlo y probarlo antes de integrarlo.

**Separar tareas complejas**
En lugar de pedir "construye todo el componente", pedir "¿qué estructura de archivos necesito?", luego "genera el componente base", luego "agrega la lógica de estado". Las tareas pequeñas producen menos alucinaciones.

---

## Limitaciones adicionales a considerar

**Conocimiento desactualizado**
Los modelos tienen una fecha de corte de entrenamiento. Tecnologías que cambiaron después de esa fecha (nuevas versiones de frameworks, APIs deprecadas, librerías actualizadas) pueden generar respuestas incorrectas aunque el modelo las mencione con seguridad.

**Código largo y complejo**
A medida que el código solicitado crece en complejidad, la tasa de errores aumenta. Para proyectos grandes, es más efectivo pedir código modular en piezas pequeñas.

**Dependencias entre archivos**
Si el modelo no tiene acceso a todos los archivos relevantes del proyecto, puede generar código que asume importaciones o variables que no existen, o que entra en conflicto con código existente.

---

## Regla práctica

> Tratar la salida del modelo como código escrito por un colaborador junior inteligente pero despistado: revisar, probar, y nunca asumir que funciona hasta haberlo ejecutado.
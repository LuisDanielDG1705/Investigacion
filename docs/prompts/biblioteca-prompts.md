# Biblioteca de prompts

Colección de plantillas organizadas por categoría.

---

## Debugging

### Error de consola
```
Tengo este error en [nombre del archivo / navegador / terminal]:

ERROR:
[pegar el error exacto]

CÓDIGO:
[pegar el fragmento relevante]

Stack: [Astro / React / Vanilla JS / Node] versión [X]
¿Cuál es la causa y cómo la corrijo?
```

### Comportamiento inesperado (sin error en consola)
```
Este componente no se comporta como espero.

COMPORTAMIENTO ESPERADO: [describir qué debería pasar]
COMPORTAMIENTO ACTUAL: [describir qué está pasando]

CÓDIGO:
[código del componente]

¿Qué está causando la diferencia?
```

### Debugging paso a paso
```
Ayúdame a depurar este problema metodicamente.
Primero identifica las posibles causas ordenadas por probabilidad.
Luego sugiere qué verificar primero y cómo.

PROBLEMA: [descripción]
CÓDIGO: [código]
```

---

## Refactorización

### Mejorar legibilidad
```
Refactoriza este código para mejorar su legibilidad.
No cambies la funcionalidad.

CRITERIOS:
- Nombres de variables y funciones más descriptivos
- Eliminar código duplicado
- Separar en funciones más pequeñas si aplica

CÓDIGO:
[código]
```

### Optimizar rendimiento
```
Identifica los problemas de rendimiento en este código y propón mejoras.
Explica el impacto de cada cambio antes de mostrarlo.

CÓDIGO:
[código]
CONTEXTO: Se ejecuta [frecuencia / en qué parte de la app]
```

### Convertir a componente reutilizable
```
Convierte este código hardcodeado en un componente reutilizable.
Identifica qué partes deben ser props y cuáles pueden tener valores por defecto.

CÓDIGO ACTUAL:
[código]
TECNOLOGÍA: [Astro / React / Web Components]
```

---

## Arquitectura

### Estructura de proyecto
```
Estoy construyendo [descripción del proyecto en 2-3 líneas].

Stack: [tecnologías]
Escala esperada: [pequeño / mediano / solo yo / equipo]

¿Qué estructura de carpetas recomiendas?
Muestra el árbol de directorios con una línea de descripción por carpeta principal.
```

### Decisión entre opciones
```
Necesito decidir entre estas opciones para [problema específico]:
- Opción A: [nombre y descripción breve]
- Opción B: [nombre y descripción breve]

Mi caso de uso: [describir el contexto]
Prioridades: [velocidad de desarrollo / escalabilidad / simplicidad]

¿Cuál recomiendas y por qué? Menciona los trade-offs de cada una.
```

### Diseño de componente
```
Necesito diseñar el componente [nombre].

RESPONSABILIDAD: [qué hace exactamente]
ENTRADAS (props): [qué datos recibe]
SALIDA: [qué renderiza o retorna]
INTERACCIONES: [eventos que maneja]

¿Qué estructura interna propones antes de escribir el código?
```

---

## Documentación

### JSDoc para función
```
Genera un comentario JSDoc para esta función.
Incluye descripción, @param con tipos y descripción, @returns y un @example.

FUNCIÓN:
[código de la función]
```

### README de componente
```
Genera la documentación de uso para este componente en formato Markdown.
Incluye: descripción, props con tipos y descripción, ejemplo de uso básico.

COMPONENTE:
[código]
```

### Comentarios inline
```
Agrega comentarios inline a este código explicando las partes no obvias.
No comentar lo que ya es evidente por el nombre de la variable o función.

CÓDIGO:
[código]
```

---

## Troubleshooting

### Instalación / configuración que falla
```
Estoy intentando configurar [herramienta / librería] y algo no funciona.

SISTEMA: [OS / versión de Node / versión del package manager]
COMANDO QUE EJECUTÉ: [comando exacto]
RESULTADO: [output exacto]
LO QUE ESPERABA: [comportamiento esperado]

¿Qué puede estar pasando?
```

### Conflicto de dependencias
```
Al instalar [paquete] obtengo este error de dependencias:

[error]

Mi package.json relevante:
[sección de dependencies]

¿Cómo resuelvo este conflicto?
```

### Algo que funcionaba dejó de funcionar
```
Este código funcionaba y dejó de funcionar después de [cambio que hice].

CAMBIO REALIZADO: [qué modifiqué]
ERROR ACTUAL: [error o comportamiento]
CÓDIGO ANTES DEL CAMBIO: [si lo tienes]
CÓDIGO ACTUAL: [código]

¿Qué puede haber roto?
```

---

## Generación de código

### Componente nuevo desde cero
```
Eres un desarrollador [Astro / React] senior.

Genera el componente [nombre] con estas características:
- [característica 1]
- [característica 2]

PROPS: [lista de props con tipos]
ESTILOS: [CSS módulos / Tailwind / scoped]
NOTAS: [cualquier restricción o preferencia]

Responde solo con el código. Sin explicaciones.
```

### Función utilitaria
```
Genera una función [nombre] que [descripción de qué hace].

ENTRADAS: [parámetros y tipos]
SALIDA: [qué retorna]
CASOS EDGE A MANEJAR: [lista si aplica]

Incluye TypeScript si aplica y un ejemplo de uso al final como comentario.
```

### Test unitario
```
Genera tests unitarios para esta función usando [Jest / Vitest].
Cubre: casos edge y manejo de errores.

FUNCIÓN:
[código]
```
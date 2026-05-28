# Configuración del entorno IA en VS Code

## Extensiones disponibles

El ecosistema de asistentes IA para VS Code en 2026 se divide principalmente en tres opciones relevantes para cuentas gratuitas:

| Extensión | Plan gratuito | Límite | Integración con GitHub |
|---|---|---|---|
| **GitHub Copilot** | Sí | 2,000 completaciones/mes | Nativa |
| **Codeium (Windsurf)** | Sí | Completaciones ilimitadas | Manual |
| **Continue** | Sí | Sin límites (modelos propios) | Manual |

### GitHub Copilot Free
- Se instala desde el marketplace de VS Code buscando `GitHub Copilot`
- Requiere cuenta de GitHub (gratuita)
- Ofrece 2,000 completaciones de código al mes y 50 mensajes de chat
- Se autentica directamente con la cuenta de GitHub, lo que le da contexto del repositorio activo

### Codeium / Windsurf
- Completaciones de código ilimitadas sin costo
- No entrena modelos con tu código (ventaja de privacidad)
- En 2025 Codeium se rebrandeó como Windsurf para enfatizar sus capacidades agénticas
- Disponible como extensión de VS Code o como editor independiente (fork de VS Code)

### Continue (código abierto)
- Permite conectar modelos propios (locales con Ollama, o APIs externas)
- Sin límites de uso porque tú controlas el modelo
- Ideal si se quiere experimentar con modelos locales sin costo de API

---

## Pasos de instalación (GitHub Copilot Free)

1. Abrir VS Code → pestaña Extensiones (`Ctrl+Shift+X`)
2. Buscar `GitHub Copilot` e instalar (también instalar `GitHub Copilot Chat`)
3. Ir a la barra de estado inferior → hacer clic en el ícono de Copilot → iniciar sesión con GitHub
4. Verificar que el ícono de Copilot no muestre error en la barra inferior
5. Abrir un archivo `.js` o `.html` y escribir un comentario para probar que sugiere código

---

## Integración con repositorios

Copilot lee el contexto del archivo activo y de archivos abiertos en otras pestañas. Para darle mejor contexto del proyecto:

- Tener abiertos los archivos más relevantes del proyecto en pestañas
- Escribir comentarios descriptivos antes del código que se quiere generar
- En proyectos con muchos archivos, abrir específicamente los que tienen las interfaces o tipos que se usan

---

## Capacidades disponibles en cuenta gratuita

| Capacidad | Disponible |
|---|---|
| Autocompletado inline | ✅ |
| Chat en panel lateral | ✅ (limitado) |
| Generación desde comentarios | ✅ |
| Explicación de código seleccionado | ✅ |
| Corrección de errores | ✅ |
| Acceso a GPT-4o o modelos avanzados | ❌ (solo en plan de pago) |
| Indexación completa del repositorio | ❌ |

---

## Notas sobre el plan gratuito

El límite de 2,000 completaciones mensuales de GitHub Copilot Free es suficiente para un desarrollador que está aprendiendo, ya que se pasa más tiempo leyendo y entendiendo código que generándolo. Cuando se llega al límite, Copilot simplemente deja de sugerir hasta el siguiente mes. Como alternativa de respaldo, Codeium puede funcionar en paralelo sin límite de completaciones.
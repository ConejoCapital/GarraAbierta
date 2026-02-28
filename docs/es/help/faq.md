---
summary: "Preguntas frecuentes sobre la instalación, configuración y uso de OpenClaw"
read_when:
  - Answering common setup, install, onboarding, or runtime support questions
  - Triaging user-reported issues before deeper debugging
title: "Preguntas frecuentes"
---

# Preguntas frecuentes

Respuestas rápidas y solución de problemas para configuraciones reales (desarrollo local, VPS, multi-agente, OAuth/claves API, conmutación por error de modelos). Para diagnósticos en tiempo de ejecución, consulta [Solución de problemas](/gateway/troubleshooting). Para la referencia completa de configuración, consulta [Configuración](/gateway/configuration).

## Los primeros 60 segundos si algo no funciona

1. **Estado rápido (primera verificación)**

   ```bash
   openclaw status
   ```

   Resumen local rápido: SO + actualización, alcance del gateway/servicio, agentes/sesiones, configuración del proveedor + problemas en tiempo de ejecución (cuando el gateway es alcanzable).

2. **Reporte para compartir (seguro)**

   ```bash
   openclaw status --all
   ```

   Diagnóstico de solo lectura con cola de logs (tokens redactados).

3. **Estado del daemon + puerto**

   ```bash
   openclaw gateway status
   ```

   Muestra el runtime del supervisor vs la disponibilidad RPC, la URL objetivo del probe y qué configuración probablemente usó el servicio.

4. **Pruebas profundas**

   ```bash
   openclaw status --deep
   ```

   Ejecuta verificaciones de salud del gateway + pruebas de proveedores (requiere un gateway alcanzable). Consulta [Health](/gateway/health).

5. **Seguir el log más reciente**

   ```bash
   openclaw logs --follow
   ```

   Si el RPC no responde, usa como alternativa:

   ```bash
   tail -f "$(ls -t /tmp/openclaw/openclaw-*.log | head -1)"
   ```

   Los logs de archivo son separados de los logs del servicio; consulta [Logging](/logging) y [Solución de problemas](/gateway/troubleshooting).

6. **Ejecutar el doctor (reparaciones)**

   ```bash
   openclaw doctor
   ```

   Repara/migra configuración/estado + ejecuta verificaciones de salud. Consulta [Doctor](/gateway/doctor).

7. **Instantánea del Gateway**

   ```bash
   openclaw health --json
   openclaw health --verbose   # muestra la URL objetivo + ruta de config en errores
   ```

   Le pide al gateway en ejecución una instantánea completa (solo WS). Consulta [Health](/gateway/health).

## Inicio rápido y primera configuración

### Estoy atascado, ¿cuál es la forma más rápida de resolver problemas?

Usa un agente de IA local que pueda **ver tu máquina**. Eso es mucho más efectivo que preguntar en Discord, porque la mayoría de los casos de "estoy atascado" son **problemas locales de configuración o entorno** que los ayudantes remotos no pueden inspeccionar.

- **Claude Code**: [https://www.anthropic.com/claude-code/](https://www.anthropic.com/claude-code/)
- **OpenAI Codex**: [https://openai.com/codex/](https://openai.com/codex/)

Estas herramientas pueden leer el repositorio, ejecutar comandos, inspeccionar logs y ayudar a corregir la configuración a nivel de tu máquina (PATH, servicios, permisos, archivos de autenticación). Dales el **checkout completo del código fuente** mediante la instalación hackeable (git):

```bash
curl -fsSL https://openclaw.ai/install.sh | bash -s -- --install-method git
```

Esto instala OpenClaw **desde un checkout de git**, para que el agente pueda leer el código + docs y razonar sobre la versión exacta que estás ejecutando. Siempre puedes volver a la versión estable después re-ejecutando el instalador sin `--install-method git`.

Consejo: pídele al agente que **planifique y supervise** la corrección (paso a paso), luego ejecuta solo los comandos necesarios. Eso mantiene los cambios pequeños y más fáciles de auditar.

Si descubres un bug real o una corrección, por favor abre un issue en GitHub o envía un PR:
[https://github.com/openclaw/openclaw/issues](https://github.com/openclaw/openclaw/issues)
[https://github.com/openclaw/openclaw/pulls](https://github.com/openclaw/openclaw/pulls)

Empieza con estos comandos (comparte las salidas cuando pidas ayuda):

```bash
openclaw status
openclaw models status
openclaw doctor
```

Qué hacen:

- `openclaw status`: instantánea rápida del estado del gateway/agente + configuración básica.
- `openclaw models status`: verifica la autenticación del proveedor + disponibilidad del modelo.
- `openclaw doctor`: valida y repara problemas comunes de configuración/estado.

Otras verificaciones útiles del CLI: `openclaw status --all`, `openclaw logs --follow`,
`openclaw gateway status`, `openclaw health --verbose`.

Bucle rápido de depuración: [Los primeros 60 segundos si algo no funciona](#los-primeros-60-segundos-si-algo-no-funciona).
Docs de instalación: [Instalar](/es/install), [Flags del instalador](/install/installer), [Actualizar](/install/updating).

### ¿Cuál es la forma recomendada de instalar y configurar OpenClaw?

El repositorio recomienda ejecutar desde código fuente y usar el asistente de configuración:

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
openclaw onboard --install-daemon
```

El asistente también puede compilar los assets de la interfaz automáticamente. Después de la configuración inicial, normalmente ejecutas el Gateway en el puerto **18789**.

Desde código fuente (contribuidores/dev):

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
pnpm install
pnpm build
pnpm ui:build # instala automáticamente las dependencias de UI en la primera ejecución
openclaw onboard
```

Si aún no tienes una instalación global, ejecútalo con `pnpm openclaw onboard`.

---

> **🌎 ¡Ayúdanos a traducir!**
>
> Esta página solo tiene las primeras secciones traducidas al español. El FAQ completo en inglés tiene más de 100 preguntas sobre configuración, canales, modelos, seguridad y más.
>
> Si quieres contribuir traduciendo más secciones, consulta [CONTRIBUIR.md](https://github.com/ConejoCapital/GarraAbierta/blob/main/CONTRIBUIR.md) y envía un PR. ¡Toda ayuda cuenta!
>
> Mientras tanto, puedes consultar el [FAQ completo en inglés](/help/faq).

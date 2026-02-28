---
summary: "Asistente de configuración CLI: configuración guiada para gateway, espacio de trabajo, canales y skills"
read_when:
  - Running or configuring the onboarding wizard
  - Setting up a new machine
title: "Asistente de configuración (CLI)"
sidebarTitle: "Configuración inicial: CLI"
---

# Asistente de configuración (CLI)

El asistente de configuración es la forma **recomendada** de configurar OpenClaw en macOS,
Linux o Windows (vía WSL2; muy recomendado).
Configura un Gateway local o una conexión a un Gateway remoto, además de canales, skills
y valores predeterminados del espacio de trabajo en un solo flujo guiado.

```bash
openclaw onboard
```

<Info>
Chat más rápido: abre la interfaz Control (no necesitas configurar ningún canal). Ejecuta
`openclaw dashboard` y chatea en el navegador. Docs: [Panel](/web/dashboard).
</Info>

Para reconfigurar después:

```bash
openclaw configure
openclaw agents add <name>
```

<Note>
`--json` no implica modo no interactivo. Para scripts, usa `--non-interactive`.
</Note>

<Tip>
Recomendado: configura una clave de API de Brave Search para que el agente pueda usar `web_search`
(`web_fetch` funciona sin clave). La forma más fácil: `openclaw configure --section web`
que almacena `tools.web.search.apiKey`. Docs: [Herramientas web](/tools/web).
</Tip>

## QuickStart vs Avanzado

El asistente comienza con **QuickStart** (valores predeterminados) vs **Avanzado** (control total).

<Tabs>
  <Tab title="QuickStart (predeterminados)">
    - Gateway local (loopback)
    - Espacio de trabajo predeterminado (o espacio de trabajo existente)
    - Puerto del Gateway **18789**
    - Autenticación del Gateway **Token** (auto-generado, incluso en loopback)
    - Aislamiento de mensajes directos predeterminado: la configuración local escribe `session.dmScope: "per-channel-peer"` cuando no está establecido. Detalles: [Referencia de configuración CLI](/start/wizard-cli-reference#outputs-and-internals)
    - Exposición Tailscale **Desactivada**
    - Los mensajes directos de Telegram + WhatsApp usan **lista de permitidos** por defecto (se te pedirá tu número de teléfono)
  </Tab>
  <Tab title="Avanzado (control total)">
    - Expone cada paso (modo, espacio de trabajo, gateway, canales, daemon, skills).
  </Tab>
</Tabs>

## Qué configura el asistente

El **modo local (predeterminado)** te guía por estos pasos:

1. **Modelo/Autenticación** — Clave de API de Anthropic (recomendado), OpenAI o Proveedor personalizado
   (compatible con OpenAI, compatible con Anthropic, o auto-detección desconocida). Elige un modelo predeterminado.
   Para ejecuciones no interactivas, `--secret-input-mode ref` almacena referencias respaldadas por variables de entorno en perfiles de autenticación en lugar de valores de clave API en texto plano.
   En modo no interactivo `ref`, la variable de entorno del proveedor debe estar establecida; pasar flags de clave en línea sin esa variable de entorno falla inmediatamente.
   En ejecuciones interactivas, elegir el modo de referencia secreta te permite apuntar a una variable de entorno o a una referencia de proveedor configurada (`file` o `exec`), con una validación previa rápida antes de guardar.
2. **Espacio de trabajo** — Ubicación para archivos del agente (predeterminado `~/.openclaw/workspace`). Genera archivos de bootstrap.
3. **Gateway** — Puerto, dirección de bind, modo de autenticación, exposición Tailscale.
4. **Canales** — WhatsApp, Telegram, Discord, Google Chat, Mattermost, Signal, BlueBubbles o iMessage.
5. **Daemon** — Instala un LaunchAgent (macOS) o unidad systemd de usuario (Linux/WSL2).
6. **Verificación de salud** — Inicia el Gateway y verifica que está corriendo.
7. **Skills** — Instala skills recomendadas y dependencias opcionales.

<Note>
Re-ejecutar el asistente **no** borra nada a menos que elijas explícitamente **Restablecer** (o pases `--reset`).
El `--reset` del CLI restablece por defecto configuración, credenciales y sesiones; usa `--reset-scope full` para incluir el espacio de trabajo.
Si la configuración es inválida o contiene claves legacy, el asistente te pide que ejecutes `openclaw doctor` primero.
</Note>

El **modo remoto** solo configura el cliente local para conectarse a un Gateway en otro lugar.
**No** instala ni cambia nada en el host remoto.

## Agregar otro agente

Usa `openclaw agents add <name>` para crear un agente separado con su propio espacio de trabajo,
sesiones y perfiles de autenticación. Ejecutarlo sin `--workspace` lanza el asistente.

Lo que establece:

- `agents.list[].name`
- `agents.list[].workspace`
- `agents.list[].agentDir`

Notas:

- Los espacios de trabajo predeterminados siguen `~/.openclaw/workspace-<agentId>`.
- Agrega `bindings` para enrutar mensajes entrantes (el asistente puede hacer esto).
- Flags no interactivas: `--model`, `--agent-dir`, `--bind`, `--non-interactive`.

## Referencia completa

Para desgloses detallados paso a paso, scripting no interactivo, configuración de Signal,
API RPC y una lista completa de campos de configuración que escribe el asistente, consulta la
[Referencia del asistente](/reference/wizard).

## Documentación relacionada

- Referencia de comandos CLI: [`openclaw onboard`](/cli/onboard)
- Visión general de la configuración inicial: [Visión general de la configuración inicial](/start/onboarding-overview)
- Configuración inicial en app macOS: [Configuración inicial](/start/onboarding)
- Ritual de primera ejecución del agente: [Bootstrapping del agente](/start/bootstrapping)

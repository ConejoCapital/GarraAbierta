---
summary: "OpenClaw es un gateway multicanal para agentes de IA que funciona en cualquier sistema operativo."
read_when:
  - Introducing OpenClaw to newcomers
title: "OpenClaw"
---

# OpenClaw 🦞

<p align="center">
    <img
        src="/assets/openclaw-logo-text-dark.png"
        alt="OpenClaw"
        width="500"
        class="dark:hidden"
    />
    <img
        src="/assets/openclaw-logo-text.png"
        alt="OpenClaw"
        width="500"
        class="hidden dark:block"
    />
</p>

> _"EXFOLIATE! EXFOLIATE!"_ — Una langosta espacial, probablemente

<p align="center">
  <strong>Gateway para cualquier SO que conecta agentes de IA a WhatsApp, Telegram, Discord, iMessage y más.</strong><br />
  Envía un mensaje, recibe una respuesta de tu agente desde el bolsillo. Los plugins añaden Mattermost y más.
</p>

<Columns>
  <Card title="Primeros pasos" href="/es/start/getting-started" icon="rocket">
    Instala OpenClaw y levanta el Gateway en minutos.
  </Card>
  <Card title="Ejecuta el asistente" href="/es/start/wizard" icon="sparkles">
    Configuración guiada con `openclaw onboard` y flujos de emparejamiento.
  </Card>
  <Card title="Abre la interfaz Control" href="/web/control-ui" icon="layout-dashboard">
    Abre el panel del navegador para chat, configuración y sesiones.
  </Card>
</Columns>

## ¿Qué es OpenClaw?

OpenClaw es un **gateway autoalojado** que conecta tus apps de chat favoritas — WhatsApp, Telegram, Discord, iMessage y más — a agentes de IA para programación como Pi. Ejecutas un solo proceso Gateway en tu propia máquina (o un servidor), y se convierte en el puente entre tus apps de mensajería y un asistente de IA siempre disponible.

**¿Para quién es?** Desarrolladores y usuarios avanzados que quieren un asistente de IA personal al que puedan escribirle desde cualquier lugar — sin perder el control de sus datos ni depender de un servicio alojado.

**¿Qué lo hace diferente?**

- **Autoalojado**: se ejecuta en tu hardware, tus reglas
- **Multicanal**: un Gateway sirve WhatsApp, Telegram, Discord y más simultáneamente
- **Nativo para agentes**: construido para agentes de programación con uso de herramientas, sesiones, memoria y enrutamiento multi-agente
- **Código abierto**: licencia MIT, impulsado por la comunidad

**¿Qué necesitas?** Node 22+, una clave de API (se recomienda Anthropic) y 5 minutos.

## Cómo funciona

```mermaid
flowchart LR
  A["Apps de chat + plugins"] --> B["Gateway"]
  B --> C["Agente Pi"]
  B --> D["CLI"]
  B --> E["Interfaz web Control"]
  B --> F["App macOS"]
  B --> G["Nodos iOS y Android"]
```

El Gateway es la fuente única de verdad para sesiones, enrutamiento y conexiones de canales.

## Capacidades clave

<Columns>
  <Card title="Gateway multicanal" icon="network">
    WhatsApp, Telegram, Discord e iMessage con un solo proceso Gateway.
  </Card>
  <Card title="Canales por plugin" icon="plug">
    Añade Mattermost y más con paquetes de extensiones.
  </Card>
  <Card title="Enrutamiento multi-agente" icon="route">
    Sesiones aisladas por agente, espacio de trabajo o remitente.
  </Card>
  <Card title="Soporte multimedia" icon="image">
    Envía y recibe imágenes, audio y documentos.
  </Card>
  <Card title="Interfaz web Control" icon="monitor">
    Panel en el navegador para chat, configuración, sesiones y nodos.
  </Card>
  <Card title="Nodos móviles" icon="smartphone">
    Conecta nodos iOS y Android con soporte Canvas.
  </Card>
</Columns>

## Inicio rápido

<Steps>
  <Step title="Instala OpenClaw">
    ```bash
    npm install -g openclaw@latest
    ```
  </Step>
  <Step title="Configura e instala el servicio">
    ```bash
    openclaw onboard --install-daemon
    ```
  </Step>
  <Step title="Conecta WhatsApp e inicia el Gateway">
    ```bash
    openclaw channels login
    openclaw gateway --port 18789
    ```
  </Step>
</Steps>

¿Necesitas la instalación completa y configuración de desarrollo? Ve [Inicio rápido](/start/quickstart).

## Panel de control

Abre la interfaz Control en el navegador después de iniciar el Gateway.

- Local por defecto: [http://127.0.0.1:18789/](http://127.0.0.1:18789/)
- Acceso remoto: [Superficies web](/web) y [Tailscale](/gateway/tailscale)

<p align="center">
  <img src="whatsapp-openclaw.jpg" alt="OpenClaw" width="420" />
</p>

## Configuración (opcional)

La configuración se encuentra en `~/.openclaw/openclaw.json`.

- Si **no haces nada**, OpenClaw usa el binario de Pi incluido en modo RPC con sesiones por remitente.
- Si quieres restringir el acceso, empieza con `channels.whatsapp.allowFrom` y (para grupos) reglas de mención.

Ejemplo:

```json5
{
  channels: {
    whatsapp: {
      allowFrom: ["+15555550123"],
      groups: { "*": { requireMention: true } },
    },
  },
  messages: { groupChat: { mentionPatterns: ["@openclaw"] } },
}
```

## Empieza aquí

<Columns>
  <Card title="Hubs de documentación" href="/start/hubs" icon="book-open">
    Toda la documentación y guías, organizadas por caso de uso.
  </Card>
  <Card title="Configuración" href="/gateway/configuration" icon="settings">
    Ajustes principales del Gateway, tokens y configuración de proveedores.
  </Card>
  <Card title="Acceso remoto" href="/gateway/remote" icon="globe">
    Patrones de acceso por SSH y tailnet.
  </Card>
  <Card title="Canales" href="/channels/telegram" icon="message-square">
    Configuración específica por canal para WhatsApp, Telegram, Discord y más.
  </Card>
  <Card title="Nodos" href="/nodes" icon="smartphone">
    Nodos iOS y Android con emparejamiento y Canvas.
  </Card>
  <Card title="Ayuda" href="/help" icon="life-buoy">
    Soluciones comunes y punto de entrada para solución de problemas.
  </Card>
</Columns>

## Más información

<Columns>
  <Card title="Lista completa de características" href="/es/concepts/features" icon="list">
    Capacidades completas de canales, enrutamiento y multimedia.
  </Card>
  <Card title="Enrutamiento multi-agente" href="/concepts/multi-agent" icon="route">
    Aislamiento de espacios de trabajo y sesiones por agente.
  </Card>
  <Card title="Seguridad" href="/gateway/security" icon="shield">
    Tokens, listas de permitidos y controles de seguridad.
  </Card>
  <Card title="Solución de problemas" href="/gateway/troubleshooting" icon="wrench">
    Diagnósticos del Gateway y errores comunes.
  </Card>
  <Card title="Acerca de y créditos" href="/reference/credits" icon="info">
    Orígenes del proyecto, contribuidores y licencia.
  </Card>
</Columns>

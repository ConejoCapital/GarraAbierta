---
summary: "Capacidades de OpenClaw en canales, enrutamiento, multimedia y experiencia de usuario."
read_when:
  - You want a full list of what OpenClaw supports
title: "Características"
---

## Destacados

<Columns>
  <Card title="Canales" icon="message-square">
    WhatsApp, Telegram, Discord e iMessage con un solo Gateway.
  </Card>
  <Card title="Plugins" icon="plug">
    Añade Mattermost y más con extensiones.
  </Card>
  <Card title="Enrutamiento" icon="route">
    Enrutamiento multi-agente con sesiones aisladas.
  </Card>
  <Card title="Multimedia" icon="image">
    Imágenes, audio y documentos de entrada y salida.
  </Card>
  <Card title="Apps e interfaz" icon="monitor">
    Interfaz web Control y app complementaria para macOS.
  </Card>
  <Card title="Nodos móviles" icon="smartphone">
    Nodos iOS y Android con soporte Canvas.
  </Card>
</Columns>

## Lista completa

- Integración con WhatsApp vía WhatsApp Web (Baileys)
- Soporte de bot de Telegram (grammY)
- Soporte de bot de Discord (channels.discord.js)
- Soporte de bot de Mattermost (plugin)
- Integración con iMessage vía imsg CLI local (macOS)
- Puente de agente para Pi en modo RPC con transmisión de herramientas
- Streaming y fragmentación para respuestas largas
- Enrutamiento multi-agente para sesiones aisladas por espacio de trabajo o remitente
- Autenticación por suscripción para Anthropic y OpenAI vía OAuth
- Sesiones: los chats directos se colapsan en un `main` compartido; los grupos se aíslan
- Soporte de chat grupal con activación basada en menciones
- Soporte multimedia para imágenes, audio y documentos
- Hook opcional de transcripción de notas de voz
- WebChat y app de barra de menú para macOS
- Nodo iOS con emparejamiento y superficie Canvas
- Nodo Android con emparejamiento, Canvas, chat y cámara

<Note>
Los paths legacy de Claude, Codex, Gemini y Opencode han sido eliminados. Pi es el único
path de agente de programación.
</Note>

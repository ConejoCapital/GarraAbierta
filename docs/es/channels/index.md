---
summary: "Plataformas de mensajería a las que OpenClaw puede conectarse"
read_when:
  - You want to choose a chat channel for OpenClaw
  - You need a quick overview of supported messaging platforms
title: "Canales de chat"
---

# Canales de chat

OpenClaw puede comunicarse contigo en cualquier app de chat que ya uses. Cada canal se conecta a través del Gateway.
El texto es compatible en todos; el soporte multimedia y de reacciones varía por canal.

## Canales compatibles

- [WhatsApp](/channels/whatsapp) — El más popular; usa Baileys y requiere emparejamiento por QR.
- [Telegram](/channels/telegram) — Bot API vía grammY; compatible con grupos.
- [Discord](/channels/discord) — Discord Bot API + Gateway; compatible con servidores, canales y mensajes directos.
- [IRC](/channels/irc) — Servidores IRC clásicos; canales + mensajes directos con controles de emparejamiento/lista de permitidos.
- [Slack](/channels/slack) — Bolt SDK; apps de espacio de trabajo.
- [Feishu](/channels/feishu) — Bot de Feishu/Lark vía WebSocket (plugin, se instala por separado).
- [Google Chat](/channels/googlechat) — App de Google Chat API vía webhook HTTP.
- [Mattermost](/channels/mattermost) — Bot API + WebSocket; canales, grupos, mensajes directos (plugin, se instala por separado).
- [Signal](/channels/signal) — signal-cli; enfocado en privacidad.
- [BlueBubbles](/channels/bluebubbles) — **Recomendado para iMessage**; usa la API REST del servidor macOS de BlueBubbles con soporte completo de características (editar, cancelar envío, efectos, reacciones, gestión de grupos — la edición actualmente no funciona en macOS 26 Tahoe).
- [iMessage (legacy)](/channels/imessage) — Integración legacy de macOS vía imsg CLI (obsoleta, usa BlueBubbles para nuevas configuraciones).
- [Microsoft Teams](/channels/msteams) — Bot Framework; soporte empresarial (plugin, se instala por separado).
- [Synology Chat](/channels/synology-chat) — Chat de Synology NAS vía webhooks entrantes+salientes (plugin, se instala por separado).
- [LINE](/channels/line) — Bot de LINE Messaging API (plugin, se instala por separado).
- [Nextcloud Talk](/channels/nextcloud-talk) — Chat autoalojado vía Nextcloud Talk (plugin, se instala por separado).
- [Matrix](/channels/matrix) — Protocolo Matrix (plugin, se instala por separado).
- [Nostr](/channels/nostr) — Mensajes directos descentralizados vía NIP-04 (plugin, se instala por separado).
- [Tlon](/channels/tlon) — Mensajero basado en Urbit (plugin, se instala por separado).
- [Twitch](/channels/twitch) — Chat de Twitch vía conexión IRC (plugin, se instala por separado).
- [Zalo](/channels/zalo) — Zalo Bot API; el mensajero popular de Vietnam (plugin, se instala por separado).
- [Zalo Personal](/channels/zalouser) — Cuenta personal de Zalo vía login QR (plugin, se instala por separado).
- [WebChat](/web/webchat) — Interfaz WebChat del Gateway sobre WebSocket.

## Notas

- Los canales pueden ejecutarse simultáneamente; configura varios y OpenClaw enrutará por chat.
- La configuración más rápida suele ser **Telegram** (un simple token de bot). WhatsApp requiere emparejamiento por QR y almacena más estado en disco.
- El comportamiento en grupos varía por canal; consulta [Grupos](/channels/groups).
- El emparejamiento y las listas de permitidos para mensajes directos se aplican por seguridad; consulta [Seguridad](/gateway/security).
- Solución de problemas: [Solución de problemas de canales](/channels/troubleshooting).
- Los proveedores de modelos se documentan por separado; consulta [Proveedores de modelos](/providers/models).

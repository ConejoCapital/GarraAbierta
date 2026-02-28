# 🦞 GarraAbierta — Asistente Personal de IA

> **garra** = claw &nbsp;|&nbsp; **abierta** = open — la traduccion al espanol de OpenClaw

<p align="center">
    <picture>
        <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/ConejoCapital/GarraAbierta/main/docs/assets/openclaw-logo-text-dark.png">
        <img src="https://raw.githubusercontent.com/ConejoCapital/GarraAbierta/main/docs/assets/openclaw-logo-text.png" alt="GarraAbierta" width="500">
    </picture>
</p>

<p align="center">
  <a href="https://github.com/ConejoCapital/GarraAbierta/actions/workflows/ci.yml?branch=main"><img src="https://img.shields.io/github/actions/workflow/status/ConejoCapital/GarraAbierta/ci.yml?branch=main&style=for-the-badge" alt="CI status"></a>
  <a href="https://github.com/ConejoCapital/GarraAbierta/releases"><img src="https://img.shields.io/github/v/release/ConejoCapital/GarraAbierta?include_prereleases&style=for-the-badge" alt="GitHub release"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/discord/1456350064065904867?label=Discord&logo=discord&logoColor=white&color=5865F2&style=for-the-badge" alt="Discord"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="Licencia MIT"></a>
</p>

---

## Creditos y origen

> **GarraAbierta es un fork en espanol de [OpenClaw](https://github.com/openclaw/openclaw).**

Este fork existe porque los mantenedores de OpenClaw declararon que no tienen capacidad para aceptar traducciones a nuevos idiomas y cerraran los PRs de traduccion. Puedes leer el contexto completo en el [issue #3460](https://github.com/openclaw/openclaw/issues/3460).

**Todo el merito del codigo va para el equipo de OpenClaw y sus mantenedores.** Nosotros solo traducimos la documentacion y la interfaz para que la comunidad hispanohablante pueda aprovechar este proyecto sin barreras de idioma.

---

## Que es GarraAbierta?

**GarraAbierta** (OpenClaw) es un _asistente personal de IA_ que corre en tus propios dispositivos. Te responde en los canales que ya usas a diario:

- **WhatsApp**
- **Telegram**
- **Slack**
- **Discord**
- **Google Chat**
- **Signal**
- **iMessage**
- **Microsoft Teams**
- **WebChat**

Ademas soporta canales de extension como BlueBubbles, Matrix y Zalo. Puede hablar y escuchar en macOS/iOS/Android, y renderizar un Canvas en vivo que tu controlas.

El Gateway es solo el plano de control — el producto es el asistente.

Si quieres un asistente personal, de un solo usuario, que se sienta local, rapido y siempre encendido, esto es para ti.

[Sitio web](https://openclaw.ai) · [Documentacion](https://docs.openclaw.ai) · [Primeros pasos](https://docs.openclaw.ai/start/getting-started) · [FAQ](https://docs.openclaw.ai/help/faq) · [Discord](https://discord.gg/clawd)

## Instalacion (recomendada)

Requisito: **Node >= 22**.

```bash
npm install -g openclaw@latest
# o bien: pnpm add -g openclaw@latest

openclaw onboard --install-daemon
```

El asistente de configuracion instala el daemon del Gateway (servicio de usuario launchd/systemd) para que se mantenga corriendo en segundo plano.

## Inicio rapido

Requisito: **Node >= 22**.

Guia completa para principiantes (autenticacion, emparejamiento, canales): [Primeros pasos](https://docs.openclaw.ai/start/getting-started)

```bash
# Inicia el asistente de configuracion e instala el daemon
openclaw onboard --install-daemon

# Arranca el Gateway manualmente (si prefieres)
openclaw gateway --port 18789 --verbose

# Envia un mensaje
openclaw message send --to +1234567890 --message "Hola desde GarraAbierta"

# Habla con el asistente (opcionalmente entrega la respuesta a cualquier canal conectado)
openclaw agent --message "Lista de pendientes" --thinking high
```

Actualizando? Consulta la [guia de actualizacion](https://docs.openclaw.ai/install/updating) (y ejecuta `openclaw doctor`).

## Funcionalidades principales

- **[Gateway local](https://docs.openclaw.ai/gateway)** — plano de control unico para sesiones, canales, herramientas y eventos.
- **[Bandeja multi-canal](https://docs.openclaw.ai/channels)** — WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, iMessage, Microsoft Teams, WebChat y mas.
- **[Enrutamiento multi-agente](https://docs.openclaw.ai/gateway/configuration)** — dirige canales, cuentas o contactos a agentes aislados.
- **[Voice Wake + Talk Mode](https://docs.openclaw.ai/nodes/voicewake)** — voz siempre activa en macOS/iOS/Android con ElevenLabs.
- **[Canvas en vivo](https://docs.openclaw.ai/platforms/mac/canvas)** — espacio de trabajo visual controlado por el agente.
- **[Herramientas integradas](https://docs.openclaw.ai/tools)** — navegador, canvas, nodos, cron, sesiones y acciones de Discord/Slack.
- **[Apps complementarias](https://docs.openclaw.ai/platforms/macos)** — app de barra de menu en macOS + nodos iOS/Android.

## Que traduce este fork?

El alcance de GarraAbierta se centra en tres pilares:

### 1. Documentacion traducida al espanol

Toda la documentacion del directorio `docs/` se traduce al espanol. Esto incluye guias de instalacion, configuracion, canales, herramientas y referencia. El objetivo es que puedas leer y entender todo sin necesidad de saber ingles.

### 2. Pipeline automatizado de sincronizacion mensual

Cada mes, un flujo de GitHub Actions:
1. Trae los cambios mas recientes de `openclaw/openclaw` (upstream).
2. Hace merge con nuestra rama principal.
3. Detecta documentos nuevos o modificados.
4. Los traduce automaticamente al espanol.
5. Crea un PR para revision humana antes de fusionar.

Esto garantiza que GarraAbierta se mantenga al dia con el proyecto original sin esfuerzo manual constante.

### 3. Traduccion guiada por glosario

Usamos un archivo de glosario (`docs/.i18n/glossary.es.json`) que asegura consistencia en la terminologia tecnica. Algunos terminos se mantienen en ingles (como "Gateway" o "Canvas") cuando no existe una traduccion natural, mientras que otros se traducen de forma estandarizada.

## Como contribuir

Consulta [CONTRIBUIR.md](CONTRIBUIR.md) para instrucciones detalladas.

Si hablas espanol, hay varias formas en que puedes ayudar:

- **Revisar traducciones existentes** — encontrar frases que suenen raras o poco naturales.
- **Reportar errores de traduccion** — abrir un issue cuando algo este mal traducido.
- **Sugerir mejoras al glosario** — proponer mejores traducciones para terminos tecnicos.
- **Agregar documentacion nueva** — escribir guias o tutoriales en espanol que complementen las existentes.

Toda contribucion es bienvenida, sin importar tu nivel de experiencia.

## Sincronizacion con upstream

GarraAbierta se sincroniza automaticamente con el repositorio original de OpenClaw mediante un proceso mensual:

```
openclaw/openclaw (upstream)
        |
        v
  GitHub Actions (cron mensual)
        |
        ├── git fetch upstream
        ├── git merge upstream/main
        ├── detectar docs nuevos/modificados
        ├── traducir con IA + glosario
        └── crear PR para revision
        |
        v
  ConejoCapital/GarraAbierta (fork)
```

Este proceso esta automatizado, pero cada PR de traduccion pasa por revision humana antes de fusionarse. Si encuentras problemas con una sincronizacion, abre un issue.

## Compilacion desde el codigo fuente

Si quieres desarrollar o contribuir al codigo:

```bash
git clone https://github.com/ConejoCapital/GarraAbierta.git
cd GarraAbierta

pnpm install
pnpm ui:build
pnpm build

pnpm openclaw onboard --install-daemon
```

## Seguridad

OpenClaw se conecta a plataformas de mensajeria reales. Trata los mensajes directos entrantes como **entrada no confiable**.

Guia completa de seguridad: [Security](https://docs.openclaw.ai/gateway/security)

## Links

| Recurso | Enlace |
|---------|--------|
| Documentacion | [docs.openclaw.ai](https://docs.openclaw.ai) |
| Discord | [discord.gg/clawd](https://discord.gg/clawd) |
| Repositorio original | [openclaw/openclaw](https://github.com/openclaw/openclaw) |
| Guia de contribucion | [CONTRIBUIR.md](CONTRIBUIR.md) |
| Licencia | [MIT](LICENSE) |
| Issue de contexto del fork | [#3460](https://github.com/openclaw/openclaw/issues/3460) |

---

<p align="center">
  Hecho con cariño para la comunidad hispanohablante por <a href="https://github.com/ConejoCapital">ConejoCapital</a>.
  <br>
  Todo el codigo original pertenece al equipo de <a href="https://github.com/openclaw/openclaw">OpenClaw</a>.
</p>

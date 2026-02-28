---
summary: "Instala OpenClaw y ejecuta tu primer chat en minutos."
read_when:
  - First time setup from zero
  - You want the fastest path to a working chat
title: "Primeros pasos"
---

# Primeros pasos

Objetivo: ir de cero a un primer chat funcional con la mínima configuración.

<Info>
Chat más rápido: abre la interfaz Control (no necesitas configurar ningún canal). Ejecuta `openclaw dashboard`
y chatea en el navegador, o abre `http://127.0.0.1:18789/` en el
<Tooltip headline="Host del Gateway" tip="La máquina que ejecuta el servicio gateway de OpenClaw.">host del Gateway</Tooltip>.
Docs: [Panel](/web/dashboard) y [Interfaz Control](/web/control-ui).
</Info>

## Requisitos previos

- Node 22 o superior

<Tip>
Verifica tu versión de Node con `node --version` si no estás seguro.
</Tip>

## Configuración rápida (CLI)

<Steps>
  <Step title="Instala OpenClaw (recomendado)">
    <Tabs>
      <Tab title="macOS/Linux">
        ```bash
        curl -fsSL https://openclaw.ai/install.sh | bash
        ```
        <img
  src="/assets/install-script.svg"
  alt="Proceso del script de instalación"
  className="rounded-lg"
/>
      </Tab>
      <Tab title="Windows (PowerShell)">
        ```powershell
        iwr -useb https://openclaw.ai/install.ps1 | iex
        ```
      </Tab>
    </Tabs>

    <Note>
    Otros métodos de instalación y requisitos: [Instalar](/es/install).
    </Note>

  </Step>
  <Step title="Ejecuta el asistente de configuración">
    ```bash
    openclaw onboard --install-daemon
    ```

    El asistente configura la autenticación, los ajustes del gateway y los canales opcionales.
    Consulta [Asistente de configuración](/es/start/wizard) para más detalles.

  </Step>
  <Step title="Verifica el Gateway">
    Si instalaste el servicio, ya debería estar ejecutándose:

    ```bash
    openclaw gateway status
    ```

  </Step>
  <Step title="Abre la interfaz Control">
    ```bash
    openclaw dashboard
    ```
  </Step>
</Steps>

<Check>
Si la interfaz Control carga, tu Gateway está listo para usar.
</Check>

## Verificaciones opcionales y extras

<AccordionGroup>
  <Accordion title="Ejecutar el Gateway en primer plano">
    Útil para pruebas rápidas o solución de problemas.

    ```bash
    openclaw gateway --port 18789
    ```

  </Accordion>
  <Accordion title="Enviar un mensaje de prueba">
    Requiere un canal configurado.

    ```bash
    openclaw message send --target +15555550123 --message "Hola desde OpenClaw"
    ```

  </Accordion>
</AccordionGroup>

## Variables de entorno útiles

Si ejecutas OpenClaw como una cuenta de servicio o quieres ubicaciones personalizadas de configuración/estado:

- `OPENCLAW_HOME` establece el directorio base usado para la resolución interna de rutas.
- `OPENCLAW_STATE_DIR` sobrescribe el directorio de estado.
- `OPENCLAW_CONFIG_PATH` sobrescribe la ruta del archivo de configuración.

Referencia completa de variables de entorno: [Variables de entorno](/help/environment).

## Profundiza

<Columns>
  <Card title="Asistente de configuración (detalles)" href="/es/start/wizard">
    Referencia completa del asistente CLI y opciones avanzadas.
  </Card>
  <Card title="Configuración inicial en app macOS" href="/start/onboarding">
    Flujo de primera ejecución para la app de macOS.
  </Card>
</Columns>

## Lo que tendrás

- Un Gateway en ejecución
- Autenticación configurada
- Acceso a la interfaz Control o un canal conectado

## Próximos pasos

- Seguridad en mensajes directos y aprobaciones: [Emparejamiento](/channels/pairing)
- Conectar más canales: [Canales](/es/channels)
- Flujos avanzados y desde código fuente: [Configuración](/start/setup)

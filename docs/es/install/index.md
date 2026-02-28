---
summary: "Instalar OpenClaw — script de instalación, npm/pnpm, desde código fuente, Docker y más"
read_when:
  - You need an install method other than the Getting Started quickstart
  - You want to deploy to a cloud platform
  - You need to update, migrate, or uninstall
title: "Instalar"
---

# Instalar

¿Ya seguiste [Primeros pasos](/es/start/getting-started)? Entonces ya estás listo — esta página es para métodos alternativos de instalación, instrucciones específicas por plataforma y mantenimiento.

## Requisitos del sistema

- **[Node 22+](/install/node)** (el [script de instalación](#métodos-de-instalación) lo instalará si falta)
- macOS, Linux o Windows
- `pnpm` solo si compilas desde código fuente

<Note>
En Windows, recomendamos encarecidamente ejecutar OpenClaw bajo [WSL2](https://learn.microsoft.com/es-es/windows/wsl/install).
</Note>

## Métodos de instalación

<Tip>
El **script de instalación** es la forma recomendada de instalar OpenClaw. Se encarga de la detección de Node, la instalación y la configuración inicial en un solo paso.
</Tip>

<Warning>
Para VPS/hosts en la nube, evita las imágenes de "1-click" de terceros cuando sea posible. Prefiere una imagen base limpia del SO (por ejemplo Ubuntu LTS), luego instala OpenClaw tú mismo con el script de instalación.
</Warning>

<AccordionGroup>
  <Accordion title="Script de instalación" icon="rocket" defaultOpen>
    Descarga el CLI, lo instala globalmente vía npm y lanza el asistente de configuración.

    <Tabs>
      <Tab title="macOS / Linux / WSL2">
        ```bash
        curl -fsSL https://openclaw.ai/install.sh | bash
        ```
      </Tab>
      <Tab title="Windows (PowerShell)">
        ```powershell
        iwr -useb https://openclaw.ai/install.ps1 | iex
        ```
      </Tab>
    </Tabs>

    Eso es todo — el script se encarga de la detección de Node, la instalación y la configuración inicial.

    Para omitir la configuración inicial y solo instalar el binario:

    <Tabs>
      <Tab title="macOS / Linux / WSL2">
        ```bash
        curl -fsSL https://openclaw.ai/install.sh | bash -s -- --no-onboard
        ```
      </Tab>
      <Tab title="Windows (PowerShell)">
        ```powershell
        & ([scriptblock]::Create((iwr -useb https://openclaw.ai/install.ps1))) -NoOnboard
        ```
      </Tab>
    </Tabs>

    Para todas las flags, variables de entorno y opciones de CI/automatización, consulta [Internos del instalador](/install/installer).

  </Accordion>

  <Accordion title="npm / pnpm" icon="package">
    Si ya tienes Node 22+ y prefieres gestionar la instalación tú mismo:

    <Tabs>
      <Tab title="npm">
        ```bash
        npm install -g openclaw@latest
        openclaw onboard --install-daemon
        ```

        <Accordion title="¿Errores de compilación de sharp?">
          Si tienes libvips instalado globalmente (común en macOS vía Homebrew) y `sharp` falla, fuerza los binarios precompilados:

          ```bash
          SHARP_IGNORE_GLOBAL_LIBVIPS=1 npm install -g openclaw@latest
          ```

          Si ves `sharp: Please add node-gyp to your dependencies`, instala las herramientas de compilación (macOS: Xcode CLT + `npm install -g node-gyp`) o usa la variable de entorno anterior.
        </Accordion>
      </Tab>
      <Tab title="pnpm">
        ```bash
        pnpm add -g openclaw@latest
        pnpm approve-builds -g        # aprobar openclaw, node-llama-cpp, sharp, etc.
        openclaw onboard --install-daemon
        ```

        <Note>
        pnpm requiere aprobación explícita para paquetes con scripts de compilación. Después de que la primera instalación muestre la advertencia "Ignored build scripts", ejecuta `pnpm approve-builds -g` y selecciona los paquetes listados.
        </Note>
      </Tab>
    </Tabs>

  </Accordion>

  <Accordion title="Desde código fuente" icon="github">
    Para contribuidores o cualquiera que quiera ejecutar desde un checkout local.

    <Steps>
      <Step title="Clona y compila">
        Clona el [repositorio de OpenClaw](https://github.com/openclaw/openclaw) y compila:

        ```bash
        git clone https://github.com/openclaw/openclaw.git
        cd openclaw
        pnpm install
        pnpm ui:build
        pnpm build
        ```
      </Step>
      <Step title="Vincula el CLI">
        Haz que el comando `openclaw` esté disponible globalmente:

        ```bash
        pnpm link --global
        ```

        Alternativamente, omite el vínculo y ejecuta comandos con `pnpm openclaw ...` desde dentro del repositorio.
      </Step>
      <Step title="Ejecuta la configuración inicial">
        ```bash
        openclaw onboard --install-daemon
        ```
      </Step>
    </Steps>

    Para flujos de desarrollo más avanzados, consulta [Configuración](/start/setup).

  </Accordion>
</AccordionGroup>

## Otros métodos de instalación

<CardGroup cols={2}>
  <Card title="Docker" href="/install/docker" icon="container">
    Despliegues en contenedor o sin interfaz gráfica.
  </Card>
  <Card title="Podman" href="/install/podman" icon="container">
    Contenedor sin root: ejecuta `setup-podman.sh` una vez, luego el script de inicio.
  </Card>
  <Card title="Nix" href="/install/nix" icon="snowflake">
    Instalación declarativa vía Nix.
  </Card>
  <Card title="Ansible" href="/install/ansible" icon="server">
    Aprovisionamiento automatizado de flotas.
  </Card>
  <Card title="Bun" href="/install/bun" icon="zap">
    Uso solo CLI vía el runtime Bun.
  </Card>
</CardGroup>

## Después de instalar

Verifica que todo funciona:

```bash
openclaw doctor         # verifica problemas de configuración
openclaw status         # estado del gateway
openclaw dashboard      # abre la interfaz en el navegador
```

Si necesitas rutas de ejecución personalizadas, usa:

- `OPENCLAW_HOME` para rutas internas basadas en el directorio home
- `OPENCLAW_STATE_DIR` para la ubicación del estado mutable
- `OPENCLAW_CONFIG_PATH` para la ubicación del archivo de configuración

Consulta [Variables de entorno](/help/environment) para la precedencia y detalles completos.

## Solución de problemas: `openclaw` no encontrado

<Accordion title="Diagnóstico y solución de PATH">
  Diagnóstico rápido:

```bash
node -v
npm -v
npm prefix -g
echo "$PATH"
```

Si `$(npm prefix -g)/bin` (macOS/Linux) o `$(npm prefix -g)` (Windows) **no** está en tu `$PATH`, tu shell no puede encontrar los binarios globales de npm (incluyendo `openclaw`).

Solución — agrégalo a tu archivo de inicio de shell (`~/.zshrc` o `~/.bashrc`):

```bash
export PATH="$(npm prefix -g)/bin:$PATH"
```

En Windows, agrega la salida de `npm prefix -g` a tu PATH.

Luego abre una nueva terminal (o `rehash` en zsh / `hash -r` en bash).
</Accordion>

## Actualizar / desinstalar

<CardGroup cols={3}>
  <Card title="Actualizar" href="/install/updating" icon="refresh-cw">
    Mantén OpenClaw al día.
  </Card>
  <Card title="Migrar" href="/install/migrating" icon="arrow-right">
    Muévete a una nueva máquina.
  </Card>
  <Card title="Desinstalar" href="/install/uninstall" icon="trash-2">
    Elimina OpenClaw completamente.
  </Card>
</CardGroup>

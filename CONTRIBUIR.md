# Contribuir a GarraAbierta

Bienvenido al tanque de langostas en espanol. Nos alegra que quieras contribuir.

## Sobre este proyecto

GarraAbierta es un fork en espanol de [OpenClaw](https://github.com/openclaw/openclaw).
El objetivo es hacer accesible la documentacion, las guias y los recursos de OpenClaw
para la comunidad hispanohablante. No reemplazamos al proyecto original: lo
complementamos con traducciones para que mas personas puedan usarlo en su idioma.

- **Proyecto original:** [openclaw/openclaw](https://github.com/openclaw/openclaw)
- **Vision del proyecto:** [`VISION.md`](VISION.md)
- **Guia de contribucion original:** [`CONTRIBUTING.md`](CONTRIBUTING.md)

## Como contribuir traducciones

1. Haz un fork de este repositorio.
2. Busca archivos sin traducir en `docs/es/`. Compara con `docs/` para
   encontrar los que todavia faltan.
3. Consulta el glosario en `docs/.i18n/glossary.es.json` antes de empezar.
4. Crea tu traduccion siguiendo la guia de estilo (ver abajo).
5. Abre un Pull Request con tus cambios.

Si es tu primera traduccion, empieza con un archivo corto para familiarizarte
con el proceso. No hace falta traducir todo de una vez.

## Guia de estilo para traducciones

### Tono y registro

- Usa el tuteo informal ("tu"), no "usted".
- Escribe de forma clara y directa, como si le explicaras algo a un colega.
- Evita lenguaje excesivamente formal o academico.

### Terminos tecnicos

Manten en ingles los terminos tecnicos que son universales y que la comunidad
hispana ya usa en ingles:

- sandbox, webhook, middleware, token, prompt
- CLI, daemon, runtime, endpoint, payload
- plugin, hook, cron, gateway, proxy
- build, deploy, commit, push, pull, merge, rebase

Si no estas seguro de si traducir un termino, consulta el glosario. Si el
termino no aparece ahi, dejalo en ingles y mencionalo en tu PR.

### Nombres de producto

Siempre en ingles, sin traducir: OpenClaw, GarraAbierta, Pi, Gateway, Skills,
WhatsApp, Telegram, Discord, Signal, Slack, ClawHub, Lobster, Peekaboo.

### Formato y estructura

- Preserva la estructura Markdown exactamente como esta en el original.
- Manten los mismos encabezados, listas, tablas y enlaces.
- No cambies el nivel de los encabezados ni reorganices secciones.

### Que NO traducir

- Bloques de codigo (` ``` `)
- Flags y opciones de CLI (`--verbose`, `--port`, etc.)
- Variables de entorno (`OPENCLAW_TEST_PROFILE`, etc.)
- URLs, rutas de archivos, nombres de archivos y directorios
- Identificadores de configuracion (claves JSON, YAML, etc.)

### Consistencia

- Consulta siempre el glosario en `docs/.i18n/glossary.es.json` antes de traducir.
- Si ves una inconsistencia con otra traduccion existente, abre un issue.
- Revisa las traducciones existentes en `docs/es/` para mantener un estilo uniforme.

## Como reportar errores de traduccion

Abre un issue con la etiqueta `traduccion` e incluye:

- **Ruta del archivo:** por ejemplo, `docs/es/configuration.md`
- **Seccion afectada:** el encabezado o numero de linea
- **Texto actual:** lo que dice ahora
- **Correccion sugerida:** lo que deberia decir

O, si la correccion es clara, envia un PR directamente con el arreglo.

## Como agregar nuevas traducciones

Revisa los archivos en `docs/` que no tienen version correspondiente en
`docs/es/`. Esos son los que necesitan traduccion.

### Traduccion automatizada

Puedes usar la herramienta de traduccion del proyecto:

```bash
cd scripts/docs-i18n
go build -o docs-i18n .
./docs-i18n -lang es -src en -docs ../../docs -mode doc -thinking high -max 5
```

Esto genera una traduccion inicial que despues debes revisar y ajustar
manualmente. No la uses como traduccion final sin revision.

### Traduccion manual

1. Copia el archivo en ingles a `docs/es/` con el mismo nombre.
2. Traduce el contenido siguiendo la guia de estilo.
3. Revisa que los enlaces y bloques de codigo sigan funcionando.
4. Abre un PR con tu traduccion.

### En tu Pull Request

- Describe que archivo(s) tradujiste.
- Indica si usaste la herramienta automatizada, traduccion manual, o ambas.
- Si hay terminos que no estaban en el glosario y tuviste que decidir como
  traducirlos, mencionalo para que lo discutamos.

## Proceso de revision

- Todos los PRs de traduccion son revisados por al menos un hablante nativo
  de espanol.
- Se ejecutan verificaciones automatizadas de formato Markdown y consistencia
  con el glosario.
- El tiempo tipico de revision es de 1 a 2 semanas. Ten paciencia; todos
  contribuimos en nuestro tiempo libre.
- Si tu PR necesita cambios, te dejaremos comentarios constructivos. No te
  desanimes: las revisiones son para mejorar el resultado, no para criticar.

## Codigo de conducta

- Se amable y respetuoso con los demas contribuidores.
- Los comentarios sobre traducciones deben ser constructivos: explica por que
  sugieres un cambio, no solo que esta "mal".
- Recuerda: una traduccion buena es mejor que ninguna traduccion. Podemos
  iterar y mejorar con el tiempo.
- Valoramos la diversidad del espanol: hay muchas variantes regionales validas.
  Apuntamos a un espanol neutro cuando sea posible, pero no rechazamos
  contribuciones por regionalismos razonables.

## Recursos utiles

- **Glosario:** [`docs/.i18n/glossary.es.json`](docs/.i18n/glossary.es.json)
- **Documentacion original:** [`docs/`](docs/)
- **Traducciones existentes:** [`docs/es/`](docs/es/)
- **Herramienta de i18n:** [`scripts/docs-i18n/`](scripts/docs-i18n/)
- **Info sobre el sistema i18n:** [`docs/.i18n/README.md`](docs/.i18n/README.md)

---

Gracias por contribuir a GarraAbierta. Cada traduccion, por pequena que sea,
ayuda a que mas personas puedan usar OpenClaw en espanol.

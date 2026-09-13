# don-cron-site

Sitio público estático de **Don Cron** (`don-cron.com`): home del canal y los
textos legales (Términos de Servicio y Política de Privacidad) exigidos para
registrar **Don Cron Publish** — la app interna de línea de comandos que
publica los videos del canal en YouTube y TikTok — ante TikTok for Developers
y, eventualmente, ante la verificación de apps OAuth de Google.

## Stack

HTML + CSS puro. Sin frameworks, sin build, sin JavaScript, sin dependencias
externas salvo Google Fonts (Space Grotesk + Inter) vía `<link>`.

## Estructura

```
index.html          Home
terminos/index.html Términos de Servicio (app + sitio)
privacidad/index.html Política de Privacidad (app + sitio)
404.html             Página de error
styles.css           Estilos compartidos
CNAME                Dominio custom para GitHub Pages
.nojekyll             Desactiva el procesamiento Jekyll de Pages
```

## Deploy

Se despliega con **GitHub Pages**, sirviendo desde la rama `main`, raíz del
repo (`/`). El archivo `CNAME` apunta el sitio a `don-cron.com`.

## Home

La home (`index.html`) incluye una sección **"Últimos videos"** (`#videos`)
con los Shorts más recientes del canal, embebidos con iframes de
`youtube-nocookie.com` (modo de privacidad mejorada). Se muestran como un
**carrusel horizontal** (`.video-carousel`, CSS `scroll-snap`, sin
JavaScript) para que la sección no crezca en altura a medida que se suman
videos.

Reglas de la lista (a mano, directamente en el markup de `index.html`):

- **Orden: el más nuevo primero.** El video publicado más recientemente va
  primero en el carrusel.
- **Tope de 8 tarjetas.** Al agregar la 9ª, hay que sacar la última (la más
  vieja) para no acumular videos indefinidamente. Hay un comentario HTML en
  `index.html`, justo arriba de la lista, que recuerda esta regla.
- Para agregar o quitar un video hay que editar esa sección (y, si
  corresponde, la versión en inglés) a mano. No hay generación automática ni
  feed dinámico.

## Alcance legal

Los textos de `terminos/` y `privacidad/` describen específicamente el uso de
**Don Cron Publish**: una herramienta interna usada únicamente por el titular
del canal (Lucas Cristaldo) para publicar sus propios videos en sus propias
cuentas de YouTube (Data API v3) y TikTok (Content Posting API). No hay
usuarios de terceros, cuentas de terceros ni recolección de datos de
visitantes del sitio.

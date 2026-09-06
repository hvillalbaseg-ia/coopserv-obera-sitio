# Sitio de práctica CoopServ Oberá Ltda. — instrucciones de publicación

Este paquete tiene el sitio estático completo (4 páginas + 2 PDF con metadatos ya sembrados)
para publicarlo en GitHub Pages y usarlo como objetivo autorizado del laboratorio de la Clase 5.

## 1. Por qué no uses No-IP para esto

No-IP (plan gratuito) sirve para apuntar un hostname a la IP de TU PROPIA máquina, no para
manejarlo como un dominio de propósito general — no da CNAME libre hacia `github.io`, hay que
reconfirmar el hostname cada 30 días o se borra, y los dominios `.ddns.net`/`.hopto.org` están
asociados en la mayoría de las bases de inteligencia de amenazas a infraestructura de malware
(C2 de botnets), lo cual es un poco irónico para el sitio de una cooperativa "legítima". No te lo
recomiendo para este uso.

## 2. Alternativa real y gratuita: is-a.dev

[is-a.dev](https://is-a.dev) es un servicio gratuito y con buena reputación (miles de
colaboradores, respaldado por Cloudflare) que delega subdominios reales — con soporte de
registros A, CNAME, MX y TXT — mediante un pull request en GitHub. Es justo lo que necesitás:
un dominio real (no un acortador ni un túnel), gratis, sin vencimiento mensual.

**Pasos (seguí la documentación oficial para el formato exacto del archivo, que puede cambiar):**

1. Creá el repositorio de GitHub Pages con este sitio (paso 3 más abajo) **antes** de pedir el
   subdominio.
2. Andá a `https://github.com/is-a-dev/register`, hacé fork, y seguí su documentación
   (`docs.is-a.dev`) para crear `domains/coopserv-obera.json` — ahí vas a declarar tu usuario de
   GitHub y un registro `CNAME` apuntando a `tu-usuario.github.io`. **No dejes que una IA te
   genere ese archivo a ciegas** — es literalmente la advertencia que pone el propio proyecto en
   su documentación, porque el esquema exacto puede cambiar y un archivo mal armado retrasa la
   aprobación. Copialo de un ejemplo real de su documentación.
3. Abrí el pull request y esperá la revisión (es manual — no lo dejes para el día antes de la
   clase, puede tardar).
4. Una vez mergeado (y con hasta 24 h de propagación), andá a tu repositorio → *Settings* →
   *Pages* → *Custom domain* → escribí `coopserv-obera.is-a.dev` → activá *Enforce HTTPS*.

Si preferís un nombre distinto a `coopserv-obera`, hacé buscar-y-reemplazar de
"coopserv-obera.is-a.dev" en `contacto.html` antes de publicar.

## 3. Publicar el sitio en GitHub Pages

1. Creá un repositorio nuevo en GitHub (público — GitHub Pages gratuito requiere repos públicos,
   salvo que tengas GitHub Pro/Team).
2. Subí todo el contenido de esta carpeta a la raíz del repositorio (incluida la subcarpeta
   `docs/` con los dos PDF — ojo, no la confundas con la carpeta especial `/docs` que usa GitHub
   Pages como *source*; si vas a servir el sitio desde `/docs` como origen, renombrá esta carpeta
   de PDFs a algo como `archivos/` para no pisarla).
3. *Settings* → *Pages* → *Build and deployment* → *Deploy from a branch* → rama `main`, carpeta
   `/ (root)` (o `/docs` si renombraste como se indica arriba).
4. Esperá unos minutos y verificá que `https://tu-usuario.github.io/tu-repo/` cargue antes de
   seguir con el paso del dominio custom.

## 4. Qué vas a poder verificar antes de la clase

- `dig coopserv-obera.is-a.dev` — debería resolver al CNAME de GitHub Pages.
- Buscar `coopserv-obera.is-a.dev` en https://crt.sh/ — debería aparecer el certificado una vez
  que GitHub emite el TLS (puede tardar un rato después de activar *Enforce HTTPS*).
- `whois coopserv-obera.is-a.dev` — va a mostrar que el dominio padre es `is-a.dev`, no un
  registro propio. Esto **no es un problema** — es en sí mismo un hallazgo válido de OSINT que
  podés comentar en la puesta en común: a veces la organización investigada no tiene dominio
  propio, sino que usa un subdominio de un tercero, y eso también dice algo.

## 5. Contenido de este paquete

- `index.html`, `quienes-somos.html`, `contacto.html`, `novedades.html` — el sitio.
- `estilos.css` — estilos compartidos.
- `docs/memoria-institucional-2025.pdf` y `docs/reglamento-interno-resumen.pdf` — con metadatos
  ya sembrados (`Author`, `Producer: LibreOffice 7.6`) para la Fase 3 del laboratorio
  (metadatos de documentos).

No hace falta que hagas nada más en los PDF — ya están listos para subir tal cual.

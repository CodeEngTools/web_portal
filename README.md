# CodeEngTools — Web Portal

Landing profesional bilingue (ES/EN) de **CodeEngTools** — Miguel del Pino, Infrastructure & Automation Engineer / SRE.

Sitio estatico de una sola pagina, sin build ni dependencias. Se despliega en **Cloudflare Pages** conectado a este repo de GitHub.

## Estructura

    web_portal/
    |- public/            # Directorio publicado (output de Cloudflare Pages)
    |  |- index.html      # La landing (todo el CSS/JS va inline)
    |  |- favicon.svg
    |  |- _headers        # Cabeceras de seguridad (CSP, HSTS, etc.)
    |  |- robots.txt
    |  |- sitemap.xml
    |- README.md
    |- .gitignore

## Despliegue en Cloudflare Pages (Git)

En **Workers & Pages -> Create -> Pages -> Connect to Git**, elige `CodeEngTools/web_portal` y configura:

| Ajuste | Valor |
|---|---|
| Framework preset | None |
| Build command | *(vacio)* |
| Build output directory | `public` |
| Production branch | `main` |

Cada push a `main` despliega automaticamente. No hay paso de build: Cloudflare publica el contenido de `public/` tal cual.

## Dominio

Dominio: **codeengtools.eu** (DNS en Cloudflare). En el proyecto de Pages -> *Custom domains* se anaden `codeengtools.eu` y `www.codeengtools.eu`. El resto de registros DNS (correo `serviciodecorreo.es` y tuneles) no se tocan. El canonico www->apex lo cubre la etiqueta `<link rel="canonical">` del HTML.

## Editar

Todo el contenido (textos ES/EN, servicios, caso Total Logistic, contacto) esta en `public/index.html`. El selector de idioma usa las clases `.lang-es` / `.lang-en` y un boton que alterna `body.en`.

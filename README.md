# Técnicos UY

Landing de una sola página de **Técnicos UY** — soporte IT, Microsoft 365, ciberseguridad y
automatización en remoto para pymes de Uruguay y LATAM, por **Juan Rodríguez** (14 años en IT
enterprise, Intel / SAP).

🔗 **En vivo:** [tecnicosuy.com.uy](https://tecnicosuy.com.uy/)

La web funciona como **capa de credibilidad**: convierte a quien llega desde propuestas de
Workana/Upwork, LinkedIn y WhatsApp, priorizando confianza, claridad y un CTA directo a WhatsApp.

## Stack

HTML / CSS / JS **estático y self-contained**. Sin frameworks, sin build, sin dependencias de
instalación. Única dependencia externa: Google Fonts (Sora, Inter, JetBrains Mono). Se despliega
en **GitHub Pages** con dominio propio.

## Estructura

```
index.html      Landing completa (CSS en <style>, JS en <script>)
og-image.png    Imagen social 1200×630
CNAME           Dominio personalizado: tecnicosuy.com.uy
robots.txt      Reglas para crawlers + sitemap
sitemap.xml     Mapa del sitio (una URL)
```

## Editar los datos de contacto (bloque CFG)

Todo lo configurable vive en un único objeto `CFG`, al inicio del `<script>` casi al final de
[`index.html`](index.html):

```js
const CFG = {
  whatsapp: "59899000000",                 // número con código de país, sin + ni espacios
  email:    "hola@tecnicosuy.com.uy",      // email de contacto
  linkedin: "https://www.linkedin.com/in/juandresrodriguez",
  waMessage:"Hola Juan, vi tu web Técnicos UY y quería consultarte por", // mensaje pre-cargado
  location: "Disponible en remoto · Respuesta el mismo día hábil"        // línea bajo el CTA
};
```

| Campo | Qué hace |
|---|---|
| `whatsapp` | Genera el link `wa.me`. Solo dígitos, con código de país (Uruguay = `598`), **sin `+` ni espacios**. |
| `email` | Usado en los botones "Enviar email" (`mailto:` con asunto pre-cargado). |
| `linkedin` | URL del perfil; alimenta el link del footer. |
| `waMessage` | Texto que aparece ya escrito al abrir WhatsApp. |
| `location` | Línea de texto que se muestra debajo del CTA de contacto. |

Editás esos valores, guardás y listo — el JS cablea automáticamente botones, footer y año.

**Proyectos mostrados:** se listan desde el array `PROJECTS` en el mismo `<script>`. Para
agregar/quitar uno, editá ese array (`name`, `lang`, `desc`, `url`).

## Previsualizar en local

Es estático, así que basta con abrir el archivo o levantar un server simple:

```bash
# Opción 1: abrir directo
start index.html        # Windows

# Opción 2: server local (recomendado, evita restricciones de file://)
python -m http.server 8000
# luego abrir http://localhost:8000
```

## Deploy (GitHub Pages + dominio propio)

El sitio se sirve desde la raíz del branch **`main`**.

1. Hacé tus cambios y commiteá.
2. `git push origin main`.
3. En **GitHub → Settings → Pages**, source = `Deploy from a branch`, branch = `main` / `/ (root)`.
4. El archivo [`CNAME`](CNAME) fija el dominio `tecnicosuy.com.uy`. **No lo borres ni lo
   renombres** — GitHub lo lee de la raíz. En el registrador del dominio, apuntá los DNS a
   GitHub Pages (registros `A` a las IPs de GitHub + `CNAME` de `www` a `juandresrodca.github.io`).
5. Cada push a `main` redeploya automáticamente.

> Si cambiás contenido relevante para SEO, actualizá `lastmod` en [`sitemap.xml`](sitemap.xml).

## Sistema de diseño

- **Fondo** teal profundo `#08131A`; **superficie** `#0F212C`; **líneas** `#1C3744`
- **Acento** celeste `#45C7E0` (interactivo) + **sol de mayo** dorado `#F4B740` (uso mínimo)
- **Texto** `#EAF3F4`; **muted** `#8FA9B1`
- **Tipografías**: Sora (display), Inter (cuerpo), JetBrains Mono (labels)
- **Marca**: ícono sol de mayo; **"UY" siempre en celeste**

---

© Técnicos UY · Juan Rodríguez

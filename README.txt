LabsMKT one page
================

Adaptación del proyecto base a https://labsmkt.com/.

Cambios principales:
- Marca actualizada a LabsMKT.
- Nuevo logotipo e isotipo SVG en /images/labsmkt-logo.svg y /images/labsmkt-icon.svg.
- Home convertido en one page.
- Eliminada la carpeta /servicios/ y todas sus páginas internas.
- Los 13 servicios aparecen ahora en la sección #servicios del inicio.
- Navegación principal por anclas: Inicio, Servicios, Método, Nosotros y Contacto.
- Formulario /api/contacto actualizado con la marca LabsMKT.
- Chat n8n mantiene el webhook del proyecto base y metadata LabsMKT.
- Sitemap actualizado para labsmkt.com.
- Política de privacidad y aviso legal se conservan como páginas legales auxiliares.

REVISIÓN ADICIONAL (esta pasada):
- BUG REAL — GA cruzado: aviso-legal.html y politica-privacidad.html
  tenían el código de Google Analytics de OTRO repositorio de la
  familia (G-JCR17PJG1D, de Trans4you), probablemente heredado al
  copiar la plantilla de páginas legales sin actualizar el ID.
  Corregido a G-F3P6F245YS (el código propio de LabsMKT) en ambas
  páginas. Revisado el resto del contenido de esas dos páginas
  (título, canonical, banner de cookies) y no se encontró más
  contaminación cruzada.
- Google Analytics: no existía en index.html. Añadido G-F3P6F245YS.
- BUG REAL — chat sin posicionar: no existía ninguna regla CSS para
  #n8n-chat .chat-window-toggle/.chat-window, así que el widget se
  mostraba en su posición por defecto del CDN, sin borde y
  potencialmente solapado con el botón flotante de WhatsApp. Añadida
  la posición estándar de la familia (chat por encima del WhatsApp,
  con borde blanco), en escritorio y móvil.
- Banner de cookies: index.html no lo tenía (las páginas legales sí);
  añadido con el mismo patrón ya usado en aviso-legal.html y
  politica-privacidad.html.
- Schema.org: ya existía AdvertisingAgency; añadido también FAQPage
  (el contenido de la sección FAQ ya existía en la página, pero sin
  marcado estructurado).
- package.json: el "name" seguía siendo "001web-web", heredado de la
  plantilla base (001web). Corregido a "labsmkt-onepage".
- No aplica middleware.mjs: aunque el proyecto base (001web) tenía
  páginas /servicios/, este dominio (labsmkt.com) es nuevo y nunca
  llegó a publicarse con esa estructura multipágina, así que no hay
  URLs antiguas indexadas que redirigir.
- H1 de portada ya cumplía el estilo de la familia (afirmativo, corto,
  sin interrogación); no se ha tocado.
- Dominio, teléfono/WhatsApp y dirección ya eran correctos y propios
  de LabsMKT; no se han modificado.

REVISIÓN ADICIONAL — BUG REAL (a petición del cliente):
- El botón flotante de WhatsApp (.float-wa) mostraba el texto "WA" en
  vez del icono SVG estándar de WhatsApp usado en el resto de la
  familia (mismo bug encontrado en AsusTech). Sustituido por el SVG
  correcto.

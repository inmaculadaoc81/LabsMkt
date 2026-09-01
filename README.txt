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

REVISIÓN ADICIONAL (a petición del cliente):
- Añadido "Sábados, domingos y días festivos estamos cerrados" debajo
  del horario en la tarjeta de información del hero.
- BUG REAL — no existía ningún botón/enlace de llamada en toda la
  web (el README anterior decía "teléfono/WhatsApp... ya eran
  correctos", pero solo había WhatsApp). Añadido el teléfono
  compartido de la familia, +34 914 46 85 03: fila "📞 Teléfono" en la
  tarjeta de información del hero, enlace en la sección de contacto
  (junto a WhatsApp y Email) y campo "telephone" en el schema.org
  (antes ausente).
- BUG REAL — las dos páginas legales (politica-privacidad.html y
  aviso-legal.html) afirmaban explícitamente "No ofrecemos atención
  telefónica directa" / "sin ofrecer atención telefónica directa",
  contenido que ya era falso incluso antes de este cambio si se
  considera el WhatsApp, y que ahora contradice directamente el nuevo
  teléfono añadido. Corregido el texto en ambas páginas, y añadido el
  teléfono también a su bloque de información del footer.
- BUG REAL — la casilla de política de privacidad del formulario
  enlazaba a la página legal local del propio repositorio
  (/politica-privacidad.html), que por su contenido HTML (clases
  ow-brand/ow-nav-wa/ow-footer-bottom, heredadas de la plantilla base
  "001web") parece no haberse rebrandeado del todo. Corregido al
  enlace estándar de la familia, https://kelatos.com/privacy-policy/,
  resaltado en azul.
- BUG REAL — las dos páginas legales referenciaban una imagen
  og:image inexistente (/images/og-001web.jpg, un archivo que nunca
  existió en /images/ y que además llevaba el nombre de la plantilla
  base, no de LabsMKT). Eliminada esa etiqueta meta rota en ambas
  páginas (index.html tampoco declara ninguna, así que queda
  coherente con el resto del sitio en vez de inventar una imagen que
  no existe).
- BUG REAL (a petición del cliente, "no tiene para agendar citas") —
  no existía ninguna sección de Cal.com en todo el sitio (a diferencia
  del resto de la familia). Añadida sección "Si prefieres dejarlo
  agendado" (id="cita") justo antes de la sección de contacto, con el
  mismo iframe compartido de la familia
  (https://cal.com/kelatos/30min?embed=true&theme=light), altura
  720px en escritorio y 760px en móvil. Añadido enlace "Pedir cita" al
  menú de navegación (el mismo <nav id="nav"> se usa para escritorio y
  móvil en esta plantilla).
- NO IDENTIFICADO — el cliente mencionó "en la imagen se señalan los
  botones que derivan a 001web, no los coloques", pero la imagen no
  llegó adjunta a este mensaje. Revisado todo el repositorio en busca
  de enlaces reales a un dominio 001web: no se encontró ningún <a
  href> apuntando a él; solo quedaban los dos rastros de plantilla ya
  corregidos arriba (imagen og:image rota) y un archivo de imagen sin
  usar, images/agencia-001web.svg (huérfano, no referenciado desde
  ningún HTML/CSS/JS, se ha dejado sin tocar por si se usa en otro
  sitio). Pendiente de que el cliente reenvíe la captura para
  identificar los botones exactos si el problema persiste.

REVISIÓN ADICIONAL (checklist unificado de la familia, a petición del cliente — repo 47/48):
- Verificado: enlace de Cal.com ya actualizado con attendeePhoneNumber
  y overlayCalendar.
- Verificado: el correo soporte@kelatos.com no aparece visible.
- Verificado: el mensaje prellenado de WhatsApp ya usa "¡Hola
  LabsMKT!".
- Verificado: el menú móvil (.menu/#nav) ya se cerraba correctamente
  al pulsar un enlace, vía script.js.
- Verificado: sin iconos ni imágenes con proporciones fijas
  incorrectas.
- Verificado: el H1 en móvil ya está en 48px.
- Verificado: los botones (.btn) ya tenían border-radius:999px y
  estados hover propios en las dos variantes (primary/ghost). No
  requerían cambios.
- Verificado: sin patrón de franja de insignias bajo el H1 (familia
  Dyson); no aplica la reubicación.
- No aplica la franja de aviso de servicio técnico independiente:
  agencia de marketing digital, no reparación.
- Sin cambios de código en este repo: todos los puntos del checklist
  ya estaban aplicados.

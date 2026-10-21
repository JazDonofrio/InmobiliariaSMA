# InmobiliariaSMA

Demo funcional de una plataforma web + mini CRM para una inmobiliaria. Es una alternativa pensada para clientes que hoy usan 2clics: sitio público con buscador, panel de gestión con login, carga de fotos y videos, consultas, visitas y un asistente con IA.

Es un único archivo (`index.html`), sin dependencias ni build. Para verla, abrí `index.html` en el navegador.

## Qué incluye

**Sitio público**
- Buscador con pestañas Comprar / Alquilar / Temporario y filtros por tipo, zona, dormitorios, baños, moneda, rango de precio, cochera, mascotas y apto crédito. Búsqueda por código o palabra clave.
- Tarjetas con galería de fotos (flechas, puntos y swipe en el celular).
- Ficha de cada propiedad con galería, fotos y videos, datos y comodidades.
- Comparador de hasta 3 propiedades.
- Consulta por formulario y por WhatsApp.
- Agendar visita: el cliente elige día y horario libre.
- Secciones Nosotros, Contacto y tasaciones, y mapa de la oficina.
- Asistente virtual que responde con la información publicada.

**Panel de la inmobiliaria** (`#panel`, usuario `admin`, contraseña `demo`)
- Alta, edición, baja y cambio de estado de propiedades.
- Carga de fotos y videos: arrastrar y soltar, pegar con Ctrl+V, optimización automática, orden por arrastre y portada.
- Pestaña Consultas (CRM) con estados y acceso directo a WhatsApp.
- Pestaña Visitas con confirmación por WhatsApp.
- Datos de la inmobiliaria, horario de visitas e información extra para el asistente.

El acceso al panel no está enlazado desde el sitio público: se entra por `index.html#panel`.

## Limitaciones de la demo

- Los datos (propiedades, fotos, consultas, visitas) se guardan solo en el navegador (IndexedDB). No hay base de datos ni servidor.
- El login es simulado y no protege nada.
- El asistente usa IA solo cuando la página corre dentro de Claude; fuera de ahí responde con una búsqueda básica por palabras clave.
- El mapa es una ilustración; el botón "Cómo llegar" abre Google Maps con la dirección cargada.
- Los videos subidos se guardan en el navegador (límite de 40 MB por archivo en la demo).

## Camino a la versión real

- Front y panel: Next.js.
- Base de datos, login de empleados y almacenamiento de fotos y videos: Supabase (Postgres, Auth, Storage), con reglas RLS para que solo usuarios autorizados editen.
- Asistente: API de Claude, con el listado de propiedades disponibles como contexto.
- Mapa real (Google Maps o Leaflet) y mapa con todas las propiedades.
- Publicación en portales, importación desde Excel/CSV, roles de usuario y avisos automáticos por WhatsApp o mail.

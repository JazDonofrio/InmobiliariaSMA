# Maqueta de plataforma inmobiliaria

Maqueta funcional de un sitio web con CRM para una inmobiliaria de **San Martín de los Andes**. Sirve para ver y probar cómo funcionaría la plataforma antes de construir la versión definitiva.

Es un único archivo (`index.html`) más las fuentes en `fonts/`. No usa librerías ni necesita compilar: se abre en el navegador o se publica en cualquier hosting estático.

> Es una **maqueta de demostración**, no el sistema final: no tiene servidor ni base de datos, así que los datos no se comparten entre dispositivos (ver "Qué falta para la versión real").

## Qué se puede probar

**Sitio público**
- Buscador por operación (comprar, alquilar, temporario), tipo, zona, dormitorios, baños, moneda, precio, cochera, mascotas y apto crédito, y búsqueda por código o palabra clave.
- Listado con galería de fotos en cada tarjeta.
- Ficha de cada propiedad con galería, datos, comodidades y videos.
- Comparador de hasta 3 propiedades.
- Consulta por formulario o WhatsApp, y **agenda de visitas**: el cliente elige día y horario libre, presencial o virtual.
- Secciones Nosotros, Contacto y tasaciones, mapa de la oficina y política de privacidad.
- Asistente virtual que responde con la información publicada.

**Panel de gestión** (se entra agregando `#panel` a la dirección; las credenciales se entregan aparte)
- Alta, edición y baja de propiedades, con carga de fotos y videos (arrastrar y soltar, optimización automática, orden y portada).
- **Excel**: descargar todas las propiedades en un `.xlsx` y volver a importarlo después de editarlo (las filas con un código existente se actualizan y las nuevas se agregan).
- Consultas (CRM) y visitas, con estados y respuesta por WhatsApp.
- Agenda en calendario, con el recorrido del día, check-in del agente con ubicación y encuesta posterior al cliente.
- Informes para propietarios: vistas del aviso, visitas, comentarios (anónimos) y ofertas, listos para enviar por WhatsApp o imprimir.
- Datos de la inmobiliaria, horarios de visita e información para el asistente.

## Contenido de la maqueta

Las propiedades, los precios y las fotos son los publicados por la inmobiliaria en su sitio, y se usan con su autorización para esta maqueta. Las consultas, visitas, ofertas y estadísticas son datos de ejemplo inventados para mostrar cómo funcionan esas pantallas.

## Qué falta para la versión real

Hoy cada navegador guarda sus propios datos: lo que se carga en una computadora no se ve en otra. Para que la inmobiliaria cargue una propiedad y la vea cualquier persona, en cualquier dispositivo, hace falta:

- **Base de datos y login reales** (por ejemplo Supabase: Postgres, Auth y Storage), con reglas que permitan a todos leer las propiedades publicadas y solo a la inmobiliaria crearlas o editarlas.
- **Almacenamiento de fotos en la nube**, en lugar de guardarlas en el navegador.
- **Actualización en vivo**: al marcar una propiedad como reservada, se ve al instante en todos los dispositivos, y dos personas no pueden tomar el mismo horario de visita.
- **Copias de seguridad** y roles (administrador y agentes).
- Mapa interactivo real (incluido un mapa con todas las propiedades), publicación en portales y avisos automáticos por WhatsApp o mail.

## Seguridad y datos personales

- Sin claves de API ni secretos en el código, y sin librerías de terceros.
- Fuentes alojadas en el propio sitio: no se envía la IP de los visitantes a servidores de Google.
- Todo dato cargado se escapa antes de mostrarse (prevención de XSS) y hay una política de seguridad de contenido (CSP) que bloquea scripts no autorizados y conexiones salientes. En Netlify se aplica como cabecera HTTP mediante `_headers`; en GitHub Pages, mediante `<meta>`.
- Los formularios piden consentimiento e incluyen la leyenda de la Ley 25.326, y los informes al propietario nunca muestran nombres ni contactos de los interesados.
- **A cargo de la inmobiliaria en la versión real:** inscribir la base de datos ante la AAIP, completar sus datos en la política de privacidad y mostrar su matrícula según la normativa vigente. Esto no es asesoramiento legal; conviene revisarlo con un profesional.

## Limitaciones conocidas

- El inicio de sesión del panel es demostrativo: cualquier control que corra en el navegador se puede saltear, así que no debe usarse con datos reales de clientes.
- El mapa de la oficina es una ilustración; "Cómo llegar" abre Google Maps.
- El check-in usa la ubicación solo cuando el agente toca el botón.
- La encuesta se envía abriendo WhatsApp con el mensaje escrito; el envío automático requiere la API de WhatsApp Business.
- El asistente usa IA solo cuando la página corre dentro de Claude; en otro lado responde con una búsqueda por palabras clave.
- El Excel no se actualiza solo: se descarga cuando se lo necesita.

## Publicación

- **GitHub Pages:** Settings > Pages > rama `main`, carpeta raíz.
- **Netlify:** arrastrar la carpeta. Toma automáticamente `_headers`.

Las fuentes Cormorant Garamond y Jost se distribuyen bajo licencia SIL OFL 1.1 (ver `fonts/OFL-*.txt`).

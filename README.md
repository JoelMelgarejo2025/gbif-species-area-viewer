# Explorador de especies

Prototipo web en español para buscar una dirección o lugar, seleccionar un radio y explorar taxones de GBIF en esa área.

## Funciones

- Mapa Leaflet como centro de la interfaz, con herramientas desplegables por iconos: búsqueda manual de direcciones, coordenadas, dibujo de polígonos y selección entre callejero y satélite. Incluye radio para las áreas creadas desde búsqueda o coordenadas y acciones Analizar, Borrar y Exportar dentro del mapa.
- Una sola consulta prepara ocho grupos taxonómicos: todos, plantas, mamíferos, aves, anfibios, reptiles, peces y insectos. Al cambiar de pestaña no se repite la consulta.
- Hasta ocho especies listadas por grupo. Entre las ocho más registradas evaluadas de cada grupo, se priorizan categorías globales IUCN CR, EN o VU cuando GBIF ofrece esa evaluación; las demás se ordenan por número de registros.
- Nombres comunes en español y sus fuentes, otros nombres vernáculos disponibles e imágenes de ocurrencias dentro del área, con atribución/licencia cuando GBIF las publica.
- Capa opcional de áreas protegidas a partir de servicios oficiales nacionales. El acceso depende de la disponibilidad y cobertura de cada servicio.
- CSV resumido por grupo. No contiene todos los registros individuales.

## Conservación y áreas protegidas

Las tarjetas usan 🔴 En peligro crítico (CR), 🟠 En peligro (EN) y 🟡 Vulnerable (VU), según la categoría global IUCN que GBIF tenga disponible. Si no hay una de esas categorías, se muestra solo el número de registros: la ausencia de símbolo no demuestra que una especie no esté amenazada.

El mapa abre en satélite con etiquetas y con la capa **Áreas** activada. Consulta servicios oficiales: SERNANP para Perú, RUNAP para Colombia, el Sistema Nacional de Áreas Protegidas de Ecuador y CNUC/MMA servido por IBAMA para Brasil. Se puede alternar al callejero y apagar la capa desde sus herramientas. Los servicios pueden cambiar, responder lentamente o tener escalas y fechas distintas. Si una fuente no responde, esa parte de la capa puede no mostrarse. La vista es una referencia y no sustituye la delimitación legal ni la cartografía oficial vigente.

## Cómo funciona y límites

La búsqueda de lugares se envía a Nominatim solo cuando el usuario pulsa **Buscar**; no se implementa autocompletado. Se limita a una petición por segundo y se mantiene atribución visible. Consulta la [política de uso de Nominatim](https://operations.osmfoundation.org/policies/nominatim/).

Las áreas dibujadas se consultan como polígonos; las direcciones y coordenadas usan el radio elegido. Las consultas de ocurrencias, taxonomía, nombres vernáculos, multimedia y categorías IUCN se hacen en vivo contra las API públicas de GBIF. Los conteos son **registros de ocurrencia**, no individuos ni abundancia. El visor muestra como máximo ocho especies por grupo; la prioridad IUCN se evalúa solo dentro de las ocho especies más registradas de cada grupo. No es una lista exhaustiva ni una descarga masiva. Una categoría IUCN ausente no significa que la especie esté fuera de peligro. Las categorías IUCN son globales y no equivalen a políticas locales de conservación.

El sitio es estático: no requiere backend, clave ArcGIS ni facturación de Google Cloud. Se usa Leaflet, OpenStreetMap para el callejero, World Imagery de Esri para satélite y el servicio de referencias de Esri para sus etiquetas; se conserva la atribución de cada proveedor. Las dependencias JavaScript se cargan desde un CDN.

## GitHub Pages

`.github/workflows/pages.yml` publica el sitio estático. En el repositorio hay que configurar **Settings → Pages → Build and deployment → GitHub Actions**. El workflow se ejecuta en cada actualización de `main`.

## APIs y atribuciones

- GBIF ocurrencias: <https://api.gbif.org/v1/occurrence/search>
- GBIF especies/nombres: <https://techdocs.gbif.org/en/openapi/v1/species>
- Nominatim: <https://operations.osmfoundation.org/policies/nominatim/>
- Mapa: © <https://www.openstreetmap.org/copyright>

## Licencia

El código de este prototipo se ofrece bajo MIT. Los datos e imágenes conservan sus licencias y condiciones de uso originales, según cada publicador en GBIF.

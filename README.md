# ROCC — Red de Observadores Climáticos Comunitarios

Herramienta para registrar y visualizar datos de pluviómetros reportados por una red
comunitaria (por ejemplo, un grupo de WhatsApp). Funciona en el navegador, sin instalar nada.

## Qué hace

- **Estaciones**: registro por número de teléfono (identificador único) con departamento,
  municipio, comunidad y coordenadas. Al cargar lluvia se autocompleta la ubicación.
- **Carga de lluvia**: manual o importando un Excel (`telefono`, `fecha`, `mm`).
- **Mapa**: lluvia por color por ubicación, con superficie interpolada (IDW) recortada a la
  red de estaciones para no extrapolar (recomendación de la OMM).
- **Periodos**: diario, semanal, mensual y anual (la lluvia se **suma** en el periodo).
- **Control de calidad**: rangos, negativos, duplicados y estaciones sin coordenadas.
- **Respaldo**: exporta/importa todo en `.json` y `.xlsx`.

> Los datos se guardan **solo en este navegador** (privados en este equipo, sin cuentas ni
> nube). Haz respaldos periódicos. Para cuentas y nube privada/compartida, ver más abajo.

## Uso rápido

1. Abre `index.html` en tu navegador (doble clic).
2. Pulsa **Cargar ejemplo** para ver cómo funciona, o empieza en **Estaciones**.
3. Ve a **Mapa** y elige el periodo.

## Publicar en GitHub Pages (gratis)

1. Crea una cuenta en <https://github.com> y un repositorio nuevo, por ejemplo `rocc`.
2. Sube el archivo `index.html` (botón **Add file → Upload files**) y confirma con **Commit**.
3. En el repo: **Settings → Pages**. En *Source* elige **Deploy from a branch**,
   rama `main` y carpeta `/root`. Guarda.
4. En 1–2 minutos tendrás una URL como `https://TU-USUARIO.github.io/rocc/`.

Cualquiera con el enlace puede **abrir la herramienta**, pero **los datos no se comparten**:
cada quien tiene los suyos en su propio navegador.

## Ampliación: cuentas de usuario y datos privados/compartidos

Para "crear perfil, guardar en la nube y que otros no lo vean salvo que compartas o publiques"
se necesita un backend. La ruta recomendada:

- **Supabase** (gratis para empezar): base de datos PostgreSQL + PostGIS, autenticación de
  usuarios y *Row Level Security* (permiso por fila) para lo privado/compartido/público.
- **Frontend**: este mismo `index.html` conectado a Supabase, o migrado a un proyecto React.
- **Geoestadística rigurosa (OMM)**: kriging ordinario con variograma, validación cruzada y
  mapa de incertidumbre, calculado en el servidor con Python (`pykrige`, `scipy`) o R (`gstat`).

La estructura de tablas y las políticas de acceso se describen en la conversación de entrega.

## Licencia

Uso libre. Ajusta según tus necesidades.

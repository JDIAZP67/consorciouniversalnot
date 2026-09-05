# CONSORCIO UNIVERSAL NOT — Sitio web

Página web corporativa de CONSORCIO UNIVERSAL NOT: catálogo de productos, formulas de cotización (lista de precios y maquila), área de distribuidores y panel administrativo protegido.

## Estructura

```
index.html      Página completa (público + panel admin)
css/estilos.css   Estilos
imagenes/         Fotos de productos y logo
```

## Publicación

Sitio estático publicado con **GitHub Pages** desde la rama `main` (raíz del repo), en el repositorio público **`consorciouniversalnot`**. Despliegue automático al hacer `git push`.

- URL: https://jdiazp67.github.io/consorciouniversalnot/
- Public directory: `/` (raíz del repo)

> Flujo: editas `index.html` → `git add -A` → `git commit -m "..."` → `git push`. En ~1 minuto GitHub Pages reconstruye y publica.

> Respaldo: el repo privado `consorcio-universal-not-web` queda asociado como remote `backup` (`git push backup main` para guardar una copia).

## Panel administrativo

- Se accede desde el botón flotante **⚙️** o "🔑 Administración" en el encabezado/pie.
- Permite gestionar **productos**, **categorías** y su visibilidad pública, con persistencia en el navegador (localStorage).
- Clave de acceso: `admin123` — **PROVISIONAL**.

> **Advertencia**: al ser una web estática, la contraseña está visible en el código fuente de la página y los datos viven solo en el navegador donde se editan. Mientras no haya base de datos, el panel es una solución de demo/maqueta.

## Próximo paso: Base de datos (pendiente)

Para producción real con datos compartidos y acceso seguro se planifica:

1. **Supabase** (Postgres + Auth + Storage) integrado con GitHub Pages.
2. Reemplazar la clave `admin123` por **login real** (Supabase Auth: correo + contraseña).
3. Mover las fotos a un **bucket de Storage** (hoy se guardan en base64 dentro del producto).
4. Activar **Row Level Security (RLS)**: lectura pública solo del catálogo; escritura únicamente con sesión de administrador.
5. Tablas iniciales: `productos`, `categorias`, `solicitudes` (leads/cotizaciones) — con semillas desde los productos y categorías actuales.
6. Guardar las claves en **Secretos** del repositorio, nunca en el código.
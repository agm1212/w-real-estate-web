# wrealestate.es

Web de W Real Estate. Se sirve con GitHub Pages desde la rama `main`: todo lo que se sube aquí queda publicado en https://wrealestate.es en uno o dos minutos.

## Lo primero: casi todo este repositorio se genera automáticamente

La mayor parte de las páginas **no se editan a mano**. Las produce un proceso de construcción que vive fuera de este repositorio y que se ejecuta cada vez que se publica el catálogo de propiedades. Ese proceso **borra y vuelve a crear** carpetas enteras. Si se edita algo dentro de ellas, se perderá en la siguiente publicación.

| Carpeta o archivo | Qué es | ¿Se puede editar? |
|---|---|---|
| `comprar/` y `en/` | Fichas de propiedad, listados, guías de municipio y toda la versión inglesa | **No. Se borran y regeneran enteras en cada publicación.** |
| `zonas/` | Guías de zona en español | No. Se regeneran. |
| `vender/`, `nosotros/`, `contacto/` | Copias de la portada arrancadas en esa sección | No. Se regeneran a partir de `index.html`. |
| `fichas/`, `fotos/` | Datos y fotos de las propiedades | No. Los escribe el catálogo. |
| `propiedades.json`, `paginas-*.json`, `sitemap*.xml`, `robots.txt`, `llms.txt` | Catálogo y SEO | No. Se regeneran. |
| `index.html` | La portada y toda la web principal (es una aplicación de una sola página) | Con cuidado: ver abajo. |
| `portal/` | Portal privado de agentes | Solo con acuerdo previo. |
| Cualquier carpeta nueva en la raíz | Landings y páginas sueltas | **Sí. Es el sitio para trabajar.** |

## Cómo crear una landing sin romper nada

1. Crea una **carpeta nueva en la raíz** con el nombre que tendrá la dirección, por ejemplo `promocion-x/` para `wrealestate.es/promocion-x/`.
2. Dentro, un `index.html` autocontenido. Puede llevar su propio CSS y JavaScript dentro de la carpeta.
3. Las imágenes van dentro de esa misma carpeta, o se referencian con **ruta absoluta** desde la raíz, por ejemplo `/w-logo-tinta.png`. Nunca con ruta relativa a otra carpeta: el proceso de construcción mueve páginas de sitio.
4. Si enlaza a otras páginas de la web, usa las direcciones públicas: `/comprar/`, `/zonas/`, `/contacto/`, `/en/buy/`. Los logos oficiales están en la raíz: `w-logo-tinta.png` (para fondo claro) y `w-logo-claro.png` (para fondo oscuro).
5. Comprueba que todos los enlaces internos existen. Antes de cada publicación se pasa un verificador que recorre todas las páginas, y **un enlace roto en una landing detiene la publicación de toda la web**.

Las landings no se incluyen en el `sitemap.xml` automáticamente. Si una landing debe posicionar, avísanos y la añadimos al generador.

## Si hay que tocar `index.html`

`index.html` es la portada y, a la vez, todas las secciones principales: comprar, vender, nosotros y contacto. Es una aplicación renderizada en el navegador, y el proceso de construcción la copia para generar `/vender/`, `/nosotros/`, `/contacto/` y `/en/`. Por eso:

- Un cambio en `index.html` **no se ve en esas secciones hasta la siguiente publicación**. Avísanos después de cambiarlo.
- Las imágenes del archivo se escriben con ruta absoluta (`/foto.jpg`). Mantén esa convención.
- La cabecera, el pie y las direcciones de las secciones los comparten las páginas generadas. Si se cambia la estructura del menú o del pie, hay que replicarlo en las plantillas del generador. Antes de hacerlo, hablamos.

## Diseño

La marca está definida y aprobada. Colores: blanco `#FFFFFF`, champán `#F6EFE3`, crema `#EDD7BF`, carbón `#1E1A17`, burdeos `#7A2027` (hover `#5E171E`), gris `#5C534B`. Tipografías: Cormorant Garamond para titulares y Lato para texto. Una landing debe usar el mismo sistema.

## Flujo de trabajo recomendado

- Trabaja en una **rama propia** y abre un pull request contra `main`. Así se revisa antes de publicar y no colisiona con las publicaciones del catálogo.
- Si subes directamente a `main`, avisa: quien publica el catálogo tiene que hacer `git pull` antes, o su publicación sobrescribirá tu cambio.
- Haz commits pequeños y con mensaje claro, en español.

## Qué no hay que subir nunca

Claves de API, contraseñas, archivos de configuración con credenciales, ni nada que mencione a terceros proveedores de la agencia. El repositorio es público.

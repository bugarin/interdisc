# Sitio web de InterDiSC

Sitio web institucional de **InterDiSC** (interdisc.com.mx) — empresa de Tecnologías
de la Información de Culiacán, Sinaloa, desde 1992. Distribuidor directo de fábrica de
equipo de cómputo y desarrollador de software hospitalario para los sectores salud y
gobierno.

Es un **sitio estático** (HTML + CSS + JS, sin backend ni proceso de build) construido
sobre la plantilla *Ntec* y personalizado para InterDiSC.

---

## 🌐 Despliegue (Vercel + GitHub)

- **Repositorio:** `git@github.com:bugarin/interdisc.git` (rama `main`).
- **Hosting:** Vercel, conectado a este repositorio de GitHub.
- **Flujo de publicación:** cada `git push` a `main` dispara un **despliegue automático**
  en Vercel. No hay paso de build (Vercel sirve los archivos estáticos tal cual).
- **URL de producción:** ver el panel de Vercel del proyecto. Al apuntar el dominio,
  quedará en `https://interdisc.com.mx`.

### Publicar un cambio

```bash
git add -A
git commit -m "describe tu cambio"
git push            # Vercel redespliega solo en ~1 min
```

> Como no hay build, lo que ves en local es exactamente lo que se publica.

---

## 💻 Ver el sitio en local

No requiere instalar nada (Python ya viene en macOS):

```bash
cd site
python3 -m http.server 8000
```

Abre `http://localhost:8000/`. (Conviene servirlo así y no abrir el `.html` con doble
clic, para que las rutas y el menú funcionen igual que en producción.)

---

## 📁 Estructura

```
site/
├── index.html          # Inicio (hero, soluciones, distribuidores, contadores, CTA)
├── conocenos.html      # Conócenos (visión, beneficios, historia, servicios)
├── dar.html            # Soluciones › DAR (Expediente Clínico Electrónico, 22 sistemas)
├── productos.html      # Productos (9 marcas distribuidas)
├── contacto.html       # Contacto (datos, botones directos, mapa)
└── assets/
    ├── css/
    │   ├── main.css        # estilos de la plantilla Ntec (color de marca ya aplicado)
    │   └── interdisc.css   # capa de personalización de InterDiSC (se carga al final)
    ├── js/
    │   └── main.js         # inicializaciones (incluye el contador propio, ver abajo)
    ├── img/
    │   ├── logo/interdisc-logo.png   # logo
    │   ├── interdisc/                # fotos de stock del Inicio (hero, distribuidores, CTA)
    │   ├── about/about__banner__01.png   # imagen del banner de páginas internas
    │   └── feature/feature__01.png       # fondo de la franja CTA
    ├── fonts/   y   scss/   # recursos de la plantilla
```

> El header (menú) y el footer **se repiten en cada `.html`** (es un sitio estático sin
> includes). Si cambias uno, hay que replicar el cambio en las 5 páginas.
>
> El menú tiene un desplegable **"Soluciones"** con **DAR** (`dar.html`). Para agregar
> otra solución, añade un `<li><a href="...">...</a></li>` dentro del `<ul class="sub-menu">`
> de la entrada Soluciones, en las 5 páginas.

---

## ✏️ Cómo editar el contenido

### Datos de contacto
Aparecen en el header, el footer, la franja CTA y en `contacto.html`. Si cambian, busca
y reemplaza en las 4 páginas:

| Dato | Valor actual | Dónde |
|------|--------------|-------|
| Teléfono | `(667) 713 55 35` y enlace `tel:+526677135535` | header, footer, botón "Llamar" |
| WhatsApp | enlace `https://wa.me/526677514421` | botones de WhatsApp |
| Correo | `mailto:interdisc@interdisc.com.mx` | header lateral, footer, contacto |
| Dirección | `Mario Camelo Oriente No. 96, Col. Gabriel Leyva, 80030 Culiacán, Sinaloa, México` | footer, CTA, contacto |
| Mapa | iframe de Google Maps en `contacto.html` (la `?q=` lleva la dirección) | contacto |

### Imágenes
- **Logo:** reemplaza `assets/img/logo/interdisc-logo.png` (mantén proporción).
- **Fotos del Inicio:** `assets/img/interdisc/hero.jpg`, `distribuidores.jpg`, `cta.jpg`.
- **Banner de páginas internas:** `assets/img/about/about__banner__01.png` (se reutiliza en
  Conócenos, Productos y Contacto).
- **Fondo de la franja CTA:** `assets/img/feature/feature__01.png`.

Las fotos actuales son de **stock libre (Unsplash)**; puedes sustituirlas por fotos reales
de InterDiSC manteniendo los mismos nombres de archivo.

### Color de marca
- Acento primario: `#2e74b5` (azul corporativo).
- Paleta multicolor del logo y demás ajustes: variables `:root` al inicio de
  `assets/css/interdisc.css`.

---

## 🔧 Personalizaciones sobre la plantilla Ntec

- `assets/css/interdisc.css`: capa de marca (paleta, motivos multicolor, tarjetas, línea de
  tiempo, botones de contacto, ajustes de imágenes). Se carga **después** de `main.css`.
- `assets/css/main.css`: es el CSS de la plantilla con el color coral original reemplazado
  por el azul `#2e74b5`.
- `assets/js/main.js`: se reemplazó el plugin `jquery.counterup` (incompatible, generaba
  errores) por un contador propio basado en `IntersectionObserver`.
- Se eliminaron las imágenes/badge de relleno del template y los textos en inglés.

---

## ⏳ Pendientes (opcionales)

- Sustituir las fotos de stock por **fotos reales** de InterDiSC.
- Añadir **logos de las marcas** (Productos) y de las soluciones (DAR/Sigho).
- Apuntar el dominio **interdisc.com.mx** al proyecto de Vercel.

---

## Créditos

- Plantilla base: *Ntec* (HTML5).
- Fotografías: [Unsplash](https://unsplash.com) (licencia libre).

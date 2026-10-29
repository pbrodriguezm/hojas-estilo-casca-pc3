# Portafolio Interactivo – Práctica N° 3 (PC3)

**Curso:** Hojas de Estilo en Cascada Avanzado – Sección 20807  
**Docente:** Mg. Ing. Hernán Francisco Peña Carnero  
**Estudiante:** U23315932 – Patrick Rodriguez Marquez  
**Repositorio:** https://github.com/pbrodriguezm/hojas-estilo-casca-pc3

Landing page de un portafolio personal construida con **Bootstrap 5**, **transformaciones CSS** y **animaciones CSS**. Es totalmente responsiva (móvil, tablet y escritorio).

## Cómo ejecutarlo

Abrir `index.html` en el navegador (o con la extensión *Live Server* de VS Code). Bootstrap 5.3.3 se carga por CDN, así que se necesita conexión a internet.

## Estructura

```
Practica 3/
├── index.html        # estructura con Bootstrap 5
├── css/
│   └── estilos.css   # transformaciones y animaciones (CSS puro)
├── capturas/         # capturas de la página y del código
└── README.md
```

## Bootstrap 5

| Componente | Clases usadas |
|---|---|
| Navbar con logo y menú (Inicio, Proyectos, Contacto) que colapsa en hamburguesa | `navbar navbar-expand-lg navbar-dark bg-dark`, `navbar-toggler`, `collapse navbar-collapse` |
| Sistema de grid | `container`, `row`, `col-sm-12`, `col-md-6`, `col-lg-4` |
| Formulario de contacto (Nombre, Email, Mensaje) | `form-label`, `form-control`, `mb-3` |
| Botones "Enviar" y "Limpiar" | `btn btn-primary`, `btn btn-secondary` dentro de `d-grid gap-2` |

## Transformaciones 2D (sección Proyectos, al hacer `:hover`)

Las tres tarjetas usan `transition: transform 0.5s ease, box-shadow 0.5s ease` para que el cambio sea suave.

| Tarjeta | Transformación |
|---|---|
| Caja 1 – PeruRail Reservas | `transform: rotate(-5deg)` |
| Caja 2 – TaxiIA | `transform: scale(1.08)` |
| Caja 3 – Dashboard de Ventas | `transform: translateY(-15px) skewX(-4deg)` |

## Transformación 3D (sección Inicio)

Tarjeta que gira al pasar el mouse:

- El contenedor padre `.escena-3d` tiene `perspective: 1000px`.
- La tarjeta `.tarjeta-3d` usa `transform-style: preserve-3d` y parte inclinada con `rotateX(10deg) rotateY(-20deg)`.
- En `:hover` pasa a `rotateX(0deg) rotateY(180deg)` y muestra la cara trasera (`backface-visibility: hidden`), con `transition: transform 0.9s ease`.

## Animaciones (`@keyframes`)

| Animación | Elemento | Propiedades de control |
|---|---|---|
| `girar` (loader) | Spinner circular de la pantalla de carga | `animation-duration: 1s`, `animation-timing-function: linear`, `animation-iteration-count: infinite` |
| `ocultar-loader` | Pantalla de carga que desaparece sola | `animation-duration: 0.6s`, `animation-delay: 1.8s`, `animation-fill-mode: forwards` |
| `deslizar-izquierda` | Título y texto del inicio que aparecen deslizándose | `animation-duration: 1s`, `animation-timing-function: ease-out`, `animation-iteration-count: 1` |
| `latido-color` | Logo "PR" de la navbar: cambia de color y tamaño | `animation-duration: 3s`, `animation-timing-function: ease-in-out`, `animation-iteration-count: infinite`, `animation-direction: alternate` |
| `brillo` | Etiqueta "Disponible para proyectos" que cambia de color | `animation-duration: 2s`, `animation-iteration-count: infinite`, `animation-direction: alternate` |

## Responsividad

- En móvil el menú se convierte en hamburguesa y las columnas se apilan (`col-sm-12`).
- En tablet las tarjetas se muestran en 2 columnas (`col-md-6`) y en escritorio en 3 (`col-lg-4`).
- Una media query (`max-width: 767px`) centra el inicio y reduce la altura de la tarjeta 3D.
- No hay desbordamiento horizontal (verificado a 390px de ancho).

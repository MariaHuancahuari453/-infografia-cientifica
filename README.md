
El proyecto está diseñado como un **archivo único autocontenido**. No requiere estructura de carpetas, dependencias externas ni procesos de compilación. Todo el marcado, los estilos y la lógica interactiva residen dentro de `index.html`.

### Secciones del HTML

| Sección              | Contenido                                                        |
| --------------------- | ---------------------------------------------------------------- |
| **Hero**              | Título principal, descripción, llamada a la acción y canvas de burbujas animadas |
| **Introducción**      | Contexto del problema y rol de la capacitación técnica           |
| **Datos clave**       | Cuatro tarjetas con los datos principales y contadores animados  |
| **Impacto económico** | Barras de progreso, medidor circular SVG de participación femenina |
| **Sostenibilidad**    | Diagrama de flujo del ciclo RAS y beneficios del reciclaje       |
| **Conclusión**        | Síntesis de las cuatro cifras principales                        |
| **Footer**            | Fuente APA y autoría del diseño                                  |

### Arquitectura CSS

- **Variables CSS** (`:root`): paleta cromática, radios, transiciones y fondos centralizados.
- **Diseño mobile-first**: media queries progresivas en `560px`, `640px`, `768px` y `960px`.
- **Clases utilitarias**: `.reveal` para animaciones de entrada, `.delay-1` a `.delay-4` para escalonamiento.
- **Componentes**: `.data-card`, `.impact-block`, `.ras-step`, `.conclusion-box`, entre otros.

### Módulos JavaScript

| Módulo                  | Responsabilidad                                          |
| ----------------------- | -------------------------------------------------------- |
| **Burbujas (Canvas)**   | Genera y anima 40 burbujas ascendentes con oscilación sinusoidal en el hero |
| **Reveal (IO)**         | Detecta elementos `.reveal` al entrar en viewport y activa la transición fade-in |
| **Contadores**          | Anima números de 0 a su valor objetivo con easing cúbico |
| **Medidor circular**    | Anima el `stroke-dashoffset` del SVG y el texto porcentual |
| **Barras de progreso**  | Anima el ancho de las barras de impacto económico        |

Todos los módulos usan `IntersectionObserver` para activarse solo cuando son visibles, y respetan `prefers-reduced-motion: reduce` desactivando animaciones cuando el usuario lo solicita.

---

## Tecnologías utilizadas

| Tecnología         | Uso                                                      |
| ------------------ | -------------------------------------------------------- |
| **HTML5**          | Estructura semántica con `<header>`, `<section>`, `<footer>`, roles ARIA |
| **CSS3**           | Variables CSS, Grid, Flexbox, gradientes, transiciones, `@keyframes`, media queries |
| **JavaScript ES5+** | Canvas 2D, IntersectionObserver, requestAnimationFrame, manipulación DOM |
| **Google Fonts**   | *Playfair Display* (títulos) y *DM Sans* (cuerpo), cargadas vía `<link>` |
| **SVG inline**     | Medidor circular, ondas separadoras de secciones         |

**No se utilizan frameworks, librerías ni herramientas de compilación.** Sin Bootstrap, sin React, sin bundlers.

---

## Paleta de colores

| Color    | Hex       | Uso principal                         |
| -------- | --------- | ------------------------------------- |
| Deep     | `#005F73` | Fondos oscuros, acentos de profundidad |
| Mid      | `#0A9396` | Acentos principales, barras, gauge    |
| Accent   | `#9D2D8D` | Destacados, CTA, participación femenina |
| BG       | `#021E24` | Fondo base del cuerpo                 |
| BG Alt   | `#03292F` | Fondo alternativo de secciones pares  |
| FG       | `#E4F2ED` | Texto principal                       |
| FG Muted | `#8AABA3` | Texto secundario y descripciones      |

---

## Cómo visualizar localmente

### Opción 1 — Doble clic (la más rápida)

Haz doble clic sobre el archivo `index.html`. Se abrirá en tu navegador predeterminado y la infografía funcionará completamente, incluyendo animaciones, contadores y el canvas de burbujas.

### Opción 2 — Servidor local (recomendada)

Usa cualquier servidor estático para evitar restricciones CORS durante el desarrollo:

```bash
# Con Python 3
python3 -m http.server 8080

# Con Node.js (npx, sin instalación global)
npx serve .

# Con PHP
php -S localhost:8080
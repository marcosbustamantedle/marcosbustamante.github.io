# Web Marcos Bustamante: mapa del proyecto

Lee esto antes de tocar nada. Busca el texto entre comillas para ir directo a cada parte. Si cambias la estructura, actualiza este mapa en el mismo commit.

## Qué es

Web pública de Marcos Bustamante, fisio deportivo y entrenador (Santander y online), más un formulario de pre-consulta para clientes. HTML estático servido por GitHub Pages, sin build ni dependencias: cada página lleva su CSS y su JS dentro.

## Ficheros

| Fichero | Qué hay |
| --- | --- |
| `index.html` | Página principal (~500 líneas). |
| `pre-consulta/index.html` | Formulario de pre-consulta (13 preguntas en 5 bloques). Ya viene comentado por dentro, paso a paso. |
| `pre-consulta/gracias.html` | Página que ve el cliente después de enviar el formulario. |
| `docs/` | **Copia idéntica** de los tres ficheros de arriba. No sabemos cuál de las dos sirve GitHub Pages (raíz o `/docs`), así que cualquier cambio se hace en las dos copias y se comprueba con `diff -q index.html docs/index.html`. |
| `.nojekyll` | Evita que GitHub procese la web con Jekyll. No borrar. |

## index.html por partes

- **CSS** en el `<style>` del `<head>`: variables de marca al principio (colores `--mb-*` y fuentes).
- **"header class=\"top\""**: logo, menú de escritorio y botón "Menú" (`#menu-btn`), que abre el menú móvil (`#menu-movil`).
- **Secciones**, en orden: hero ("section class=\"hero\"", lema y botones), "id=\"servicios\"" (Valoración y Rutina personalizada, precio "A tu medida"), "class=\"sec objetivos\"" (4 objetivos), "id=\"como-trabajo\"" (3 pasos), "// Modalidades" (presencial y online), "id=\"sobre-mi\"" (bio y trayectoria; la foto es un hueco "Espacio para tu foto"), "id=\"contacto\"".
- **"nav class=\"barra-movil\""**: barra fija de WhatsApp y Reservar en el móvil.
- **"<footer>"**.
- **JS** al final: contacto en `const WHATSAPP`, `const CALENDLY` y `const MENSAJE`. Todos los enlaces con clase `js-wa` van a WhatsApp y los `js-cal` a Calendly: para cambiar el número o el enlace de reserva, se toca solo ahí. También el menú móvil y el botón "Copiar número".

## pre-consulta/index.html

- Lo envía FormSubmit: "action=\"https://formsubmit.co/..." manda las respuestas al correo de Marcos. Los campos ocultos que empiezan por `_` son ajustes de FormSubmit (asunto, formato tabla, página de gracias, campo trampa antispam).
- Bloques marcados con "========== BLOQUE N": 1 Datos básicos, 2 Motivo de la consulta, 3 Antecedentes, 4 Señales de alerta, 5 Expectativas, y después "PRIVACIDAD Y CONSENTIMIENTO".
- El `<script>` del final arma el asunto con el nombre del cliente y junta las casillas marcadas.
- La página no se indexa en Google (`noindex`): es solo para clientes.

## No tocar sin cuidado

- El texto de privacidad está marcado como "PENDIENTE DE REVISIÓN LEGAL": no lo des por válido ni lo cambies sin avisar.
- Los datos sanitarios del formulario viajan por FormSubmit hasta el correo: cualquier cambio en el envío afecta a datos de salud de clientes.
- La marca: colores y fuentes según la skill `marca-marcos-bustamante` (Anton, Barlow, Barlow Condensed, IBM Plex Mono; negro, amarillo, azul).
- Las dos copias (raíz y `docs/`) deben quedar iguales.

# Invitación de bautizo: cómo editarla

Todo está en `index.html`. Ábrelo con cualquier editor (VS Code, por ejemplo) y para verlo dale doble clic o arrástralo al navegador.

## Textos
Busca el texto dentro de `index.html` y cámbialo. Escribe en minúsculas normales: las mayúsculas las pone el estilo.
- **Nombre del bebé:** `Amyra` (h1) e `Irlanda`, en la sección PORTADA. Se ven en dorado.
- **Papás / padrinos:** secciones MIS PAPÁS y MIS PADRINOS. El `&amp;` es el símbolo "&".
- **Fecha:** `15`, `Domingo`, `de nov.`, `09:30`, `Am.`
- **Lugares y horarios:** sección ITINERARIO.
- **Título de la pestaña y vista previa de WhatsApp:** `<title>` y las etiquetas `og:` al inicio.

Si un texto queda más largo o más corto, ajusta su `left` / `width` en el atributo `style`.

## Imágenes (carpeta `img/`)
Para cambiar una imagen, **reemplaza el archivo por otro con el mismo nombre**. Usa PNG con fondo transparente para que se vea bien sobre el rosa. Si la nueva imagen tiene otra proporción, no se deforma (se ajusta dentro de su caja).

| Archivo | Dónde aparece |
|---|---|
| `conejita-portada.png` | Conejita sentada de la portada |
| `conejita-papas.png` | Conejita junto a "Mis Papás" |
| `conejita-confirmar.png` | Conejita del final, junto a "Te Esperamos" |
| `marco-encaje.png` | Marco ovalado de encaje de la portada |
| `flores-marco.png` | Flores a la izquierda del marco |
| `ramo-1.png` … `ramo-6.png` | Ramos de flores decorativos (se repiten en varias secciones) |
| `rama-flores.png` | Ramitas alrededor de "Restan" |
| `franja-flores-1.png` | Franja de flores bajo el botón de música |
| `franja-flores-2.png` | Franja de flores en "Mis Papás" y al final |
| `mariposa-*.png` | Mariposas (lila, rosa y amarilla, de frente y de perfil) |
| `iglesia.png` | Iglesia de la tarjeta (Misa) |
| `copas.png` | Copas de la tarjeta (Recepción) |
| `textura-papel.jpg` | Fondo de papel de la tarjeta del itinerario |
| `boton-amarillo.png` | Fondo de los botones "Ver ubicación" y "Confirmar aquí" |
| `titulo-dorado-original.png` | Título dorado original de Canva. No se usa, queda como referencia |

Para mover o cambiar el tamaño de cualquier imagen, edita `left`, `top`, `width` y `height` en su `style`. Las medidas están en px sobre un diseño de 390 px de ancho, y la página se escala sola a cualquier pantalla.

## Cuenta regresiva, música y links
Al final de `index.html`, en `CONFIG`:
- `fechaEvento: '2026-11-15T09:30'`: pon aquí la fecha real (año-mes-díaThora:min). Si la fecha ya pasó, el contador se queda en 0.
- `musicaYoutube`: el ID del video de YouTube, o sea lo que va después de `v=` en el link.
- `musicaArchivo`: si prefieres tu propio MP3, ponlo en una carpeta (ej. `musica/cancion.mp3`) y escribe aquí esa ruta.

> **Ojo:** YouTube no suena si abres el archivo con doble clic. Sí suena cuando la invitación está publicada en internet. Con un MP3 propio suena en los dos casos.

Links de los botones: busca `href=` en los botones "Ver ubicación" (Google Maps) y "Confirmar aquí" (WhatsApp).

## Invitados con pase personalizado
En **/admin** (`admin.html`) se crean invitaciones con el nombre del invitado y sus lugares (personas en total, contando al invitado). Cada invitación tiene un link `…/?i=CÓDIGO` que se copia o se manda directo por WhatsApp.

Cuando el invitado abre su link:
- Arriba de la portada aparece "Con mucho cariño para" + su nombre.
- Antes de "Te Esperamos" aparece la tarjeta **Tu Pase**: los lugares reservados, cuántas personas asistirán (de 1 hasta el máximo) y los botones **Confirmar asistencia** / **No podré asistir**.
- Al responder, la respuesta se guarda (en el admin se ve en vivo quién confirmó y cuántos van) y se abre WhatsApp con el mensaje listo para enviar.
- Puede cambiar su respuesta después desde el mismo link.

Sin código (o con un código que no existe) la invitación se ve como siempre, con el botón "Confirmar aquí".

Dónde se configura:
- **Número que recibe las confirmaciones:** `whatsappConfirmar` en `CONFIG` (52 + número a 10 dígitos).
- **Texto de los mensajes de WhatsApp:** función `mensajeWhatsApp()` al final de `index.html`.
- **Mensaje con el que se manda la invitación:** `mensajeInvitacion` en `admin.html`.
- **Datos de Firebase:** `firebase-config.js`.

### Firebase (una sola vez)
Publicar las reglas de `firestore.rules`: `firebase deploy --only firestore:rules` (o pegarlas en Firebase Console → Firestore Database → Reglas → Publicar).

**Ojo:** el admin no pide contraseña. Cualquiera que tenga el link `/admin` puede ver, editar y borrar la lista, así que no lo compartas. Las reglas no protegen quién edita, pero sí evitan datos sin sentido (por ejemplo, más asistentes que lugares).

## Colores y tipografías
Al inicio del `<style>`, en `:root`: `--rosa` (color del texto), `--fondo` y las fuentes.
Tres de las fuentes originales de Canva son comerciales (Slight, MADE TheArtist Script y BLOSTA), así que se cambiaron por equivalentes gratuitos de Google Fonts (WindSong, Sacramento y Josefin Sans).

## Publicarla
Sube la carpeta completa (`index.html`, `admin.html`, `firebase-config.js`, `vercel.json` + `img/`) a un hosting estático gratuito. Está publicada en Vercel: `vercel.json` hace que el admin abra en `/admin`. La opción más fácil es Netlify Drop (app.netlify.com/drop): arrastras la carpeta y te da un link para compartir. También sirven GitHub Pages o Vercel.

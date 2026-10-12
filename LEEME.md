# Invitación de bautizo: cómo editarla

Todo está en `index.html`. Ábrelo con cualquier editor (VS Code, por ejemplo) y para verlo dale doble clic o arrástralo al navegador.

## Textos
Busca el texto dentro de `index.html` y cámbialo. Escribe en minúsculas normales: las mayúsculas las pone el estilo.
- **Nombre del bebé:** `Alana` (h1) y `Gabriela`, en la sección PORTADA. Se ven en dorado.
- **Papás / padrinos:** `Mariana Olvera<br>&amp;<br>Carlos Mendoza`. El `&amp;` es el símbolo "&".
- **Fecha:** `20`, `Sábado`, `de junio`, `05:00`, `Pm.`
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
- `fechaEvento: '2026-06-20T17:00'`: pon aquí la fecha real (año-mes-díaThora:min). Si la fecha ya pasó, el contador se queda en 0.
- `musicaYoutube`: el ID del video de YouTube, o sea lo que va después de `v=` en el link.
- `musicaArchivo`: si prefieres tu propio MP3, ponlo en una carpeta (ej. `musica/cancion.mp3`) y escribe aquí esa ruta.

> **Ojo:** YouTube no suena si abres el archivo con doble clic. Sí suena cuando la invitación está publicada en internet. Con un MP3 propio suena en los dos casos.

Links de los botones: busca `href=` en los botones "Ver ubicación" (Google Maps) y "Confirmar aquí" (WhatsApp).

## Colores y tipografías
Al inicio del `<style>`, en `:root`: `--rosa` (color del texto), `--fondo` y las fuentes.
Tres de las fuentes originales de Canva son comerciales (Slight, MADE TheArtist Script y BLOSTA), así que se cambiaron por equivalentes gratuitos de Google Fonts (WindSong, Sacramento y Josefin Sans).

## Publicarla
Sube la carpeta completa (`index.html` + `img/`) a un hosting estático gratuito. La opción más fácil es Netlify Drop (app.netlify.com/drop): arrastras la carpeta y te da un link para compartir. También sirven GitHub Pages o Vercel.

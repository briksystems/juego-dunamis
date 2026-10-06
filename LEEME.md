# Dunamis, juego de pistas

Página de un solo nivel de código. Funciona en celular y computador. No necesita servidor propio ni base de datos. Solo archivos estáticos.

## Qué contiene

- index.html: todo el código (HTML, CSS y JavaScript juntos)
- assets/c24dcd9f-image.jpg: fondo de toda la página
- assets/d1788457-image.png: barra del jugador (pastilla verde con la D)
- assets/471def09-image.png: barra del computador (la ola)
- assets/9e6f2fe2-image.png: llama que se ve detrás de la cancha
- assets/logo-dunamis.png: logo blanco del inicio y de la revelación

Los nombres de los archivos no se cambiaron. Si se renombra alguno, hay que actualizar la ruta en el bloque CONFIG de index.html.

## Cómo meterlo en la página madre

Opción recomendada, con iframe. Es la más segura porque no choca con los estilos ni el código de la página madre.

1. Subir la carpeta completa dunamis (con index.html y assets juntos) al mismo sitio.
2. En la página madre poner:

   <iframe src="/dunamis/index.html" title="Dunamis" style="width:100%;height:100dvh;border:0" allow="web-share; autoplay"></iframe>

Opción alterna: enlazar a /dunamis/index.html como una página aparte.

El juego ocupa todo el alto de su ventana. Dentro de un iframe toma el tamaño del iframe. Se recomienda darle alto completo de pantalla.

## Qué se edita (todo en el bloque CONFIG, al inicio del script)

- guests: nombre, respuestas aceptadas, foto y las 3 pistas de cada invitado. Hoy tienen texto de relleno (Lorem ipsum).
- pointsToWin: puntos para ganar cada nivel. Hoy es 2.
- event: fecha y lugar que se muestran al final.
- assets: rutas de las imágenes.

La tipografía se cambia en las variables --sans y --display, arriba en el CSS. Hoy usa Montserrat desde Google Fonts, por lo que necesita internet. Si se prefiere otra fuente, se cambia el enlace de Google Fonts y esas dos variables.

## Cosas que debe saber el programador

- El progreso de cada persona se guarda en su propio navegador (localStorage, clave dunamis-progreso-v1). No se envía nada a ningún servidor.
- Los nombres de los invitados quedan dentro del código. Alguien con conocimientos técnicos podría verlos. Si eso es un problema, la validación de la respuesta se pasa a un servidor.
- Para pruebas se puede agregar a la dirección: ?rapido (cada nivel se gana con 1 punto) y ?reset (borra el progreso guardado). No afectan a los usuarios normales.
- La llama de fondo pesa cerca de 1.6 MB y el fondo cerca de 1 MB. Si se quiere que cargue más rápido en datos móviles, se pueden comprimir manteniendo el mismo nombre y las mismas medidas.
- Las barras se dibujan recortando una zona exacta de cada imagen. Si se cambia una imagen por otra con otras medidas, hay que ajustar PLAYER_ART o CPU_ART en el script.

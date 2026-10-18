# anylum · Derecho al alcance de todos

Sitio web de anylum: resúmenes de derecho, herramientas y juegos para servidores judiciales, estudiantes y abogados del Perú.

- `index.html`: portada. Pregunta qué vienes a hacer (Aula, Judicial o Pro) y despliega las apps de ese camino.
- `aula/`: app Aula Anylum. Lecciones en etapas de juego (Introducción al Derecho y Código Procesal Civil por secciones), cuenta para guardar el avance y comentarios moderados.

Es un sitio estático: no necesita instalación. Para publicarlo, activa GitHub Pages desde la rama `main` y la carpeta raíz.

## Pendientes de configuración

Al final de `index.html`, en el objeto `ANYLUM`, completa:

- `yape` y `plin`: número de celular para recibir aportes.
- `yapeQR`: nombre del archivo con el código QR de Yape (súbelo a la raíz, por ejemplo `yape-qr.png`).
- `tarjeta`: enlace de pago con tarjeta.

Mientras estén vacíos, los botones avisan que el servicio llega muy pronto.

El contenido es educativo y no reemplaza la asesoría legal de un profesional.

## Supabase

El boletín, las cuentas del Aula y los comentarios usan el mismo proyecto de Supabase que la calculadora. Las tablas `progreso_aula` y `comentarios` se crean con el script SQL que acompaña la entrega. Los comentarios solo se publican cuando se marcan como `aprobado` en Supabase.

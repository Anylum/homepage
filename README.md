# anylum · Derecho al alcance de todos

Sitio web de anylum: resúmenes de derecho, herramientas y juegos para servidores judiciales, estudiantes y abogados del Perú.

- `index.html`: portada. Pregunta qué vienes a hacer (Aula, Judicial o Pro) y despliega las apps de ese camino.
- `aula/`: app Aula Anylum. Lecciones en etapas de juego (Introducción al Derecho y Código Procesal Civil por secciones), cuenta para guardar el avance y comentarios moderados.

Es un sitio estático: no necesita instalación. Para publicarlo, activa GitHub Pages desde la rama `main` y la carpeta raíz.

El contenido es educativo y no reemplaza la asesoría legal de un profesional.

## Cómo editar el contenido (Supabase)

Todo se edita en Supabase → **Table Editor**. Los cambios se ven en la web al recargar la página; no hace falta tocar el código. Si Supabase no responde, la web muestra el contenido que trae escrito como respaldo.

| Tabla | Qué controla |
|---|---|
| `sitio_config` | Yape (`yape`), Plin, enlace de tarjeta, textos de Sobre mí, franja de aviso (`aviso`) y aviso del Aula (`aula_aviso`). Valor vacío = oculto. |
| `aula_unidades` | Unidades del Aula: título, sección, descripción, `orden` y `estado` (`publicada`, `proximamente` u `oculta`). |
| `aula_etapas` | Etapas de cada unidad: `tipo` (`leer`, `vf`, `ordenar`, `parejas`, `caso`), título, objetivo, `orden`, `visible` y `contenido`. |
| `biblioteca_resumenes` | Resúmenes: materia (crea sus filtros), título, `pasos`, fuente, `caminos` (puntos de color) y `destacar_en` (aparece en Judicial o Pro). |
| `enlaces` | Enlaces de interés: categoría, título, url, descripción, `orden` y `visible`. |
| `redes_sociales` | Pega la url de cada red; solo se muestran las que tienen url. En WhatsApp basta el número y en Correo, la dirección. |
| `comentarios` | Comentarios del Aula. Llegan ocultos; marca `aprobado` para publicarlos. |

La calculadora de plazos lee sus propias tablas en el mismo proyecto: `plazos`, `feriados`, `terminos_distancia`, `codigos`, `reglas_notificacion`, `reglas_calculo`, `lecciones`, `textos` y `avisos`.

### El campo `contenido` de una etapa

Lo más fácil es duplicar una etapa del mismo tipo y cambiar los textos. `correcta` cuenta desde 1. Se puede usar `<b>` e `<i>` en los textos.

- `leer`: `{"texto": ["párrafo 1", "párrafo 2"], "pregunta": {"enunciado": "…", "opciones": ["A", "B"], "correcta": 2, "explicacion": "…"}, "fuente": "…"}`
- `vf`: `{"afirmaciones": [{"texto": "…", "verdadero": true, "explicacion": "…"}]}`
- `ordenar`: `{"orden_correcto": ["primero", "segundo", "tercero"], "explicacion": "…"}`
- `parejas`: `{"parejas": [{"izquierda": "…", "derecha": "…"}]}`
- `caso`: `{"caso": "…", "opciones": ["A", "B", "C"], "correcta": 2, "explicacion": "…"}`

Si una etapa queda incompleta, el Aula la salta en lugar de romperse. El avance de cada estudiante se guarda por el `id` de la etapa: no cambies el `id` de una etapa publicada.

## Cuentas del Aula

El avance con cuenta (`progreso_aula`) usa el inicio de sesión por enlace al correo de Supabase. En Authentication → URL Configuration agrega `https://anylum.github.io/homepage/aula/` en **Redirect URLs** (y como **Site URL** si no hay otra).

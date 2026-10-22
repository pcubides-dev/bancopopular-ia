# Caiga en la Nota

Juego tipo karaoke: suena una canción, la música se silencia unos segundos, la gente sigue cantando y, cuando vuelve el sonido, aparece la línea exacta donde va la canción. Juega una persona a la vez: el presentador (o el micrófono) decide si "cayó en la nota" y los puntos van al participante de turno.

## Cómo correrlo

YouTube no permite insertar videos desde `file://`, así que hay que servirlo con un servidor local:

```bash
cd caiga-en-la-nota
python3 -m http.server 8000
# abre http://localhost:8000 en Chrome
```

## Fuentes de música

| Fuente | Qué necesita |
|---|---|
| **YouTube / YouTube Music** | Pegar el enlace (`music.youtube.com/watch?v=…` o `youtube.com/watch?v=…`). Algunos videos no permiten insertarse (error 150). |
| **Apple Music** | Un developer token de MusicKit (cuenta Apple Developer) y una cuenta con suscripción a Apple Music. |
| **Archivo** | Un MP3/M4A local. Funciona sin internet. |
| **Demo** | Nada. Ritmo sintetizado con «Cielito lindo» (dominio público). |

Las letras sincronizadas se buscan en [LRCLIB](https://lrclib.net) o se pegan en formato LRC (`[01:23.45] texto`).

## Cómo se juega

- Agrega a los participantes y marca qué canciones de **Fonseca** entran al sorteo (Te mando flores, Arroyito, Simples corazones, Eres mi sueño, Por pura curiosidad, Vine a buscarte, Estar lejos).
- **Sorteo por turno:** lo primero que se ve en cada turno es la pantalla de sorteo. Ahí se elige o se agrega a quien canta y se pulsa **Sortear canción** (o `Espacio`); la luz recorre las canciones, cae en una y la música arranca sola con su letra. No se repite una canción hasta que hayan salido todas las marcadas.
- Cada canción trae varios videos de respaldo: si YouTube no deja insertar uno, se prueba el siguiente. Si el video que carga dura distinto que la letra, se busca la letra de esa duración.
- Juega **una persona a la vez**; el botón **Jugar** de cada nombre le da el turno y abre el sorteo.
- **Rondas por turno:** 3, 5 o sin límite. Al terminar, la canción se pausa, se muestra el total del turno y el botón pasa al siguiente participante, que sortea su propia canción.
- **Silencios automáticos:** al empezar una línea, la música se silencia y vuelve exactamente al inicio de una línea posterior (según la duración elegida).
- **Silencios manuales:** el presentador pulsa `Espacio` para silenciar y para volver.
- Al volver la música se muestra la línea donde va la canción y se califica al participante: En la nota +100, Cerca +50, Perdido 0.
- **Micrófono (experimental, Chrome/Edge):** transcribe lo que canta durante el silencio y sugiere una calificación.
- **Ajuste de letra por canción:** si la letra no va a tiempo, pulsa **La letra va tarde** (`→`) o **La letra va antes** (`←`), de 0.25 s en 0.25 s, o **Ajustar letra aquí** justo cuando el cantante empiece una línea. El ajuste queda guardado para ese video en ese navegador.
- **Dejar los ajustes fijos:** en la tarjeta *Ajustes de letra*, **Copiar ajustes** copia los valores; se pegan en `OFFSETS` dentro de `index.html` para que sirvan en cualquier dispositivo.
- El silencio nunca dura más que el tiempo hasta la línea de regreso más 3 s (máximo 30 s); si el video quedó detenido al volver el sonido, se reanuda solo.

Atajos: `Espacio` silenciar/volver · `P` reproducir/pausar · `←` `→` ajustar letra · `1` en la nota · `2` cerca · `3` perdido · `Enter` siguiente ronda.

## Antes de usarlo en eventos públicos

Las suscripciones de streaming son de uso personal. Para bares o eventos se necesita licencia de comunicación pública (en Colombia, SAYCO-ACINPRO), y para un producto comercial, letras con licencia (Musixmatch o LyricFind).

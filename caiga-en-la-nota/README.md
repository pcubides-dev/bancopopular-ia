# Caiga en la Nota

Juego tipo karaoke: suena una canción, la música se silencia unos segundos, la gente sigue cantando y, cuando vuelve el sonido, aparece la línea exacta donde va la canción. El presentador (o el micrófono) decide qué equipos "cayeron en la nota".

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

- **Silencios automáticos:** al empezar una línea, la música se silencia y vuelve exactamente al inicio de una línea 1 a 5 líneas después (según la duración elegida).
- **Silencios manuales:** el presentador pulsa `Espacio` para silenciar y para volver.
- Al volver la música se muestra la línea donde va la canción y se puntúa: En la nota +100, Cerca +50, Perdidos 0.
- **Micrófono (experimental, Chrome/Edge):** transcribe lo que canta el público durante el silencio y sugiere un veredicto.
- **Ajustar letra aquí:** si la letra va adelantada o atrasada, pulsa el botón justo cuando empiece una línea.

Atajos: `Espacio` silenciar/volver · `P` reproducir/pausar · `1`–`9` equipo en la nota · `Enter` siguiente ronda.

## Antes de usarlo en eventos públicos

Las suscripciones de streaming son de uso personal. Para bares o eventos se necesita licencia de comunicación pública (en Colombia, SAYCO-ACINPRO), y para un producto comercial, letras con licencia (Musixmatch o LyricFind).

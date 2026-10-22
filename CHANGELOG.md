# Cambios de cada versión

## 2026-10-22b — Villa con graves y agudos, turnos de invitados con perfiles, salud del ESP32, subida de música corregida
- Casas y túnel: patrón «Graves a agudos (música)» y 6 colores nuevos de casas (uno cambia con la música)
- Escenas y shows al día con la villa; ambiente «Túnel del tren» en el generador
- Invitados: perfiles de control, permisos por acción, zonas (árbol, casas, túnel, tren), interruptor de aceptar invitados, música y volumen con tope
- Turnos: aviso a los 30 s, aviso al siguiente, «ya es tu turno» y extender 2 min si nadie espera
- Sistema: panel Salud del ESP32 (memoria, temperatura, WiFi, MAC, último reinicio)
- Tarjeta «En escena» describe qué hace la escena en árbol, casas, túnel, tren, estrella y giro
- Música: los nombres largos conservan la extensión; registro de actividad de subidas
- El PIN de 4 cifras entra solo al teclear la cuarta

## 2026-10-22 — Villa de 13 LED, prueba de luces, sensor de vuelta y web minimizada
- La villa pasa a una tira de 13 LED RGB (sin blanco) en el orden real: casa 1 (2 LED), pasillo, casas y túnel del tren de 7 luces; MOSFET propio de la villa (GPIO 9) y LED blanco simple opcional para el tren (GPIO 10).
- Botón de pulsador momentáneo: 1 toque enciende o apaga, 2 música, 3 escena siguiente, 4 modo «todo»; rescate del PIN con 6 pulsaciones y 10 s apretado.
- Nueva Prueba de luces en Sistema: encender cada casa, luz del túnel, LED del árbol o estrella con color e intensidad, recorrido uno a uno, todo a máximo y opción de ignorar el límite de corriente para medir el consumo.
- 10 patrones nuevos para las casas y 12 para el túnel, y 6 espectáculos con la villa como protagonista.
- Franja con las 5 casas y el túnel junto al árbol, y aviso fijo de cambios sin guardar en Sistema.
- Sensor de vuelta opcional (GPIO 11) y cambio de sentido rápido; el giro puede invertirse con el tren dentro del túnel.
- El brillo global se nota en el visor 3D. La web va minimizada dentro del programa.

## 2026-10-21 — Motor paso a paso y villa de 10 LED
- El motor del árbol pasa a ser un **NEMA 17 con A4988** (STEP 16, DIR 12, ENABLE 8): velocidad exacta y **giro en los dos sentidos** por escena (un sentido, al revés, va y viene cada 20 s o cada 8 s). Se quitan el MOSFET del motor, el puente H y el ajuste de vueltas al mínimo.
- Se quita el ULN2803A de las casas: la **segunda tira direccionable** (GPIO 13) lleva ahora 10 LED: 3 luces de paso al principio, 2 del tren y 5 casas al final. Las casas tienen color propio.
- Luces de **paso** y **casas** con patrones, color y máscara propios (6 patrones de casa nuevos), y un selector de **protagonismo**: «las casas protagonistas» deja al árbol con un efecto sencillo y tranquilo mientras las casas se llevan la vista.
- Ambiente **🏘 Villa protagonista** en el generador de escenas y 5 escenas de fábrica nuevas. La villa de la página y la tarjeta «En escena» pintan el color real de cada casa y de los 3 farolitos.
- Diagrama de conexiones y manual actualizados.

## 2026-10-21 — Tira en espiral y distancias entre LED
- Pestaña **🎮 Juegos** con cuatro juegos desde el celular: **Snake** (la culebra sube por 5 niveles hasta la estrella, con animación de inicio y de victoria), **Tocados** (dos jugadores mueven unos puntos de luz y gana quien toque primero al otro), Pong y tres en raya.
- Nueva capa **Cuadros de ajedrez** (casillas del mismo tamaño que suben, bajan, giran o cambian de color) y 100 efectos de tablero.
- Almacenamiento a prueba de miles: música en 256 subcarpetas con índice (elegir al azar o la siguiente sin recorrer carpetas), y efectos del usuario, de invitados y espectáculos en almacenes por registros; las copias de seguridad los leen de uno en uno; la caché de la PSRAM descarta lo menos usado. Los archivos antiguos se pasan solos al arrancar.
- Nuevo ajuste «Mi tira es una espiral» (activo por defecto): la tira sube desde abajo en sentido horario, 12 LED por vuelta, y el LED 0 y el 1 están en la misma cara.
- Conexiones: dibujo de la espiral con la estrella, y distancias de centro a centro entre LED (fijas en la misma placa, siguiendo el cono al cambiar de cara o fila). Tocando un cable se ve su medida.
- Registro de errores y reporte de fallos (informe sin datos personales para GitHub o Telegram; aviso automático si el árbol se reinicia solo).
- Tarjeta «En escena» con vista plana del árbol, un punto por casa que brilla como la casa, y la villa animada sale del ESP32 (sigue en el repositorio).
- Flores y emojis (16 bytes) que giran y rebotan; rebote DVD en dos dimensiones; espiral corregida en la punta; 1000+ efectos nuevos, 120 escenas y 40 espectáculos.
- Juegos con el celular: Pong (un LED rebota entre dos barras, uno o dos celulares, o contra el árbol) y tres en raya, desde /juego.html.
- Motor de efectos con piezas avanzadas: rebote tipo DVD, pelotas con gravedad, juego de la vida, metabolas, filtros (tono, giro, espejo, caleidoscopio, desenfoque, posterizar, invertir, contraste, torsión), estela y onda lenta en cualquier capa; 48 efectos nuevos.
- Pantalla de la tele: información, sonómetro y menú de acceso rápido con el control remoto.
- Motor de efectos: la capa «espiral» ahora es una espiral de verdad (rayas verticales corregidas) y se compensa la mayor densidad de LED de la punta en todos los efectos.
- Motor con puente H (opcional): el GPIO 12 da el sentido de giro y la casa 5 se une a la casa 4; panel H en Conexiones.
- Descanso del árbol: se apaga tras N horas encendido o por ratos (X min encendido, Y min apagado), configurable y desactivado de fábrica.
- Pantalla LCD 1602 con perilla y modo «tiras por Arduino» (opcionales, apagados de fábrica).

## 2026-10-20 — Ecualizador, voz, campanadas, sensores opcionales, votacion, galeria y mas
- Ecualizador de 12 columnas y medidor de ruido (escenas nuevas).
- Mensajes de voz: desde el movil, con el microfono del arbol o la perilla, y hablar en vivo (necesita https).
- Campanadas a la hora en punto con sonido configurable, saludo al detectar movimiento.
- Sensores opcionales apagados de fabrica: DHT11/22, reloj TinyRTC, PIR, perilla KY-040/HW-040.
- Dia y noche en la villa, clima real, votacion de invitados con QR, juego Simon, galeria de la comunidad, letras sincronizadas, estadisticas y copia semanal.
- Arreglos: la punta ya no brilla de mas, rayos con destellos, fuente y cometas usan todo el arbol, ledFlip.

## 2026-10-19 — Guirnalda con los colores de la paleta y arreglos de memoria
- La guirnalda de luces de la página usa los colores de la paleta elegida (clásica, aurora, hielo, dulce, dorado).
- Arregla una fuga de memoria (50-90 KB) en cada aviso de Telegram, descarga de música o búsqueda de versión.
- Actualización sin cable desde este repositorio (Sistema → Actualizar el programa).
- Micrófono MAX9814 opcional, Home Assistant (MQTT), fechas especiales, pestaña Shows con línea de tiempo, manual en /manual, mesa de trabajo 3D avanzada.


# Examen Práctico Montacargas
![Examen Practico _ Montacargas _ Guido Santillan DIV D](https://github.com/flowk1/Proyectos-SPD-1-Cuatrimestre/assets/93514202/45e0b476-2e6f-4ce5-9334-2ffad6b36fc2)

## Integrantes
Guido Santillán

## 🤖 Link al proyecto
https://www.tinkercad.com/things/kkw93x8KAki-examen-practico-montacargas-guido-santillan-div-d/editel?sharecode=3B3U0pQSD9YY-hiT9PTjVAYmOTdxSSodXfIxuyUbW5M

## Descripción del Proyecto

El siguiente código implementa un sistema de control para un montacargas utilizando un Arduino. El montacargas cuenta con un Display de 7 segmentos para mostrar el número actual del piso y dos LEDS (verde y rojo) para indicar si esta en funcionamiento o no.Para que el montacargas pueda realizar alguna acción se utilizan tres botones que suben,pausan o bajan.

## Código y Funcionamiento
El código implementa un sistema de control para un montacargas utilizando un Arduino. El montacargas se puede controlar mediante tres botones: el botón de subir `(BOTON_ARRIBA)`, el botón de pausa `(BOTON_PAUSA)` y el botón de bajar `(BOTON_ABAJO)`.

Al encender el Arduino, se configuran los pines correspondientes a los botones, LEDS y el Display. Luego, en el bucle principal ,el LED rojo se enciende y se llama a las funciones BotonSubir() y BotonBajar() para verificar si se ha solicitado subir o bajar el montacargas.

La función `BotonSubir()` se encarga de comprobar si el botón de subir ha sido presionado. Si es así, se activa la bandera de subir `(flagSubir)` y se realiza un bucle desde el valor actual del contador hasta 9. Durante cada iteración, se enciende el LED verde, se muestra el número de piso actual en el display y se verifica si se ha presionado el botón de pausa `(BotonPausar(11))` para romper el bucle.

La función `BotonPausar(int valorBreak)` se encarga de comprobar si el botón de pausa ha sido presionado. Si es así, se activa la bandera de pausa `(flagPausar)`. Durante la pausa, se muestra el número de piso actual en el display y se establece el valor del contador según el parámetro valorBreak. Esto permite que, al retomar la ejecución de `BotonSubir()` o `BotonBajar()`, se rompa la iteración en el valor adecuado y se continúe el movimiento del montacargas.

La función `BotonBajar()` funciona de manera similar a `BotonSubir()`, pero en este caso verifica si se ha presionado el botón de bajar. Si es así, se activa la bandera de bajar `(flagBajar)` y se realiza un bucle desde el valor actual del contador hasta 0. Durante cada iteración, se enciende el LED verde, se muestra el número de piso actual en el display y se verifica si se ha presionado el botón de pausa `(BotonPausar(-11))` para romper el bucle.

## Configuracion de los pines 

- LEDS:
  - LED_VERDE: Pin 2
  - LED_ROJO: Pin 3

- DISPLAY:
  - DISPLAY_B: Pin 10
  - DISPLAY_A: Pin 9
  - DISPLAY_F: Pin 8
  - DISPLAY_G: Pin 7
  - DISPLAY_C: Pin 6
  - DISPLAY_D: Pin 5
  - DISPLAY_E: Pin 4

- BOTONES:
  - BOTON_ABAJO: Pin 13
  - BOTON_PAUSA: Pin 12
  - BOTON_ARRIBA: Pin 11

## Variables

- `botonSubirEstado`, `botonPausarEstado`, `botonBajarEstado`: almacenan el estado de los botones (presionado o no).
- `contador`: lleva la cuenta del número de piso actual.
- `guardarValor`: guarda el valor actual del contador para ser utilizado después de una pausa.
- `flagSubir`, `flagPausar`, `flagBajar`: indican si se ha solicitado subir, pausar o bajar el montacargas respectivamente.

## Funciones

### `setup()`

- Configura los modos de los pines: dos botones como entrada con resistencias pull-up internas,y uno sin resistencias internas, los LEDS y  el Display como salidas y  al final,la comunicación serial.

### `loop()`

- Enciende el LED rojo y llama a las funciones `BotonSubir()` y `BotonBajar()` en cada iteración.

### `mostrarDisplay()`

- Enciende los segmentos del display correspondientes al número de piso actual.

### `prenderDisplay()`

- Prende los leds necesarios del display para formar el número requerido.

### `apagarDisplay()`

- Apaga todos los segmentos del display.

### `BotonSubir()`

- Verifica si el botón de subir está presionado.
- Si se presiona, cambia el valor de la bandera a True y realiza un bucle desde el valor actual del contador hasta 9.
- Durante el bucle, enciende el LED verde, muestra el número de piso en el display y verifica si se presiona el botón de pausa para romper el bucle.

### `BotonPausar(int valorBreak)`

- Verifica si el botón de pausa está presionado.
- Si se presiona, activa la bandera de pausa.
- Durante la pausa, muestra el número de piso en el display y establece el valor del contador según el parámetro `valorBreak` para romper la iteración en `BotonSubir()` o `BotonBajar()`.

### `BotonBajar()`

- Verifica si el botón de bajar está presionado.
- Si se presiona, cambia el valor de la bandera a True y realiza un bucle desde el valor actual del contador hasta 0.
- Durante el bucle, enciende el LED verde, muestra el número de piso en el display y verifica si se presiona el botón de pausa para romper el bucle.

## Limitaciones
El boton que pausa el montacargas debe ser mantenido o presionado justo antes de que el display de 7 segmentos muestre el siguiente número,de lo contrario, no se podra pausar.

## Diagrama esquematico
![Sistema esquematico Guido Santillan](https://github.com/GuidoSantillan/Proyectos-SPD-1-Cuatrimestre/assets/93514202/fc16b900-03ee-4030-a6a8-944b30a00be4)


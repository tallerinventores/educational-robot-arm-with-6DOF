# Educational Robot Arm with 6DOF #

> Robot arm w/ 6DOF for educational use

* * *

## Resumen ##

Brazo robótico con seis grados de libertad para uso en entornos educativos. El
brazo ha sido desarrollado y optimizado para impresión 3D y pensando en su bajo
coste y facilidad de montaje y uso. Es personalizable al poder aumentar o
disminuir los grados de libertad, del mismo modo que permite controlarse desde
diferentes plataformas.

## Instalación ##

En esta sección se cubre la instalación de software y hardware para el montaje
recomendado, mediante [Scratch](https://scratch.mit.edu/) y
[Arduino](http://www.arduino.cc/).

### Requerimientos de software ###

Para poder usar Scratch (v2.0 online) con Arduino, es necesario
(s2a_fm)[https://github.com/MrYsLab/s2a_fm] una extensión de Scratch para
comunicarse con Arduino. Para generar los archivos aptos para la impresora 3D
desde los archivos `.stl` será necesario adicionalmente un software para esta
función, como puede ser (Slic3r)[http://slic3r.org/].

Ver los requerimientos de mencionados programas previamente.

### Requerimientos de hardware ###

Será necesario para su montaje y uso una fuente de alimentación que proporcione
7.5W a 5V, un Arduino Uno o equivalente, seis servomotores tipo 9g con sus
correspondientes accesorios (tornillos y cuernos). El brazo está optimizado para
usar los servos **TowerPro SG90**.

## Uso ##

Instrucciones de montaje y puesta en marcha.

### Montaje del brazo robótico ###

1.  Imprimir una unidad de los archivos `feet.stl`, `grip.stl`, `plate.stl`,
    `wrist`, `rest.stl`, `axle.stl`, `left_jaw.stl` and `right_jaw.stl`.
    Imprimir dos unidades de `arm.stl`. Imprimir cinco unidades de
    `fastener.stl` y `clip.stl`. Puede ser necesario repasar las piezas impresas
    con el fin de eliminar rebabas.  
2.  Presentar la base del brazo (_feet_) en un tablero y atornillarlo al mismo
    con cuatro tornillos para madera.  
3.  Colocar un servo (sin cuerno) en la base, haciéndo coincidir el eje del
    mismo con el centro de la base y atornillarlo a la misma con los tornillos
    de montaje del servo.  
4.  Poner el cuerno del servo sobre la huella con su forma en la parte inferior
    del plato (_grip_), considerando que el eje estará en hacia abajo.  
5.  Insertar el plato (_plate_) en la pieza anterior, asegurando que el cuerno
    encaja en su posición.  
6.  Comprobar que una vez colocado el conjunto del plato sobre el servo, éste
    realiza el giro de la forma deseada. En ese momento se puede atornillar el
    servo al cuerno con el tornillo provisto por el servo.  
7.  Fijar el siguiente servo con dos tornillos en la parte superior del plato,
    de forma que quede el eje centrado con respecto al plato.  
8.  Del primer tramo del brazo (_arm_), hacer coincidir el orificio destinado
    para el cuerno del servo en el eje del mismo mientras que se inserta el otro
    extremo en el saliente del plato.  
9.  Asegurar el brazo en esta posición usando un pasador (_fastener_ y _clip_),
    insertando el primero desde fuera hacia dentro, y retenerlo aquí con el
    segundo.  
10. Encastrar el cuerno en el brazo y asegurar que el servo es capaz de realizar
    giro completo de un extremo al otro. Entonces atornillarlo al servo.  
11. Atornillar un servo en el extremo del tramo del brazo recién montado, con el
    eje lo más distante a la base.  
12. Repetir los pasos ocho al once para el siguiente tramos de brazo (_arm_),
    estándo este montado rotado con respecto al anterior.   
13. De la misma manera, poner el último tramo (_wrist_) en la parte superior del
    brazo, también rotado con respecto al tramo intermedio.  
14. Introducir el servo del último tramo de forma que el eje del mismo quede
    centrado y atornillarlo.  
15. Hacer coincidir los dos orificios del último tramo montado con los
    respectivos del asiento (_rest_) y fijarlos. El grande mediante pasador como
    anteriormente y el pequeño con un alambre y doblándolo después. Un clip para
    papel es perfecto para esta función. Cortar el sobrante una vez doblado en
    los extremos.  
16. Encajar las dos piezas que permitirán que rote la pinza (_gripper_ y
    _axle_). Insertar el cuerno del servo en la endidura central de los mismos.  
17. Presentar este bloque contra el asiento y asegurar que gira de la forma
    deseada antes de atornillar el cuerno al servo.  
18. Montar el último servo en la parte más alta del brazo, con el eje hacia el
    centro. Atornillarlo por la parte externa.  
19. Con el cuerno del servo dentro de la mitad derecha de la pinza
    (_right\_jaw_), insertarlo en el eje del servo correspondiente y asegurar
    que realiza el giro necesario. Acto seguido atornillarlo.  
20. Colocar la otra mitad de pinza (_left\_jaw_), engranarla con la primera de
    forma que realicen el cierre en el centro. Fijarlo al cuerpo del brazo con
    un pasador.   
21. Realizar una correcta gestión de cableado para asegurar que todos llegan
    hasta la base sin impedir el movimiento de cada tramo, ni que son aplastado
    por los mismos. Puede ser necesario extender algunos de ellos.

### Conexión eléctrica ###

Todas las alimentaciones de los servomotores van en paralelo y a la fuente de
alimentación. Las señales de control de los servos van a Arduino, usando las
conexiones del dos al siete para los servos de la pinza a la base,
respectivamente y por orden. La masa del Arduino y de la fuente de alimentación
ha de ser compartida. Conectar el Arduino a un puerto USB libre del ordenador a
usar.

### Firmware ###

El Arduino deberá tener cargado el firmware Firmata (incluido con Arduino IDE
bajo en nombre de `StandardFirmata`).

### Software ###

Con el Arduino conectado al ordenador, lanzar s2a_fm con el nombre del puerto
donde realizar la comunicación con Arduino. Por ejemplo:

        python s2a_fm.py /dev/ttyACM0

Abrir Scratch y cargar el proyecto `educational-robot-arm-with-6DOF.sb2`, una
vez hecho, se podrá ver en la interfaz gráfica los posibles movimientos del
brazo en forma de flechas para dichas órdenes. Se presentan dos formas de mover
el brazo:

-   Semiautomática.  
-   Manual.

Para conmutar entre ellos se usa el botón situado en la esquina superior
derecha, que al ser pulsado mostrará las opciones `STEP`, `BIG STEP`, `FULL` y
`MANUAL`. Las tres primeras son semiautomáticas, mientras que la última permite
controlar el brazo robótico manualmente.

En semiautomático, es tan sencillo como pulsar la flecha correspondiente al
tramo y dirección deseado para realizar un movimiento angular de tantos grados
como esté seleccionado.

En manual, ha de seleccionarse el tramo a mover, después seleccionar el número
de grados a mover dicho tramo y deseleccionar el tramo para efectuar el
movimiento.

La interfaz gráfica incluye los límites físicos del brazo para prevenir la
rotación de los servos más allá de estos.

### Bugs ###

Se han observado los siguientes problemas:

-   Las dos partes de la pinza tienen cierta holgura, eso provoca que no se
    cierren alineadas.  
-   El brazo totalmente extendido en horizontal presenta demasiada carga para
    los servos más cercanos a la base.  
-   El software de control provoca al inicio movimientos extraños.  
-   En determinados momentos hay servos que se deshabilitan sin razón aparente.
    (Problema de PyMata?).  
-   Por protocolo de Firmata, es necesario un pequeño tiempo entre órdenes para
    asegurar que son recibidas y procesadas. (Implementado).

## Enlaces externos ##

Este proyecto también está presente en:

-   [Scratch](https://scratch.mit.edu/projects/65804696/).  
-   [Thingiverse](http://www.thingiverse.com/thing:436096).

## Créditos ##

Proyecto realizado por Taller de Inventores 2015, representado por:

-   kwendenarmo <kwendenarmo@akornsys-rdi.net>

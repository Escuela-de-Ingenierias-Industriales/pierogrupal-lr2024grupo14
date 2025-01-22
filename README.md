# PIERO - Robot Móvil Autónomo DIY
---
## Índice
1. [Presentación](#presentación)
2. [Introducción](#introducción)
3. [Estudio de las Partes del Robot PIERO: Dispositivos y Cableado](#estudio-de-las-partes-del-robot-PIERO-dispositivos-y-cableado)
    - [Componentes Principales](#componentes-principales-del-robot-PIERO)
    - [Cableado del Robot PIERO](#cableado-del-robot-PIERO)
4. [Interconexionado](#interconexionado)
5. [Estudio de la Programación IDE del Arduino Mega](#estudio-de-la-programación-ide-del-arduino-mega)
    - [Función ISR](#función-isr)
    - [Creación de Interrupciones en Arduino](#creación-de-interrupciones-en-arduino)
6. [Estudios Previos para el Desarrollo del Código](#estudios-previos-para-el-desarrollo-del-código)
    - [Estudio del Arduino Mega 2560 para su Programación con Simulink](#estudio-del-arduino-mega-2560-para-su-programación-con-simulink)
    - [Programación en Arduino mediante MATLAB y Simulink](#programación-en-arduino-mediante-matlab-y-simulink)
7. [Desarrollo del Código](#desarrollo-del-código)
    - [Programa General del PIERO](#programa-general-del-PIERO)
    - [Trayectoria](#trayectoria)
    - [Sistema Anticolisión](#sistema-anticolisión)
    - [Control de Velocidad](#control-velocidad)
    - [Odometría](#odometría)
    - [Bluetooth Total](#bluetooth-total)
8. [Resultados Prácticos](#resultados-prácticos)
   - [Prueba de evitar colisiones](#prueba-de-evitar-colisiones)
   - [Prueba Anticaída](#prueba-anticaída)
   - [Prueba de seguimiento de trayectoria](#prueba-de-seguimiento-de-trayectoria)
   - [Prueba avanzar 10 baldosas](#prueba_avanzar_10_baldosas)
   - [Prueba trayectoria circular](#prueba_trayectoria_circular)
9. [Conclusiones](#conclusiones)
10. [Autoevaluación](#autoevaluación)
<br><br>
## Presentación
  
Somos el grupo 14 de la asignatura de Laboratorio de Robótica 2024/25 formado por [Iván Calvo](https://github.com/IvanCS-Chenfu), [Lucía Ortiz](https://github.com/IvanCS-Chenfu) y [Jorge Espiau](https://github.com/JorgeEspiau). Como parte de este curso, se nos ha asignado el desarrollo de un robot móvil llamado PIERO. Este proyecto combina diseño, montaje y programación con el fin de crear un dispositivo capaz de desplazarse de manera autónoma y evitar obstáculos. A modo de adelanto, la siguiente imagen muestra el resultado final nuestro proyecto, un arduo trabajo lleno de inconvenientes y obstáculos en el que hemos puesto casi tres meses de empeño.

<p align="center">
	<img src="https://github.com/user-attachments/assets/6d67505c-bbe4-4150-a839-e79d018be690" alt="Componentes del grupo 14" width="400"/>

<p align="center">
	<img src="https://github.com/user-attachments/assets/dfeb176c-7327-4ce5-afa6-8ceadfbb84b2" alt="Nuestro PIERO" width="400"/> 



https://github.com/user-attachments/assets/06fce31a-1cc8-4662-9828-db3589afb73d



<br><br>
## Introducción
En esta asignatura se nos planteó el desafío de construir y programar un robot móvil llamado PIERO, diseñado para desplazarse de manera autónoma y evitar obstáculos. Este proyecto busca aplicar conceptos de robótica, integración de hardware y desarrollo de software en un entorno práctico.
PIERO es un robot de accionamiento diferencial con dos motores electricos, una rueda caster y sensores que le permiten interpretar el entorno. Nuestra tarea consistió en caracterizar sus componentes, desarrollar el software necesario para que pueda seguir consignas de velocidad lineal y angular, y probar su capacidad para resolver un reto concreto: partiendo de un punto determinado, salir del laboratorio evitando obstáculos.
<br><br>


## Estudio de las Partes del Robot PIERO: Dispositivos y Cableado

  En esta etapa inicial de la investigación sobre el robot PIERO, nos hemos dedicado a explorar de manera detallada los elementos fundamentales y la instalación del cableado requerido para ensamblar y operar el robot. Cada uno de los dispositivos que conforman al PIERO es de suma para el correcto movimiento e interacción del éste con su entorno.

### Componentes Principales del Robot PIERO

<p align="center">
	<img src="https://github.com/user-attachments/assets/fc06e6f1-2265-43b0-b6dc-e3e6b4f56709" alt="motor con rueda" width="200"/>
</p>
<p align="center">
	<img src="https://cdn.discordapp.com/attachments/1250034242201849910/1323363479423291422/image.png?ex=67743dc8&is=6772ec48&hm=749dc1c1722ca175fafe8c41f6b874ba4d989b38ae63a0caf0af5c29c0726b17&" alt="lca" width="300"/>
</p>

- **Motores con encoders y ruedas (x2)**: El motor DC funciona con voltajes entre 5V a 12V, el torque y velocidad de salida varían de acuerdo al voltaje aplicado. Al trabajar con el voltaje nominal de 12V, la velocidad angular de salida será de 170 RPM (revoluciones por minuto). El dispositivo está compuesto de tres partes: el motor DC, la caja reductora y el encoder de cuadratura. La caja reductora de metal cumple la función de reducir la velocidad de entrada y aumentar el torque de salida. El encoder sirve como un sensor de velocidad y sentido de giro, funciona utilizando dos sensores de efecto Hall. El voltaje de alimentación del encoder es de 3.3V a 5V en corriente continua(DC). Estos motores son fundamentales para el desplazamiento del robot y conforman la base de su sistema de movimiento, los enconders que vienen con estos motores son esenciales para ubicar de forma precisa el robot en tiempo real.  Además contamos con una rueda caster para estabilizar su base. <br><br>

<p align="center">
	<img src="https://github.com/user-attachments/assets/0c6cc2c1-5139-4d9e-a8e4-08744dde88be" alt="lca1010a" width="200"/>
</p>

- **Arduino Mega 2560**:  Es el cerebro del robot. La característica más destacada del Arduino Mega 2560 es su habilidad para controlar numerosas entradas y salidas gracias al gran abanico de pines con los que cuenta. Esto posibilita la conexión sin dificultades de múltiples sensores y actuadores. El arduino se puede alimentar con una fuente de 12V.<br><br>

<p align="center">
<img src="https://github.com/user-attachments/assets/97a91e1a-5f60-451e-8ca8-12479732a0c2" alt="driver" width="200"/>
</p>

- **Driver de Potencia L298N**: Este elemento tiene la responsabilidad de manejar los motores. Actúa como un puente H que proporciona control de velocidad y rotación del motor mediante PWM (modulación de ancho de pulso).Este driver permite regular la salida tanto para dispositivos que requieran una entrada de 12V como aquellos que necesiten 5V. <br><br>

<p align="center">
<img src="https://github.com/user-attachments/assets/48ce2882-181b-4222-862f-62d08f6ef41d" alt="sensor ultrasonidos" width="200"/>
</p>

- **Sensores de Distancia Ultrasonidos**: Los sensores de distancia son esenciales para detectar obstáculos y prevenir colisiones durante el desplazamiento del robot. Los sensores de ultrasonido ofrecen una cobertura amplia pero poca precisión.<br><br>

- **Interruptor**.

<p align="center">
<img src="https://github.com/user-attachments/assets/630676de-b5b8-4d26-be37-59a526c30c9f" alt="pack baterías" width="200"/>
</p>
<p align="center">
<img src="https://github.com/user-attachments/assets/eba3c2f0-3491-45df-99ed-b09ac7372d22" alt="Opera Instantánea_2024-12-30_190246_www google com" width="200"/>
</p>

- **Baterías y Porta Baterías**: Para el suministro de energía, se emplean baterías de 3,7V y 3400 mAh del tipo 18650, las cuales son recargables y presentan una adecuada combinación entre capacidad y tamaño. El soporte de baterías facilita una instalación segura y organizada, conectándose al Arduino mediante un interruptor para regular el encendido y apagado del sistema.<br><br>

<p align="center">
<img src="https://github.com/user-attachments/assets/3a20e2b5-511a-4cbd-ba71-4c37b3aeb141" alt="Bluetooth" width="200"/>
</p>
- **Placa Bluetooth**: Esta es la funcionalidad que hemos añadido al proyecto.<br><br>

<p align="center">
<img src="https://github.com/user-attachments/assets/1efdb843-4632-4274-a111-10ac87f57a30" alt="voltímetro" width="200"/>
</p>

- **Indicador de voltaje**: Es un elemento pequeño pero imprescindible para supervisar la descarga de la batería en tiempo real. <br><br>

<p align="center">
<img src="https://github.com/user-attachments/assets/065ba332-55cf-44b6-8df2-2efa3bf48f66" alt="image" width="200"/>
</p>

- **Sensor de voltaje**: Este módulo se basa en los principios de diseño de un divisor resistivo, puede reducir el voltaje de la conexión del terminal de entrada cinco veces, voltaje de entrada analógica de hasta 5V, entonces el voltaje de entrada del módulo de detección de voltaje no puede ser mayor que 5V × 5 = 25V (3,3 V si se utiliza el sistema, El voltaje de entrada no excede 3.3Vx5 = 16,5 V). Debido a que los chips AVR se utilizan en 10 AD, la resolución de simulación de este módulo es de 0,00489 V (5V / 1023), por lo que el módulo de detección de voltaje detecta que el voltaje mínimo de entrada es 0,00489 V × 5 = 0,02445 V. <br><br>

<p align="center">
<img src="https://github.com/user-attachments/assets/2c65bff1-1a82-42d9-8c63-773507afdd6f" alt="cables dupont" width="200"/>
</p>

- **Cables Du Pont y Conexiones**: El cableado correcto es esencial en el proceso de montaje. El uso de cables Du Pont hace que sea más fácil conectar los diferentes módulos al Arduino. Principalmente se han utilizado cables Macho-Hembra<br> <br>

## Cableado del Robot PIERO
 El cableado del robot es una de las partes más cruciales que demanda mayor concentración. Garantizar la adecuada conexión de las piezas es clave para el correcto funcionamiento del robot. A continuación, se resaltan algunos puntos clave:

- **Conexión de los Motores al Driver L298N**: Los motores se enlazan al controlador a través de las clavijas de salida del motor del L298N. Este controlador también se conecta a los pines de control del Arduino (generalmente pines digitales).Asimismo, es necesario enlazar el módulo de alimentación para asegurar que los motores cuenten con la cantidad adecuada de Esquivando Cenergía.

- **Conexión de Sensores**: Los sensores de ultrasonido son conectados a los pines digitales del Arduino. Configurar adecuadamente los pines de entrada y salida y programar el Arduino de forma eficiente es crucial para la lectura de datos.

- **Baterías y Sistema de Alimentación**: Se conectan las baterías al Arduino y a los motores mediante un sistema de distribución de energía que cuenta con un interruptor y un voltímetro. Esto no solo hace más sencillo encender y apagar al robot, sino que también permite vigilar constantemente el estado de la batería.

- **Sensor de voltaje**: El pin de salida debe de estar conectado a un pin analogico del Arduino.

Una vez entendidas las funciones de cada componente y habiendo estudiado su conexionado nos dispusimos a montarlo por nuestra cuenta sobre un túper de plástico:

<p align="center">
<img src="https://github.com/user-attachments/assets/214a9444-8e65-4567-8313-7f9e135281a2" alt="Foto 1" width="300"/>
</p>
<br><br>

Lo primero fue idear donde colocar cada dispositivo. Los motores y la caster fueron los primeros en añadirse. Para la rueda caster utilizamos tornillos de diámetro 4 mm y para las ruedas motoras, debido a su disposición, elegimos poner bridas que posteriormente se cortarian.

<p align="center">
<img src="https://github.com/user-attachments/assets/4ba2bad3-c811-44bf-ad49-5e47cd3fb5cc" alt="Foto 1.5" width="300"/>
<img src="https://github.com/user-attachments/assets/b4aa51e1-3f78-446d-ae9c-2cfc883ec827" alt="Foto 2" width="300"/>
</p>
<br><br>

Ya con los motores colocados, lo siguiente fue poner la placa Arduino, el portabaterías, el driver y la protoboard donde mejor se pudieran manejar, aun así, en la imagen se puede apreciar que estaban de forma temporal para poder probar distintos lugares y ver cómo se manejaban en estos.

<p align="center">
<img src="https://github.com/user-attachments/assets/44ea9486-413e-4977-b52c-203c5a792e92" alt="Foto 3" width="400"/>
</p>
<br><br>

El siguiente paso fue idear donde sería mejor poner los sensores de ultrasonidos y también ponerlos de forma temporal con alambres.

<p align="center">
<img src="https://github.com/user-attachments/assets/416c5a5b-8d32-471c-8732-158616a87031" alt="Foto 4" width="400"/>
</p>
<br><br>

Y por último, antes de pasar al cableado, fue distribuir y poner los distintos leds que usaríamos. 

<p align="center">
<img src="https://github.com/user-attachments/assets/8c412997-c6ba-48c8-815f-42cee2f8c519" alt="Foto 5" width="400"/>
</p>
<br><br>

## Interconexionado.

Para esta parte empezaos haciendo un Excel que nos serviría de guía para saber quéƒ pines del Arduino ya estábamos usando y para que se utilizaban. Este Excel se tuvo que cambiar a lo largo del proyecto un par de veces debido a fallos del propio Arduino.
<br>
<p align="center">
	<img src="https://github.com/user-attachments/assets/e321d71c-54ed-425e-883b-f56e3cb35bd0" alt="pinouts" width="800"/>
</p>

Así, pudimos empezar con el conexionado.

<p align="center">
<img src="https://github.com/user-attachments/assets/a553416c-72b7-4060-9b21-a6164f28e597" alt="Conexionado 1" width="300"/>
<img src="https://github.com/user-attachments/assets/b4d016d5-d037-4014-aaea-2c029640bd24" alt="Conexionado 2" width="300"/>
<img src="https://github.com/user-attachments/assets/ad38c3d4-b7dd-4d28-aa11-24efd3594903" alt="Conexionado 3" width="300"/>
</p>
<br><br>

Aunque, a decir verdad, esta fue la parte en la que tuvimos más problemas, el mayor causante de estos fueron los cable que venían por defecto en los componentes que pedimos, estos cables eran muy frágiles y con mala conducción, es por eso que tuvimos que quitar algunos y sustituirlos por otros cables de nuestra elección, empalmar unos cables con otros e incluso utilizar celo para que no se desconectaran.

<p align="center">
<img src="https://github.com/user-attachments/assets/92601a6c-eba4-436c-9877-da2651aa6569" alt="Conexionado 4" width="300"/>
</p>
<br><br>

Una vez llegaron los nuevos cables ya pudimos soldarlos y empalmarlos correctamente. Debido a la mala conexión de la protoboard de la que disponiamos no nos arriesgamos a meter 12V y  5V por los posibles daños al crearse vibraciones producidas por el movimiento del robot. Para ello, decidimos comprar PCBs de circuito impreso de doble cara para poder diseñarla a nuestro gusto y poder conectar los 12V y la tierra correspondiente.

<p align="center">
<img src="https://github.com/user-attachments/assets/b89ed0cb-19db-45fa-9c05-f4854520a7d9" alt="Conexionado 5" width="300"/>
<img src="https://github.com/user-attachments/assets/52d61136-9872-4759-a25c-204c8c8fa5d7" alt="Conexionado 6" width="300"/>
</p>
<br><br>

Ya con estos cables conseguimos un prototipo al PIERO que buscábamos, pero todavía nos daba fallos en conexiones y por eso tuvimos un estancamiento largo en esta parte.

<p align="center">
<img src="https://github.com/user-attachments/assets/8834bb77-62a1-4729-9757-7464b78d31ef" alt="Conexionado 7" width="300"/>
</p>
<br><br>

En las pruebas con el código, que pudimos ver que una de las ruedas no giraba, y que no era fallo del código. Después de medir voltaje en los pines del Arduino para ver que todo funcionara con normalidad y que se correspondía con lo programado, nos dimos cuenta de que teníamos unos pines estropeados que proporcionaban un voltaje ficticio. Es por eso que desconectamos todo y lo volvimos a rehacer, cambiando parte del pinout (la foto de arriba del pinout es la actualizad).

<p align="center">
<img src="https://github.com/user-attachments/assets/f596e851-56ee-4958-b1ab-bdf04dd6aa27" alt="Conexionado 8" width="300"/>
<img src="https://github.com/user-attachments/assets/56b57d6a-1880-47e4-964d-289ad4dc6a52" alt="Conexionado 9" width="300"/>
<img src="https://github.com/user-attachments/assets/754d84b9-d4f4-48e0-8c8a-5bdae4b4c528" alt="Conexionado 10" width="300"/>
</p>
<br><br>

Y al fin conseguimos que todo estuviera bien cableado.

<p align="center">
<img src="https://github.com/user-attachments/assets/c16be8fc-df80-4a7a-8ead-c76eff1c19ca" alt="Conexionado 11" width="300"/>
</p>
<br><br>

***

# Estudio de la programación IDE del Arduino Mega

 Arduino dispone de dos tipos de eventos en los que definir interrupciones. Por un lado tenemos las interrupciones de timers. Por otro lado, tenemos las interrupciones de hardware, que responden a eventos ocurridos en ciertos pines físicos.

Dentro de las interrupciones de hardware, que son las que nos ocupan en esta entrada, Arduino es capaz de detectar los siguientes eventos:

* `RISING`, ocurre en el flanco de subida de `LOW` a `HIGH`.
* `FALLING`, ocurre en el flanco de bajada de `HIGH` a `LOW `.
* `CHANGING`, ocurre cuando el pin cambia de estado (`rising` + `falling`)
* `LOW`, se ejecuta continuamente mientras está en estado `LOW`.

Los pines susceptibles de generar interrupciones varían en función del modelo de Arduino. El Arduino Mega 2560 dispone de 6 interrupciones, en los pines 2, 3, 21, 20, 19 y 18 respectivamente.

<p align="center">
<img src="https://github.com/user-attachments/assets/f010aa3b-ab0f-4f4c-bba4-5fd6604493bb" alt="Arduino-Mega-Pinout" width="700"/>
<img src="https://github.com/user-attachments/assets/7a1aa8af-6413-42d4-9da1-ab5a1161969c" alt="Captura de pantalla 2024-09-20 115055" width="300"/>
</p>

## Función ISR
La función asociada a una interrupción se denomina ISR (Interruption Service Routines) y, por definición, tiene que ser una función que no recibe nada y no devuelva nada.
Dos ISR no pueden ejecutarse de forma simultánea. En caso de dispararse otra interrupción mientras se ejecuta una ISR, la función ISR se ejecuta una a continuación de otra. Al diseñar una ISR debemos mantener el menor tiempo de ejecución posible.
Frecuentemente la función de la ISR se limitará a activar un flag, incrementar un contador, o modificar una variable. Esta modificación será atendida posteriormente en el hilo principal, cuando sea oportuno.

Para poder modificar una variable externa a la ISR dentro de la misma debemos declararla como “volatile”. El indicador “volatile” indica al compilador que la variable tiene que ser consultada siempre antes de ser usada, dado que puede haber sido modificada de forma ajena al flujo normal del programa.

Las interrupciones tienen efectos en la medición del tiempo de Arduino, tanto fuera como dentro de la ISR, porque Arduino emplea interrupciones de tipo Timer para actualizar la medición del tiempo.
Durante la ejecución de una interrupción, Arduino no actualiza el valor de la función `millis` y `micros`.

Dentro de la ISR el resto de interrupciones están desactivadas. Esto supone:
* La función `millis()` no actualiza su valor, por lo que no podemos utilizarla para medir el tiempo dentro de la ISR. 
* Como consecuencia, la función `delay()` no funciona, ya que basa su funcionamiento en la función `millis()`.
* La función `micros()` actualiza su valor dentro de una ISR, pero empieza a dar mediciones de tiempo inexactas pasado el rango de 500us.
* En consecuencia, la función `delayMicroseconds()` funciona en ese rango de tiempo, aunque debemos evitar su uso porque no deberíamos introducir esperas dentro de una ISR.

## Creación de interrupciones en Arduino
Para definir una interrupción en Arduino usamos la función:
`attachInterrupt(interrupt, ISR, mode);`

Donde interrupt es el número de la interrupción que estamos definiendo, ISR la función de callback asociada, y mode una de las opciones disponibles (FALLING, RISING, CHANGE y LOW).
No obstante, es más limpio emplear la función `digitalPinToInterrupt()`, que convierte un Pin a la interrupción equivalente.
`attachInterrupt(digitalPinToInterrupt(pin), ISR, mode);`

Otras funcionas interesantes para la gestión de interrupciones son:
* `DetachInterrupt(interrupt)`, anula la interrupción.
* `NoInterrupts()`, desactiva la ejecución de interrupciones hasta nueva orden.
* `Interrupts()`, reactiva las interrupciones.


## Estudios previos para el desarrollo del código
### Estudio del Arduino Mega 2560 para su programación con Simulink
#### Lectura, escritura y análisis de datos de los sensores de Arduino
El [paquete de soporte de MATLAB para Arduino](https://es.mathworks.com/hardware-support/arduino.html) permite escribir programas de MATLAB que leen y escriben datos en los dispositivos Arduino y otros dispositivos conectados, tales como Adafruit Motor Shield, I2C y SPI.

Ventajas del uso de MATLAB para la programación en Arduino:
* Lectura y escritura de datos de sensor de forma interactiva sin necesidad de esperar a la compilación del código
* [Análisis](https://es.mathworks.com/products/matlab/data-analysis.html) de los datos de sensor mediante miles de funciones prediseñadas para el procesamiento de señales, el [aprendizaje automático](https://es.mathworks.com/solutions/machine-learning.html), el [modelado matemático](https://es.mathworks.com/solutions/mathematical-modeling.html), etc.
* Visualización rápida de los datos gracias a la amplia gama de [tipos de gráficos](https://es.mathworks.com/products/matlab/plot-gallery.html) de MATLAB

Con Simulink Support Package for Arduino, puede desarrollar el algoritmo en Simulink y desplegar en Arduino con generación de código automática. Luego, el procesamiento se realiza en el dispositivo Arduino.

Ventajas del uso de Simulink para la programación en Arduino:

* [Desarrollo y simulación de los algoritmos en Simulink](https://es.mathworks.com/products/simulink.html) y uso de la generación automática de código para ejecutarlos en el dispositivo
* Incorporación de rutinas de procesamiento de señales, [diseño de control](https://es.mathworks.com/discovery/control-design-software.html), [lógica de estados](https://es.mathworks.com/products/stateflow.html) y otras rutinas avanzadas de matemáticas e ingenierí­a en los proyectos de hardware
* Ajuste y optimización interactivos de parámetros mientras el algoritmo se ejecuta en el dispositivo
* Modificación fácil de algoritmos para su ejecución en otras plataformas de hardware comerciales de bajo coste

<br><br>
### Programación en Arduino Mediante Matlab y Simulink
Para empezar a operar nuestro Arduino en el software de Matlab deberemos instalarnos dos paquetes de soporte. Para ello realizaremos los tres siguientes pasos:
1. Abriremos el software Matlab
2. Accederemos a “Home”  > "Adds-Ons" > "Get Adds-Ons"
3. Instalamos los dos siguientes Adds-Ons:

<p align="center">
<img src="https://github.com/user-attachments/assets/93e0f456-99da-4a42-b864-97f34a10600c" alt="imagen" width="1100"/>
</p>

 
Una vez instalados, separaremos la configuración de nuestro Arduino dependiendo de si utilizamos Matlab o Simulink.
Para establecer la conexión entre Matlab y nuestra placa deberemos poner el siguiente comando:

`a = arduino()`. Se utilizará si hemos conectado al ordenador un hardware Arduino oficial

`a = arduino('COM3','Uno')`. Se utilizara si el hardware no es oficial. “COM3” es el puerto del ordenador y “Uno” es el modelo del hardware.
 
<br><br>
### Simmulink
Para establecer la conexión entre Simulink y nuestra placa deberemos pulsar el botón “Model Configuration Parameters Button”
 
Una vez dentro, accedemos a la pestaña “Hardware Implementation” y rellenamos el hueco de “Hardware Board” con el nombre de nuestra placa. Además, debemos ajustar los baudios, todas las opciones a 115200.

Para simular nuestro proyecto en Simulink deberemos elegir el modo de simulación externo (para ejecutar nuestro programa en el hardware Arduino). Deberemos poner también el tiempo de simulación en infinito.
 
Para transferir nuestro código a la placa Arduino (evitando la necesidad de que la placa no tenga que estar siempre conectada a Simulink) hay que pulsar el botón de "Build, Deploy & start".
<p align="center">
<img src="https://github.com/user-attachments/assets/b7f81aff-8a07-4cd5-a936-d2518e8590bf" alt="imagen" width="300"/>
</p>
<br><br>



## Desarrollo del código.

---

Ya con los fundamentos sobre como usar las interrupciones, Matlab y simulink, empezamos a desarrollar todo el código necesario para lograr la navegación reactiva.
Al principio, lo primero que hicimos fueron las actividades del test de motores, LEDs y  sensores. 
Aunque hicimos algunas tareas para clase y unos cuantos códigos que están en el repositorio, nos centraremos únicamente en los que utilizamos finalmente en nuestro proyecto.

### Estudio de la plataforma robótica móvil PIERO y navegación reactiva básica en Simulink
Habiendo hecho previamente el estudio de la plataforma robótica móvil, hemos realizado un programa básico en el que nuestro PIERO va a girar cada vez que detecte un obstáculo. 

Al principio, se nos pedía una tarea en la que el PIERO evitase paredes sin tener controladores. Para ello había que meterle una velocidad cualquiera y que cuando detectase un obstáculo (una pared o similar), lo esquivase. Para ello hicimos el siguiente programa:
<p align="center">
<img src="https://github.com/user-attachments/assets/26aa7fc0-4800-4e28-b5b8-f4c048beea30" alt="Evita paredes"/>
</p>
<br>
Los subsistemas usados están explicados más adelante.
<br><br>

- Video Evita Paredes

https://github.com/user-attachments/assets/324cfe03-0829-4512-b191-3ab5e9f98cb4

<br>


Hablaremos ahora, de nuestro testTotal, un archivo que junta las librerias necesarias para, no solo hacer que el robot esquive obstaculos, sino para lograr que el robot siga una trayectoria esquivando los obstaculos necesarios. Además, hemos añadido dun componente bluetooth para que se pueda controlar el robot desde el movil.
Este test esta compuesto por cinco librerias, cada una de ellas contribuyendo con una funcion vital para el perfecto desempeño del PIERO.

<br><br>


- ### **Programa General del PIERO**

A continuación, explicaremos cada uno de los bloques que conforman nuestro código, todos ellos juntos, logran hacer que el robot tenga un control eficiente de su navegación reactiva, su velocidad y comunicación. 
Para unir estos subbloques y dar una idea general y completa del código, podemos dar la siguiente explicación del flujo: 

1. Entrada de Datos y Configuración:
El modelo comienza con las entradas generales del sistema, que incluyen:
- `Waypoints:` Representan la lista de coordenadas que el robot debe seguir.
- `Umbrales:` Parámetros para evitar colisiones y ajustar el comportamiento en función de la proximidad a obstáculos.
- `Señal de habilitación:` Activa el funcionamiento general del sistema.
Las cuales se pueden introducir o manualmente antes de cargar el código en el PIERO o por bluetooth desde el dispositivo móvil.

2. Bloques Principales:
El modelo está compuesto por varios bloques que trabajan de manera coordinada para cumplir los objetivos de navegación y control del robot:
	- Bluetooth_Total: Procesa la información recibida desde el módulo Bluetooth, permitiendo la comunicación entre el robot y un dispositivo externo. Es responsable de traducir los comandos en datos que el sistema pueda usar, como umbrales, velocidades y waypoints.
	- Trayectoria: Toma como entrada los waypoints, la posición actual del robot y los umbrales, y calcula la trayectoria óptima hacia el siguiente punto. Determina la velocidad y orientación necesarias para que el robot alcance cada waypoint en secuencia.
	- Control_Velocidad: Ajusta la velocidad de las ruedas del robot para que siga las instrucciones definidas por el bloque de trayectoria. Utiliza controladores internos para garantizar que la velocidad sea precisa y adaptada a las necesidades del robot.
	- Odometría: A partir de la velocidad de las ruedas, calcula la posición y orientación actual del robot. Proporciona información clave para el bloque de trayectoria y para cualquier monitoreo del robot.
	- Salida de Motores: Convierte las instrucciones generadas por el bloque de control de velocidad en señales PWM que controlan directamente los motores del robot.

Con todo esto conseguimos que nuestro robot al meterle una trayectoria, la siga y esquive los obstaculos que se le crucen por el camino de la manera más precisa posible. 

<p align="center">
<img src="https://github.com/user-attachments/assets/7f174f3d-8dc0-471f-b393-7529585dd427" alt="Total"/>
</p>
<br><br>



- ### Trayectoria

<p align="center">
<img src="https://github.com/user-attachments/assets/fcb39e4f-f192-4c5e-98fd-d10a6b97cf25" alt="Trayectoria"/>
</p>
<br><br>


El bloque "Trayectoria" se encarga de calcular y supervisar el movimiento del robot entre una serie de puntos de paso o waypoints. 
Su objetivo principal es determinar la velocidad y orientación necesarias para que el robot se dirija al siguiente waypoint en la secuencia, hasta que se alcancen todos ellos. 
Este bloque juega un papel crucial en la navegación del robot, ya que traduce la información sobre la posición actual del robot y los objetivos definidos en una trayectoria eficiente y controlada. Además, los switches sirven para controlar el contador `i` del bloque de código `Matlab Function`, y así poder reiniciar los waypoints.

Para lograr este objetivo, el bloque recibe las siguientes entradas:

- `Waypoints`: Una matriz donde cada fila representa las coordenadas(x,y) de un waypoint al que el robot debe dirigirse.
- `Umbral_Trajectoria`: Una distancia umbral que determina cuándo el robot se considera lo suficientemente cerca de un waypoint para avanzar al siguiente.
- `Pose`: La posición actual del robot, especificada en un vector [x,y].
- `V_in`: La velocidad de entrada actual del robot.
- `i_act`: El índice del waypoint actual que está siguiendo el robot.

Con esta información, el bloque calcula y actualiza las siguientes salidas:

- `V_out`: La velocidad del robot después de procesar la trayectoria.
- `o`: La orientación del robot, calculada para dirigirse al siguiente waypoint.
- `i_prox`: El índice actualizado del siguiente waypoint al que debe dirigirse el robot.

El funcionamiento interno del bloque toma como punto de partida la posición actual del robot (`Pose`) y el siguiente waypoint en la lista (`Waypoints[iprox]`). 
Primero, se calcula la distancia entre ambas posiciones mediante la fórmula euclidiana d = √((x_2 - x_1)^2 + (y_2 - y_1)^2). 
Con esta distancia, se evalúa si el robot se encuentra lo suficientemente cerca del waypoint (es decir, si está dentro del umbral definido por `Umbral_Trajectoria`). 
Si la distancia supera el umbral, el bloque calcula la orientación necesaria para que el robot avance hacia el waypoint y ajusta la velocidad de salida (`Vout`) en función de la velocidad de entrada (`Vin`). 

Cuando el robot alcanza el waypoint (distancia menor o igual al umbral), el índice del waypoint actual (`iprox`) se actualiza para dirigir al robot hacia el siguiente objetivo en la lista. 
Si no quedan más waypoints por alcanzar, el bloque detiene el movimiento del robot, asignando cero a la velocidad y la orientación.
Dentro del bloque, el cálculo de las transformaciones de las entradas a las salidas se realiza principalmente a través de una función MATLAB. 
Esta función implementa la lógica de navegación en varios pasos clave. Primero, se evalúa si aún quedan waypoints disponibles en la lista. 
Luego, utiliza la posición actual del robot y las coordenadas del siguiente waypoint para calcular la distancia entre ambos mediante la fórmula euclidiana. 
Basándose en esta distancia, la función determina si el robot debe continuar avanzando hacia el waypoint actual o si debe pasar al siguiente. 
Además, calcula la orientación requerida mediante la función `atan2`, que asegura un ángulo correcto entre las posiciones del robot y el waypoint. 
Finalmente, actualiza las salidas `Vout` y `o` para controlar el movimiento del robot, y ajusta `iprox` para garantizar que el robot siga avanzando correctamente por la trayectoria definida. 
Si no quedan más waypoints, la función garantiza que el robot se detenga, asignando cero a la velocidad y la orientación.

La función que hemos implementado es la siguiente:
<br>
<pre>
<code>
function [v_out,o,i_prox] = fcn(umbral_waypoint,waypoints,v_in,pose,i_act)

i_prox = i_act + 1;

x_pose = pose(1);
y_pose = pose(2);

% Si sigue habiendo waypoints -> Se mueve
if(size(waypoints,1) >= i_prox)
    x_waypoint = waypoints(i_prox,1);
    y_waypoint = waypoints(i_prox,2);
    
    dist = sqrt((x_waypoint-x_pose)^2+(y_waypoint-y_pose)^2);
   
    % Como atan2 da un ángulo entre pi y -pi, cuando el robot va hacia
    % atrás en x, hay problemas. Por eso todo esto.
    o = atan2(y_waypoint-y_pose,x_waypoint-x_pose);

    if (i_prox == 1 && x_waypoint < 0 && y_waypoint == 0)
        o_aux = -sign(o)*(2*pi+o);
        if(abs(o_aux-pose(3)) > pi/4)
            o = pi;
            v_out = 0;
        else
            o = o_aux;
            v_out = v_in;
        end
    else
        if (x_waypoint < waypoints(i_prox-1,1) && y_waypoint == waypoints(i_prox-1,2))
            o_aux = -sign(o)*(2*pi+o);
            if(abs(o_aux-pose(3)) > pi/4)
                o = pi;
                v_out = 0;
            else
                o = o_aux;
                v_out = v_in;
            end
        else
            v_out = v_in;
        end
    end

    % Si está lejos de waypoint -> Sigue yendo al mismo waypoint
    if (dist > umbral_waypoint)
       i_prox = i_prox - 1;
    end
    

% Si ya no hay mas waypoints -> se para el robot.
else
    v_out = 0;
    o = pose(3);
    i_prox = i_act;

end
</code>
</pre>

Para este bloque hemos calculado los valores del PID de la siguiente manera:
<p align="center">
<img src="https://github.com/user-attachments/assets/8a34d013-3cb8-402a-a59d-856227c1a4f4" alt="Cálcuo del PID de trayectoria"/>
</p>
<br><br>

Con el bloque de la odometría me da el ángulo que tiene el robot actualmente. Con esto, calculamos el error del ángulo. Con esto se calculan los valores del PID. Los subsistemas que se han implementado para estos están explicados en los siguientes apartados.

- Valores del PID
<p align="center">
<img src="https://github.com/user-attachments/assets/e5735ddd-83e2-46e7-a48a-7131c4b88731" alt="Valores del PID de trayectoria"/>
</p>
<br><br>



- ### Sistema Anticolisión

<p align="center">
<img src="https://github.com/user-attachments/assets/f77578b1-c9d7-4267-97ab-9dea3658d104" alt="sistema anticolisión"/>
</p>
<br>

El bloque "Sistema_Anticolision" es una parte clave del sistema de navegación del robot. 
Su propósito es garantizar que el robot pueda moverse de forma segura, reaccionando rápidamente a posibles colisiones o caídas. 
Este bloque ajusta la velocidad y la orientación del robot en tiempo real, basándose en los datos de los sensores y en ciertos umbrales predefinidos que indican riesgos.

Para cumplir este objetivo, el bloque "Sistema_Anticolision" recibe las siguientes entradas:

- `Velocidad`: La velocidad lineal actual del robot, que puede modificarse en función de las condiciones detectadas.
- `UmbralFrontal`: Distancia mínima al frente que, si se supera, se considera que hay riesgo de colisión frontal.
- `UmbralLateral`: Distancia mínima a los lados que, si se supera, indica riesgo de colisión lateral.
- `UmbralCaida`: Distancia mínima hacia abajo que, si se supera, identifica un posible riesgo de caída.

Con esta información, el bloque genera las siguientes salidas:

- `V (Velocidad Lineal)`: La velocidad lineal ajustada del robot tras procesar las condiciones de riesgo.
- `W (Velocidad Angular)`: La velocidad angular ajustada para modificar la orientación del robot y evitar colisiones o caídas.

El bloque "Sistema_Anticolision" está formado por varios subbloques que trabajan juntos para analizar las condiciones del entorno y tomar las decisiones necesarias:
<br>

#### Subbloque "Bits_Colision"
Este subbloque toma los datos de los sensores y los compara con los valores de los umbrales establecidos (`UmbralFrontal`,`UmbralLateral`,`UmbralCaida`). 
Básicamente, convierte las lecturas continuas de los sensores en señales binarias (0 o 1) que indican la presencia o ausencia de riesgo. Por ejemplo:

- Un valor `1` en `Collision Frontal` indica que la distancia medida por el sensor frontal es menor o igual al `UmbralFrontal`, es decir, hay un riesgo de colisión frontal.
- Un valor `0` indica que no hay riesgo de colisión en esa dirección.

De esta forma, las señales binarias son un resumen claro y directo del estado del entorno, lo que facilita la toma de decisiones en los siguientes subbloques.
<br>


- Imagen del subsistema bits_colisión
<p align="center">
<img src="https://github.com/user-attachments/assets/761fba19-e890-4d3d-b7a0-848b261fa46b" alt="bits_colisión"/>
</p>
<br>
 
- Valores del sensor de abajo
<p align="center">
<img src="https://github.com/user-attachments/assets/7618ce32-6dec-42e5-849b-a1515a1591f7" alt="sensor abajo"/>
</p>
<br>

- Valores del sensor del centro
<p align="center">
<img src="https://github.com/user-attachments/assets/6394a75c-1e23-45c7-b830-9a3face75334" alt="sensor centro"/>
</p>
<br>


- Valores del sensor de la izquierda
<p align="center">
<img src="https://github.com/user-attachments/assets/391790c7-32d1-43ce-87e9-9e14abc43831" alt="sensor izq"/>
</p>
<br>


- Valores del sensor de la derecha
<p align="center">
<img src="https://github.com/user-attachments/assets/10fa137d-06d8-4051-b5f3-3fee55c055b0" alt="sensor derecha"/>
</p>
<br>



#### Subbloque "ME_Colision"
El subbloque "ME_Colision" utiliza un diagrama de estados implementado con la herramienta Stateflow para traducir las señales binarias de "Bits_Colision" en acciones concretas. 
Este diagrama define una serie de estados y transiciones que controlan cómo el robot responde ante riesgos detectados:

- Si se detecta un obstáculo frontal, el robot puede girar a la izquierda o derecha, o incluso retroceder, dependiendo de la lectura de los otros sensores.
- Si se detecta riesgo de caída, el robot detiene su movimiento y ejecuta maniobras de recuperación.

Por ejemplo, un estado como `GiroIzquierda` se activa si hay un obstáculo frontal y lateral derecho, y el diagrama lo acompaña de las velocidades lineal y angular necesarias para ejecutar el giro. 
Las transiciones entre estados se activan según condiciones específicas, como `Choque==1` o `Caida==1`.
 <br><br>

- Imagen de ME_Colisión
<p align="center">
<img src="https://github.com/user-attachments/assets/304307d1-9e5a-485a-b50c-e32a8e6298ad" alt="ME_Colision"/>
</p>
<br> 

- Imagen de la máquina de estados usada en ME_Colisión
<p align="center">
<img src="https://github.com/user-attachments/assets/4e6e9006-6ea0-49c5-941a-12ad965471c0" alt="Máquina de estados"/>
</p>
<br>
 
#### Subbloque "Leds_Colision"
El subbloque "Leds_Colision" es el encargado de gestionar los LEDs RGB del robot para proporcionar una señal visual del estado actual. 
Los pines 40, 38 y 42 del Arduino están conectados a los colores rojo (R), verde (G) y azul (B) del LED respectivamente, y están configurados en cortocircuito para operar como un único LED RGB. 

Este diseño permite que el sistema informe visualmente sobre posibles riesgos o eventos importantes en tiempo real, lo que resulta útil tanto para la supervisión externa durante pruebas como para mejorar la interacción con el entorno.

- Imagen del subsistema de Leds_colisión
<p align="center">
<img src="https://github.com/user-attachments/assets/a09d3e12-b407-4941-ac93-1200eea05755" alt="leds colisión"/>
</p>
<br><br>



- ### Control Velocidad
<p align="center">
<img src="https://github.com/user-attachments/assets/332f9b1f-0377-4b8e-83ab-5a0514e5e184" alt="controlvelocidad"/>
</p>
<br><br>

El bloque Control_Velocidad se encarga de calcular y ajustar las velocidades necesarias para que el robot pueda moverse correctamente. 
Para ello, utiliza como entradas la velocidad lineal (`V`), la velocidad angular (`W`) y la distancia entre las ruedas (`L`). 
Este bloque está formado por dos partes principales: "Vel_Ruedas", que calcula la velocidad de cada rueda (izquierda y derecha), y "Controlador_BC", que ajusta estas velocidades usando un controlador PID y envía las señales necesarias para que los motores funcionen correctamente.

Dentro del Controlador_BC, también se encuentra el modelo del robot, que conecta los motores y los sensores (encoders) para medir la distancia recorrida. 
Esto permite que el sistema sea preciso y funcione bien en todo momento.
<br>

#### Vel_Ruedas
<p align="center">
<img src="https://github.com/user-attachments/assets/52e15257-3b69-464b-97cf-9a70be4245e2" alt="vel_ruedas"/>
</p>
<br><br>

El subbloque Vel_Ruedas es el encargado de calcular las velocidades individuales de las ruedas izquierda (`V_Left`) y derecha (`V_Right`) a partir de los datos de entrada: la velocidad lineal del robot (`V`), la velocidad angular (`W`), y la distancia entre ruedas (`L`). 
Este cálculo se realiza mediante las siguientes fórmulas, basadas en el modelo cinemático diferencial del robot:

- `V_{Left} = V − (W⋅L)/2`
- `V_{Right} = V + (W⋅L)/2`
  
La lógica del subbloque toma `V` como base para ambas ruedas y luego ajusta cada una según la velocidad angular y la distancia entre las ruedas. 
Este cálculo permite que el robot pueda girar y avanzar de manera precisa.

El resultado de este subbloque son las velocidades independientes para cada rueda, que se envían al siguiente subbloque para ser ajustadas y ejecutadas.
<br>

#### Sistema_Controlado_BC
<p align="center">
<img src="https://github.com/user-attachments/assets/79d956dd-f410-413b-ab20-bdd2efe35353" alt="sistema_controlado_bc"/>
</p>
<br><br>

El subbloque "Controlador_BC" ajusta las velocidades calculadas en "Vel_Ruedas" mediante un controlador PID, asegurando que el robot alcance la velocidad deseada de forma estable y precisa. 
Este ajuste se realiza generando señales PWM (modulación por ancho de pulso) que controlan la potencia de los motores. Dentro de este subbloque encontramos:

1. Mi_Piero: Este bloque modela el comportamiento físico del robot, simulando cómo los motores convierten las señales PWM en movimiento.

<br><br>
<p align="center">
<img src="https://github.com/user-attachments/assets/93ac99c6-aad3-45e9-9591-f185a8016126" alt="mi_piero"/>
</p>
<br><br>

Contiene:

- FTs_Piero: Modela la dinámica de los motores a través de funciones de transferencia específicas para cada rueda (izquierda y derecha), transformando las señales PWM en velocidades lineales simuladas.

<br><br>
<p align="center">
<img src="https://github.com/user-attachments/assets/cbc139ae-8208-4918-8155-76db8e06dbbd" alt="fts_piero"/>
</p>
<p align="center">
<img src="https://github.com/user-attachments/assets/ae64e15a-49c5-4d2e-826a-da14c3b799ce" alt="fts_1"/>
</p>
<p align="center">
<img src="https://github.com/user-attachments/assets/f143e531-3e32-47d7-babd-c3256eab2da3" alt="fts_2"/>
</p>
<br><br>

Para implementar un controlador PID en nuestro sistema, primero es necesario determinar su función de transferencia, que en este caso relaciona la entrada (PWM) con la salida (velocidad en m/s). Para ello, utilizamos el sistema "Obtener_Valores_PieroHW", el cual nos permite introducir un valor PWM y obtener la velocidad resultante del robot. Esto se realiza midiendo la respuesta del sistema ante un "step" de PWM.

<p align="center">
<img src="https://github.com/user-attachments/assets/7c8b5226-c0e3-4f2c-9014-e5f1bf726345" alt="PID ruedas"/>
</p>

Con los datos obtenidos, empleamos la herramienta "System Identification" de Simulink, que nos permite estimar una función de transferencia ajustada a las características del sistema. Esta herramienta ofrece la flexibilidad de configurar el número de ceros y polos que deseamos en la función de transferencia, lo que nos permite encontrar el modelo más adecuado.

<p align="center">
<img src="https://github.com/user-attachments/assets/8daae83f-ae52-4f56-a1c1-1a28d3cf7ed4" alt="Datos rueda izquierda"/>
</p>

Hemos hecho lo mismo para la rueda derecha
<p align="center">
<img src="https://github.com/user-attachments/assets/bcd9a043-cf7d-402f-870c-f93bb0c63c10" alt="Datos rueda derecha"/>
</p>

A continuación, se ha comprobado que los datos recogidos por la simulación son válidos. El porcentaje que se puede ver a la derecha de cada imagen, indica cuánto se asemeja nuestra función de transferencia estimada a la señal real.

- Para la rueda izquierda
<p align="center">
<img src="https://github.com/user-attachments/assets/5193e564-6549-4f7f-adeb-00210c24822d" alt="Izquierda general"/>
</p>

<p align="center">
<img src="https://github.com/user-attachments/assets/636cf2f3-1156-44f4-af27-c64eeed3ba84" alt="izq1"/>
</p>

<p align="center">
<img src="https://github.com/user-attachments/assets/91d07eb5-07b9-45be-9554-0777e71d4ef7" alt="izq2"/>
</p>

<p align="center">
<img src="https://github.com/user-attachments/assets/396e2887-426c-4365-91bd-0bad76a05235" alt="izq3"/>
</p>


- Para la rueda derecha
<p align="center">
<img src="https://github.com/user-attachments/assets/ce42ad95-de1d-4796-81ec-d4bd381d61ae" alt="Derecha general"/>
</p>

<p align="center">
<img src="https://github.com/user-attachments/assets/77b6ae9a-dd41-42fa-ad33-8a943af7a7c3" alt="dcha1"/>
</p>

<p align="center">
<img src="https://github.com/user-attachments/assets/c963a187-31b5-4987-ae6a-acd356be5251" alt="dcha2"/>
</p>


Tras evaluar diversas opciones, seleccionamos la función de transferencia que tiene 2 polos y 0 ceros (denominada como la 20). Aunque el modelo con un cero (la función 21) ofrece una aproximación más precisa, añadir ceros a la función de transferencia complica el diseño del controlador PID, por lo que optamos por la simplicidad y eficiencia del modelo con solo polos. De esta forma, garantizamos que el controlador sea robusto y funcional sin incrementar innecesariamente su complejidad.

- PierroHW: Conecta las señales de control con el hardware del robot.
	- Salida_Motores: Genera las señales PWM para los motores, incluyendo las señales de habilitación necesarias.
	- Encoder_A_Metros: Convierte las señales de los encoders en distancias recorridas, permitiendo la retroalimentación del sistema.

<p align="center">
<img src="https://github.com/user-attachments/assets/e0f70521-8737-4f7e-b294-cb888c061ad6" alt="piero_hw"/>
</p>
<br><br>

- Imagen del subsistema Salida_Motores
<p align="center">
<img src="https://github.com/user-attachments/assets/76bf46f0-c8a8-49a8-9baa-34c875345446" alt="salida_motores"/>
</p>
<br><br>

- Imagen del subsistema Encoder_A_Metros
<p align="center">
<img src="https://github.com/user-attachments/assets/46e6a71c-0b26-4722-b741-fca9d173413c" alt="encoders_a_metros"/>
</p>
<p align="center">
<img src="https://github.com/user-attachments/assets/718c003e-a9bc-45c7-b65c-64641eb68939" alt="izq1"/>
</p>
<p align="center">
<img src="https://github.com/user-attachments/assets/64c819f1-4da0-4c77-9f29-5994b5e83027" alt="drch1"/>
</p>
<br><br>


Para determinar las ganancias, comenzamos girando manualmente una de las ruedas del robot una vuelta completa y registramos el número de pulsos mostrados en el display del encoder. Posteriormente, aplicamos la fórmula para calcular la ganancia:

`Ganancia = 2*pi*r/Pulsos_una_vuelta`

Donde 𝑟 es el radio de la rueda, y Pulsos_una_vuelta representa el número de pulsos que se generan al completar una vuelta completa de la rueda.

Repetimos este procedimiento para ambas ruedas, asegurándonos de dar una vuelta exacta en cada caso. Los pulsos generados por cada rueda se visualizan mediante un display configurado en Simulink. Sin embargo, durante el proceso observamos que uno de los encoders siempre registraba más pulsos que el otro al realizar una vuelta completa. Esto podría deberse a diferencias en la calibración de los encoders o variaciones en el hardware.

Finalmente, utilizamos los valores obtenidos para cada rueda para ajustar sus ganancias respectivas, asegurando que ambas entreguen lecturas consistentes y precisas durante el funcionamiento del robot.

2. PID: Este componente contiene dos controladores PID, uno para la rueda izquierda y otro para la derecha. 
Cada PID compara la velocidad deseada con la velocidad actual, calculando la diferencia (error) y ajustando la señal PWM para reducir este error.

- Imagen del subsistema PID
<p align="center">
<img src="https://github.com/user-attachments/assets/bc11a483-7c34-4821-af95-e5b2cd9b5bc4" alt="pid"/>
</p>
<br><br>


- Parametros PID izquierdo
<p align="center">
<img src="https://github.com/user-attachments/assets/9a63c468-1974-4348-99dc-609c869bd753" alt="Valores Pid izquierdo"/>
</p>

- Parametros PID derecho
<p align="center">
<img src="https://github.com/user-attachments/assets/fdfce343-f082-4cfe-a0e5-a7951d9e5903" alt="Valores Pid derecho"/>
</p>

Ambos tienen los mismo Tiempo de Establecimiento y el mismo overshoot y ambos tienen saturación (no pueden pasar de +- 255 de señal pwm).
<p align="center">
<img src="https://github.com/user-attachments/assets/3987e823-41be-4d00-ac03-84a97be4e074" alt="Valores Pid comunes"/>
</p>



- Comprobación del controlador
El primer video muestra como reacciona el sistema ante esfuerzos cortos, es decir, aplicar resistencias durante corto tiempo a las ruedas.

https://github.com/user-attachments/assets/9ddf1e7d-75d3-40ea-9754-cb8f7adaa74a

Al haber un delay entre el scope y los estímulos que le proporcionamos, los videos son muy largos. Se verá que primero va el estímulo y pasado un rato, se ve cómo se modifica el valor en pantalla.
<br><br>

El segundo video muestra como se le aplica un esfuerzo durante un largo periodo de tiempo a cada rueda para ver cómo se estabiliza la velocidad (es la ventana de abajo del scope)

https://github.com/user-attachments/assets/82c5fba7-cbe7-4960-9b40-68a3af7f7ea3

<br><br> 



- ### Odometría

<p align="center">
<img src="https://github.com/user-attachments/assets/3abe216b-caa6-47e4-a551-c13360d67bee" alt="Odometria"/>
</p>
<br>


El bloque "Odometría" es el encargado de estimar la posición y orientación del robot en el espacio global mientras éste se desplaza. 
Su objetivo principal es calcular las coordenadas globales (`x`,`y`) y la orientación (`o`) del robot basándose en su velocidad y orientación actuales. 
Este bloque es realmente necesario si queremos que el PIERO siga la trayectoria de la forma más precisa posible.

Para lograr esto, el bloque recibe las siguientes entradas:

- `m/s_control`: Un vector que contiene la velocidad de cada rueda, calculadas en el bloque anterior (Control_Velocidad).
- `L`: La distancia entre las ruedas izquierda y derecha del robot, necesaria para los cálculos cinemáticos.

Con esta información, el bloque genera las siguientes salidas:

- `x, y`: Las coordenadas globales del robot en el plano.
- `o`: La orientación del robot en radianes, relativa al sistema global de coordenadas.

El funcionamiento interno del bloque se basa en el modelo cinemático del robot. 
En primer lugar, las velocidades lineales y angulares se utilizan para calcular las velocidades globales (`Vx`, `Vy`, `W`) mediante transformaciones trigonométricas que tienen en cuenta la orientación actual del robot (`o`).
Estas velocidades globales se integran a lo largo del tiempo para actualizar la posición y orientación global del robot:

1. Cálculo de las velocidades globales: Se realiza una conversión de las velocidades locales a velocidades globales utilizando funciones trigonométricas (`cos` y `sin`).
2. Integración de las velocidades: Las velocidades globales se integran para calcular los incrementos en las coordenadas `x` e `y`, así como los cambios en la orientación `o`.
3. Actualización de las coordenadas globales: Los valores calculados se suman a la posición previa para obtener la nueva posición global.


Dentro del bloque, para facilitar el diseño y la comprensión se encuentra el subbloque MCD (Modelo Cinemático Directo). Este subbloque realiza la transformación de velocidades locales a globales utilizando las entradas `m/s_control` y `L`.

<p align="center">
<img src="https://github.com/user-attachments/assets/46b40aaf-f952-4433-84b5-6cd17f9375d9" alt="Subsistema MCD"/>
</p>
<br>

Finalmente, el bloque incluye una representación visual mediante un gráfico XY Graph, que muestra en tiempo real la trayectoria del robot en el plano. Esto permite monitorear y analizar el movimiento del robot de manera intuitiva.


<br><br>

- ### Bluetooth Total

<p align="center">
<img src="https://github.com/user-attachments/assets/f4492c12-9535-497f-a473-1a2bda156d87" alt="Bluetooth"/>
</p>
<br>

El bloque Bluetooth_Total es el encargado de gestionar la comunicación entre el robot y un dispositivo externo mediante Bluetooth. Es la funcionalidad adicional que le hemos metido a la idea base del PIERO. 
Su objetivo principal es procesar la información recibida a través del canal Bluetooth y traducirla en los parámetros de control que se utilizan en todo el proyecto, como umbrales, velocidades y waypoints. 

Para lograr este objetivo, el bloque recibe las siguientes entradas:

- `Entradas de datos Bluetooth`: Señales digitales representadas por valores binarios provenientes del módulo Bluetooth.
- `Señal de habilitación (Enable)`: Un indicador que activa o desactiva el procesamiento del bloque.

Con esta información, el bloque calcula y actualiza las siguientes salidas:

- `Umbral_Lateral, Umbral_Frontal, Umbral_Abajo y Umbral_Trajectoria`: Parámetros ajustables que definen las distancias críticas para evitar colisiones y guiar el movimiento.
- `V y W`: Velocidades lineales y angulares para el control dinámico del robot.
- `Waypoints`: Lista de puntos de paso que el robot debe seguir en su trayectoria.
- `Movimiento trayectoria`: Señales específicas que modifican otros aspectos del comportamiento del robot.

Dentro del bloque Bluetooth_Total, la información se organiza y procesa en 4 subbloques principales. 
El flujo de datos sigue un orden lógico que comienza de la siguiente manera:
- Bluetooth_Datos sirve como nodo principal para la recepción y distribución de los datos. Todas las señales entrantes primero pasan por este subbloque, que valida y organiza la información.

<p align="center">
<img src="https://github.com/user-attachments/assets/b1abfa28-ac8b-4000-a97f-a2279ed81477" alt="Bluetooth_Datos"/>
</p>
<br>

- Desde Bluetooth_Datos los datos se dirigen a los otros tres subbloques según las funciones específicas:
  
  - Bluetooth_Umbrales recibe las señales relacionadas con distancias y parámetros críticos. Este subbloque calcula los umbrales dinámicos que el robot utilizará para decisiones de navegación y seguridad. Convierte las entradas digitales en valores escalados y los asigna a las salidas correspondientes (`Umbral_Lateral`, `Umbral_Frontal`, `Umbral_Abajo` y `Umbral_Trajectoria`).
  - Bluetooth_Velocidad se conecta para procesar los comandos de movimiento. A partir de los datos recibidos de Bluetooth_Datos traduce las señales digitales en parámetros de velocidad lineal (`V`) y angular (`W`) que el robot utilizará para desplazarse.
  - Bluetooth_Trayectoria toma los datos correspondientes a los waypoints para generar la lista de puntos de paso que definirán la trayectoria que el robot debe seguir. La salida principal de este subbloque es la lista Waypoints que se utiliza en la navegación.

- Imagen del subsistema Bluetooth_Umbrales
<p align="center">
<img src="https://github.com/user-attachments/assets/97076b39-13b7-489a-9179-dc36c596ccbc" alt="Bluetooth_Umbrales"/>
</p>
<br>

- Imagen del subsistema Bluetooth_Velocidad
<p align="center">
<img src="https://github.com/user-attachments/assets/7da28d94-a1f9-45b9-8cc4-cee7aa62291e" alt="Bluetooth_Velocidad"/>
</p>
<br>

- Imagen del subsistema Bluetooth_Velocidad
<p align="center">
<img src="https://github.com/user-attachments/assets/5c25076d-87e0-4c56-b6d3-7564b4b26da7" alt="Bluetooth_Trayectoria"/>
</p>
<br>

- Imagen de la aplicación
<p align="center">
<img src="https://github.com/user-attachments/assets/0f0c3ffa-6066-4b4d-944e-84e5c5d8d642" alt="comandos" width="400"/>
</p>

Para la comunicación Bluetooth del robot PIERO, hemos utilizado el módulo HM-10, que utiliza  Bluetooth 4.0, conectado a través de la aplicación nRF Connect en un dispositivo Android. Esta configuración permite enviar y recibir comandos en forma de bytes desde el móvil, los cuales son procesados en el entorno de Simulink mediante el bloque Serial Receive. Existen tres tipos principales de comandos:

- `FFFF` para establecer comandos de velocidad.
- `FFAA` para definir trayectorias enviando cuatro bytes que representan las coordenadas de los puntos de la trayectoria (por ejemplo, `x=1` y `y=0` es 98, 94 es `x=1` y `y=-4`, ya que si `x=0` y `y=0`, es 88).
- `AAFF` para modificar los umbrales del robot en tiempo real.
  
El sistema incluye funcionalidades avanzadas como la reinicialización de la posición y ángulo del robot al inicio de cada nueva trayectoria, facilitando la programación de múltiples trayectorias consecutivas sin perder el punto de referencia. Esta implementación no solo optimiza la navegación reactiva del robot, sino que también permite ajustes dinámicos a través del móvil, haciendo que el sistema sea altamente interactivo y adaptable.

https://github.com/user-attachments/assets/5f756aeb-399f-415a-8cfe-dfe6288214d1

https://github.com/user-attachments/assets/7abba03a-3ade-438d-89d5-c365054659f7



<br><br>

## Resultados prácticos:

Una vez implementado el código nos dispusimos a comprobar su funcionamiento. 
Los resultados de estas pruebas, después de todos los inconvenientes encontrados y de todos los errores cometidos, son muy satisfasctorios. 
El robot logra totalmente seguir la trayectoria dada esquivando los obstaculos:

<br><br>


- ### Prueba Anticaída
El sistema de esta prueba se encuentra en el sistema Anticolisión

https://github.com/user-attachments/assets/5fc0a8a3-feac-4729-8c7d-b6ef88b0056c

<br><br>

- ### Prueba de seguimiento de trayectoria (3 giros de 90º y saliendo de la clase)
El sistema de esta prueba es lo que denominamos como test total.

https://github.com/user-attachments/assets/4b7aaf1d-b11d-4f0d-a7fe-ae252d0c7349

<br><br>

- ### Prueba avanzar 10 baldosas

<p align="center">
<img src="https://github.com/user-attachments/assets/4f7bf2e8-292e-4a8e-a0ca-f5ef5a167473" alt="prueba 100 baldosas"/>
</p>

https://github.com/user-attachments/assets/350bd845-e4a3-4ac6-aad6-4c441525449a

<br><br>

- ### Prueba trayectoria circular
<p align="center">
<img src="https://github.com/user-attachments/assets/bb4663d9-044e-45db-9299-b7fa5c0858da" alt="prueba circular"/>
</p>

https://github.com/user-attachments/assets/6427d975-f33c-4852-8bc5-7db2bab975b4


<br><br>

## Conclusiones:

A pesar de haber sido un trabajo un tanto tedioso, ya sea por el manejo de los cables, sus uniones y empalmes, o por los ajustes del código (para que lograra hacer lo que se nos pide), hemos aprendido bastante al poner en práctica lo que hemos estado viendo teóricamente en la asignatura. 
Si tuviésemos que cambiar algo, simplemente sería el software de diseño de código ya que, al utilizar Arduino Mega lo más eficiente es utilizar el Arduino IDE para generar todo el código ya que está optimizado para la placa utilizada.
<br><br>

## Autoevaluación:
<p align="center">
<img src="https://github.com/user-attachments/assets/03783c57-9509-43e2-a45a-32eb62841742" alt="trabajandoenequipo" width="800"/>
</p>

Como grupo consideramos que hemos trabajado de la forma más equitativa posible. Hemos intentado siempre estar juntos para trabajar a la vez en todos los ámbitos, ya sea en el Readme, montando el PIERO o escribiendo el código. Es por esto que a los tres nos damos el mismo porcentaje de nota un 33,33%. 
Teniendo todo lo explicado en el Readme, como proyecto, le pondríamos a nuestro PIERO un 8, ya que pensamos que hay cosas que se pueden mejorar, pero sí hemos logrado muy bien el objetivo y hemos aprendido de nuestros errores.

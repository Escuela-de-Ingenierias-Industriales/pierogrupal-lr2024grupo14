# PIERO - Robot Móvil Autónomo DIY
## Presentacion
  
  Somos el grupo 14 de la asignatura de Laboratorio de robótica 2024/25 formado por Iván Calvo Santos, Lucía Ortiz Miranda y Jorge Espiau Bhawnani.  Como parte de este curso, se nos ha asignado el desarrollo de un robot móvil llamado PIERO. Este proyecto combina diseño, montaje, programación e integración de sistemas para crear una plataforma capaz de desplazarse de manera autónoma y evitar obstáculos. A modo de adelanto, la siguiente imagen muestra el resultado final nuestro proyecto, un arduo trabajo lleno de inconvenientes y obstáculos en el que hemos puesto casi tres meses de empeño.

## Introducción
En esta asignatura, se nos planteó el desafío de construir y programar un robot móvil llamado PIERO, diseñado para desplazarse de manera autónoma y evitar obstáculos. Este proyecto busca aplicar conceptos de robótica, integración de hardware y desarrollo de software en un entorno práctico.
PIERO es una plataforma de tracción diferencial equipada con dos motores eléctricos y sensores que le permiten interpretar el entorno. Nuestra tarea consistió en caracterizar sus componentes, desarrollar el software necesario para que pueda seguir consignas de velocidad lineal y angular, y probar su capacidad para resolver un reto concreto: partiendo de un punto determinado, salir del laboratorio evitando obstáculos.


## Estudio de las Partes del Robot PIERO: Dispositivos y Cableado

  En esta etapa inicial de la investigación sobre el robot PIERO, nos hemos dedicado a explorar de manera detallada los elementos fundamentales y la instalación del cableado requerido para ensamblar y operar el robot. Impresiona ver cómo cada uno de los dispositivos que conforman al Piero es crucial para el correcto movimiento e interacción del este con su entorno, y de cómo, a pesar de la aparente complejidad del modelo visto en clase, su cableado y conexión son bastante sencillos.

El siguiente listado contiene los componentes usados 
### Componentes Principales del Robot PIERO
![motor con rueda](https://github.com/user-attachments/assets/fc06e6f1-2265-43b0-b6dc-e3e6b4f56709)

**-Motores con Ruedas (x2)**: Los motores son de corriente continua de 12V y 170 RPM. Estos motores son fundamentales para el desplazamiento del robot y conforman la base de su sistema de movimiento.  Además contamos con una rueda caster para estabilizar su base.

![lca1010a](https://github.com/user-attachments/assets/0c6cc2c1-5139-4d9e-a8e4-08744dde88be)

**-Arduino Mega 2560**:  Es el cerebro del robot. La característica más destacada del Arduino Mega 2560 es su habilidad para controlar numerosas entradas y salidas gracias al gran abanico de pines con los que cuenta. Esto posibilita la conexión sin dificultades de múltiples sensores y actuadores. 

![driver](https://github.com/user-attachments/assets/97a91e1a-5f60-451e-8ca8-12479732a0c2)

**-Driver de Potencia L298N**: Este elemento tiene la responsabilidad de manejar los motores. Actúa como un puente H que proporciona control de velocidad y rotación del motor mediante PWM (modulación de ancho de pulso).

![sensor ultrasonidos](https://github.com/user-attachments/assets/48ce2882-181b-4222-862f-62d08f6ef41d)


**-Sensores de Distancia Ultrasonidos**: Los sensores de distancia son esenciales para detectar obstáculos y prevenir colisiones durante el desplazamiento del robot. Los sensores de ultrasonido ofrecen una cobertura amplia pero poca precisión.

![pack-de-2-baterias-li-ion-18650-2400mah-37v](https://github.com/user-attachments/assets/630676de-b5b8-4d26-be37-59a526c30c9f)

**-Baterías y Porta Baterías**: Para el suministro de energía, se emplean baterías del tipo 18650, las cuales son recargables y presentan una adecuada combinación entre capacidad y tamaño. El soporte de baterías facilita una instalación segura y organizada, conectándose al Arduino mediante un interruptor para regular el encendido y apagado del sistema.

![voltimetro](https://github.com/user-attachments/assets/1efdb843-4632-4274-a111-10ac87f57a30)

**-Voltímetro**: Es un elemento pequeño pero imprescindible para supervisar la descarga de la batería en tiempo real. 

![cables-dupont-macho-macho-40-cm-40-unidades](https://github.com/user-attachments/assets/2c65bff1-1a82-42d9-8c63-773507afdd6f)

**-Cables Du Pont y Conexiones**: El cableado correcto es esencial en el proceso de montaje. El uso de cables Du Pont hace que sea más fácil conectar los diferentes módulos al Arduino. 

## Cableado del Robot PIERO
### El cableado del robot es una de las partes más cruciales que demanda mayor concentración. Garantizar la adecuada conexión de las piezas es clave para el correcto funcionamiento del robot. A continuación, se resaltan algunos puntos clave:

**-Conexión de los Motores al Driver L298N**: Los motores se enlazan al controlador a través de las clavijas de salida del motor del L298N. Este controlador también se conecta a los pines de control del Arduino (generalmente pines digitales).Asimismo, es necesario enlazar el módulo de alimentación para asegurar que los motores cuenten con la cantidad adecuada de energía.

**-Conexión de Sensores**: Los sensores de ultrasonido son conectados a los pines digitales del Arduino. Configurar adecuadamente los pines de entrada y salida y programar Arduino de forma eficiente es crucial para la lectura de datos.

**-Baterías y Sistema de Alimentación**: Se conectan las baterías al Arduino y a los motores mediante un sistema de distribución de energía que cuenta con un interruptor y un voltímetro. Esto no solo hace más sencillo encender y apagar al robot, sino que también permite vigilar constantemente el estado de la batería.

Una vez entendidas las funciones de cada componente y habiendo estudiado su conexionado nos dispusimos a montarlo por nuestra cuenta sobre un túper de plástico:

![Foto 1](https://github.com/user-attachments/assets/7dcbb292-c408-4090-8af7-696aa969e9ce)

Lo primero fue idear donde colocar cada dispositivo. Los motores y la caster fueron los primeros en añadirse. Utilizamos tornillos de diámetro 5 para la caster u como no pudimos conseguir los tornillos de diámetro 4 y longitud mínima para los motores utilizamos bridas que posteriormente se cortarían.

![Foto 2](https://github.com/user-attachments/assets/795fa7de-bc00-4727-bda8-6a95b4cdf083)
	
Ya con los motores, lo siguiente fue poner al Arduino, porta baterías, driver y protoboard donde mejor se pudieran manejar, aun así, en la imagen se puede apreciar que estaban de forma temporal para poder probar distintos lugares y ver cómo se manejaban en estos.

![Foto 3](https://github.com/user-attachments/assets/44ea9486-413e-4977-b52c-203c5a792e92)

El siguiente paso fue idear donde sería mejor poner los sensores de ultrasonidos y también ponerlos de forma temporal con alambres.

![Foto 4](https://github.com/user-attachments/assets/a067525a-b45b-4e66-91af-381737e7e4de)

Y por último, antes de pasar al cableado, fue distribuir y poner los distintos leds que usaríamos. 

![Foto 5](https://github.com/user-attachments/assets/1ca3f5e6-371b-4c1c-b586-75649f501777)
![Foto 6](https://github.com/user-attachments/assets/8a3e72e0-4c24-4a54-8106-12fd81642d62)


## Interconexionado.

Para esta parte empezaos haciendo un Excel que nos serviría de guía para saber que pines del Arduino ya estábamos usando y para que se utilizaban. Este Excel se tuvo que cambiar a lo largo del proyecto un par de veces debido a fallos del propio Arduino.

--Foto del excel

Así, pudimos empezar con el conexionado.

![Conexionado 1](https://github.com/user-attachments/assets/a553416c-72b7-4060-9b21-a6164f28e597)
![conexionado 2](https://github.com/user-attachments/assets/b4d016d5-d037-4014-aaea-2c029640bd24)
![Conexionado 3](https://github.com/user-attachments/assets/ad38c3d4-b7dd-4d28-aa11-24efd3594903)

 Aunque, a decir verdad, esta fue la parte en la que tuvimos más problemas, el mayor causante de estos fueron los cable que venían por defecto en los componentes que pedimos, estos cables eran muy frágiles y con mala conducción, es por eso que tuvimos que quitar algunos y sustituirlos por otros cables de nuestra elección, empalmar unos cables con otros e incluso utilizar celo para que no se desconectaran.
 
![conexionado 4](https://github.com/user-attachments/assets/92601a6c-eba4-436c-9877-da2651aa6569)

Una vez llegaron los nuevos cables ya pudimos soldarlos y empalmarlos correctamente

![conexionado 5](https://github.com/user-attachments/assets/b89ed0cb-19db-45fa-9c05-f4854520a7d9)
![conexionado6](https://github.com/user-attachments/assets/52d61136-9872-4759-a25c-204c8c8fa5d7)

Ya con estos cables conseguimos un prototipo precario al Piero que buscábamos, todavía nos daba fallos en conexiones y por eso tuvimos un estancamiento largo en esta parte.

![conexionado 7](https://github.com/user-attachments/assets/8834bb77-62a1-4729-9757-7464b78d31ef)

Fue con este conexionado, en las pruebas con el código, que pudimos ver que una de las ruedas no giraba, y que no era fallo del código. Es por eso que desconectamos todo y lo volvimos a rehacer para ver que pines no estaban funcionando como debian

![conexionado 8](https://github.com/user-attachments/assets/f596e851-56ee-4958-b1ab-bdf04dd6aa27)
![conexionado 9](https://github.com/user-attachments/assets/56b57d6a-1880-47e4-964d-289ad4dc6a52)
![conexionado 10](https://github.com/user-attachments/assets/754d84b9-d4f4-48e0-8c8a-5bdae4b4c528)

Y al fin conseguimos que todo estuviera bien cableado.

![conexionado 11](https://github.com/user-attachments/assets/c16be8fc-df80-4a7a-8ead-c76eff1c19ca)

***

# Estudio de la programación IDE del Arduino Mega (Interrupciones, lectura encoders)
### Arduino dispone de dos tipos de eventos en los que definir interrupciones. Por un lado tenemos las interrupciones de timers. Por otro lado, tenemos las interrupciones de hardware, que responden a eventos ocurridos en ciertos pines físicos.

Dentro de las interrupciones de hardware, que son las que nos ocupan en esta entrada, Arduino es capaz de detectar los siguientes eventos.

* <RISING>, ocurre en el flanco de subida de <LOW> a <HIGH>
* <FALLING>, ocurre en el flanco de bajada de <HIGH> a <LOW>
* <CHANGING>, ocurre cuando el pin cambia de estado (rising + falling)
* <LOW>, se ejecuta continuamente mientras está en estado <LOW>

Los pines susceptibles de generar interrupciones varían en función del modelo de Arduino. El Arduino Mega dispone de 6 interrupciones, en los pines 2, 3, 21, 20, 19 y 18 respectivamente.

![Arduino-Mega-Pinout](https://github.com/user-attachments/assets/f010aa3b-ab0f-4f4c-bba4-5fd6604493bb)


![Captura de pantalla 2024-09-20 115055](https://github.com/user-attachments/assets/7a1aa8af-6413-42d4-9da1-ab5a1161969c)


## Función ISR
La función asociada a una interrupción se denomina ISR (Interruption Service Routines) y, por definición, tiene que ser una función que no recibe nada y no devuelva nada.
Dos ISR no pueden ejecutarse de forma simultánea. En caso de dispararse otra interrupción mientras se ejecuta una ISR, la función ISR se ejecuta una a continuación de otra. Al diseñar una ISR debemos mantener el menor tiempo de ejecución posible.
Frecuentemente la función de la ISR se limitará a activar un flag, incrementar un contador, o modificar una variable. Esta modificación será atendida posteriormente en el hilo principal, cuando sea oportuno.

Para poder modificar una variable externa a la ISR dentro de la misma debemos declararla como “volatile”. El indicador “volatile” indica al compilador que la variable tiene que ser consultada siempre antes de ser usada, dado que puede haber sido modificada de forma ajena al flujo normal del programa.

Las interrupciones tienen efectos en la medición del tiempo de Arduino, tanto fuera como dentro de la ISR, porque Arduino emplea interrupciones de tipo Timer para actualizar la medición del tiempo.
Durante la ejecución de una interrupción Arduino no actualiza el valor de la función millis y micros.

Dentro de la ISR el resto de interrupciones están desactivadas. Esto supone:
* La función millis no actualiza su valor, por lo que no podemos utilizarla para medir el tiempo dentro de la ISR. 
* Como consecuencia, la función delay() no funciona, ya que basa su funcionamiento en la función millis().
* La función micros() actualiza su valor dentro de una ISR, pero empieza a dar mediciones de tiempo inexactas pasado el rango de 500us.
* En consecuencia, la función <delayMicroseconds> funciona en ese rango de tiempo, aunque debemos evitar su uso porque no deberíamos introducir esperas dentro de una ISR.

## Creación de interrupciones en Arduino
Para definir una interrupción en Arduino usamos la función:
<attachInterrupt(interrupt, ISR, mode);>

Donde interrupt es el número de la interrupción que estamos definiendo, ISR la función de callback asociada, y mode una de las opciones disponibles (FALLING, RISING, CHANGE y LOW).
No obstante, es más limpio emplear la función digitalPinToInterrupt(), que convierte un Pin a la interrupción equivalente.
<attachInterrupt(digitalPinToInterrupt(pin), ISR, mode);>

Otras funcionas interesantes para la gestión de interrupciones son:
* <DetachInterrupt(interrupt)>, anula la interrupción.
* <NoInterrupts()>, desactiva la ejecución de interrupciones hasta nueva orde.
* <Interrupts()>, reactiva las interrupciones.


***
## Estudios previos para el desarrollo del código
### Estudio del Arduino Mega 2560 para su programación con Simulink: librería y entorno específico
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


### Programación en Arduino Mediante Matlab y Simulink
Para empezar a operar nuestro Arduino en el software de Matlab deberemos instalarnos dos paquetes de soporte. Para ello realizaremos los tres siguientes pasos.
1. Abriremos el software Matlab
2. Accederemos a “Home”  > "Adds-Ons" > "Get Adds-Ons"
3. Instalamos los dos siguientes Adds-Ons:
 
Una vez instalados, separaremos la configuración de nuestro Arduino dependiendo de si utilizamos Matlab o Simulink
Matlab
Para establecer la conexión entre Matlab y nuestra placa deberemos poner el siguiente comando: 
a = arduino()  Se utilizará si hemos conectado al ordenador un hardware Arduino oficial

a = arduino('COM3','Uno'). Se utilizara si el hardware no es oficial. ## “COM3” es el puerto del ordenador y “Uno” es el modelo del hardware.

Los comandos que nos dan los “adds-ons” instalados son los siguientes
 

### Simmulink
Para establecer la conexión entre Simulink y nuestra placa deberemos pulsar el botón “Model Configuration Parameters Button”
 
Una vez dentro, accedemos a la pestaña “Hardware Implementation” y rellenamos el hueco de “Hardware Board” con el nombre de nuestra placa.

Para simular nuestro proyecto en Simulink deberemos elegir el modo de simulación externo (para ejecutar nuestro programa en el hardware Arduino). Deberemos poner también el tiempo de simulación en infinito.
 
Para transferir nuestro código a la placa Arduino (evitando la necesidad de que la placa no tenga que estar siempre conectada a Simulink)
 
## Desarrollo del código.
Ya con los fundamentos sobre como usar las interrupciones, el Matlab y el simulink empezamos a desarrollar todo el código necesario para lograr la navegación reactiva.
Al principio, lo primero que hicimos fueran las actividades del Test de motores, de leds y de sensores. 
Aunque hicimos algunas tareas para clase y unos cuantos códigos que están en el repositorio, nos centraremos unicaente en los que utilizamos finalmente en nuestro proyecto.
Hablaremos  ahora, de nuestro testTotal, un test que junta las librerias necesarias para, no solo hacer que el robot esquive obstaculos, sino para lograr que el robot siga una trayectoria esquivando los obstaculos que puedan haber en su recorrido, con el añadido de que, gracias a un componente bluetooth, se pueda controlar el robot desde el movil.
Este test esta compuesto por cinco librerias, cada una de ellas desempeñando una funcion vital para el perfecto desempeño del Piero.
### Trayectoria
El bloque "Trayectoria" se encarga de calcular y supervisar el movimiento del robot entre una serie de puntos de paso o waypoints. 
Su objetivo principal es determinar la velocidad y orientación necesarias para que el robot se dirija al siguiente waypoint en la secuencia hasta que se alcancen todos ellos. 
Este bloque juega un papel crucial en la navegación del robot, ya que traduce la información sobre la posición actual del robot y los objetivos definidos en una trayectoria eficiente y controlada.

Para lograr este objetivo, el bloque recibe las siguientes entradas:

- Waypoints: Una matriz donde cada fila representa las coordenadas(x,y) de un waypoint al que el robot debe dirigirse.
- Umbral_Trajectoria: Una distancia umbral que determina cuándo el robot se considera lo suficientemente cerca de un waypoint para avanzar al siguiente.
- Pose: La posición actual del robot, especificada en un vector [x,y].
- V_in: La velocidad de entrada actual del robot.
- i_act: El índice del waypoint actual que está siguiendo el robot.

Con esta información, el bloque calcula y actualiza las siguientes salidas:

- V_out: La velocidad del robot después de procesar la trayectoria.
- o: La orientación del robot, calculada para dirigirse al siguiente waypoint.
- i_prox: El índice actualizado del siguiente waypoint al que debe dirigirse el robot.

El funcionamiento interno del bloque toma como punto de partida la posición actual del robot (Pose) y el siguiente waypoint en la lista (Waypoints[iprox]). 
Primero, se calcula la distancia entre ambas posiciones mediante la fórmula euclidiana. 
Con esta distancia, se evalúa si el robot se encuentra lo suficientemente cerca del waypoint (es decir, si está dentro del umbral definido por Umbral_Trajectoria). 
Si la distancia supera el umbral, el bloque calcula la orientación necesaria para que el robot avance hacia el waypoint y ajusta la velocidad de salida (Vout) en función de la velocidad de entrada (Vin). 

Cuando el robot alcanza el waypoint (distancia menor o igual al umbral), el índice del waypoint actual (iprox) se actualiza para dirigir al robot hacia el siguiente objetivo en la lista. 
Si no quedan más waypoints por alcanzar, el bloque detiene el movimiento del robot, asignando cero a la velocidad y la orientación.
Dentro del bloque, el cálculo de las transformaciones de las entradas a las salidas se realiza principalmente a través de una función MATLAB. 
Esta función implementa la lógica de navegación en varios pasos clave. Primero, se evalúa si aún quedan waypoints disponibles en la lista. 
Luego, utiliza la posición actual del robot y las coordenadas del siguiente waypoint para calcular la distancia entre ambos mediante la fórmula euclidiana. 
Basándose en esta distancia, la función determina si el robot debe continuar avanzando hacia el waypoint actual o si debe pasar al siguiente. 
Además, calcula la orientación requerida mediante la función atan2, que asegura un ángulo correcto entre las posiciones del robot y el waypoint. 
Finalmente, actualiza las salidas Vout y o para controlar el movimiento del robot, y ajusta iprox para garantizar que el robot siga avanzando correctamente por la trayectoria definida. 
Si no quedan más waypoints, la función garantiza que el robot se detenga, asignando cero a la velocidad y la orientación.


### Sistema_Anticolision
El bloque "Sistema_Anticolision" es una parte clave del sistema de navegación del robot. 
Su propósito es garantizar que el robot pueda moverse de forma segura, reaccionando rápidamente a posibles colisiones o caídas. 
Este bloque ajusta la velocidad y la orientación del robot en tiempo real, basándose en los datos de los sensores y en ciertos umbrales predefinidos que indican riesgos.

Para cumplir este objetivo, el bloque "Sistema_Anticolision" recibe las siguientes entradas:

- Velocidad: La velocidad lineal actual del robot, que puede modificarse en función de las condiciones detectadas.
- UmbralFrontal: Distancia mínima al frente que, si se supera, se considera que hay riesgo de colisión frontal.
- UmbralLateral: Distancia mínima a los lados que, si se supera, indica riesgo de colisión lateral.
- UmbralCaida: Distancia mínima hacia abajo que, si se supera, identifica un posible riesgo de caída.

Con esta información, el bloque genera las siguientes salidas:

- V (Velocidad Lineal): La velocidad lineal ajustada del robot tras procesar las condiciones de riesgo.
- W (Velocidad Angular): La velocidad angular ajustada para modificar la orientación del robot y evitar colisiones o caídas.

El bloque "Sistema_Anticolision" está formado por varios subbloques que trabajan juntos para analizar las condiciones del entorno y tomar las decisiones necesarias:

#### Subbloque "Bits_Colision"
Este subbloque toma los datos de los sensores y los compara con los valores de los umbrales establecidos (UmbralFrontal,UmbralLateral,UmbralCaida). 
Básicamente, convierte las lecturas continuas de los sensores en señales binarias (0 o 1) que indican la presencia o ausencia de riesgo. Por ejemplo:

- Un valor 1 en "Collision Frontal" indica que la distancia medida por el sensor frontal es menor o igual al UmbralFrontal, es decir, hay un riesgo de colisión frontal.
- Un valor 0 indica que no hay riesgo de colisión en esa dirección.

De esta forma, las señales binarias son un resumen claro y directo del estado del entorno, lo que facilita la toma de decisiones en los siguientes subbloques.

#### Subbloque "ME_Colision"
El subbloque "ME_Colision" utiliza un diagrama de estados implementado con la herramienta Stateflow para traducir las señales binarias de "Bits_Colision" en acciones concretas. 
Este diagrama define una serie de estados y transiciones que controlan cómo el robot responde ante riesgos detectados:

- Si se detecta un obstáculo frontal, el robot puede girar a la izquierda o derecha, o incluso retroceder, dependiendo de la lectura de los otros sensores.
- Si se detecta riesgo de caída, el robot detiene su movimiento y ejecuta maniobras de recuperación.

Por ejemplo, un estado como "GiroIzquierda" se activa si hay un obstáculo frontal y lateral derecho, y el diagrama lo acompaña de las velocidades lineal y angular necesarias para ejecutar el giro. 
Las transiciones entre estados se activan según condiciones específicas, como Choque==1 o Caida==1.

#### Subbloque "Leds_Colision"
El subbloque "Leds_Colision" es el encargado de gestionar los LEDs RGB del robot para proporcionar una señal visual del estado actual. 
Los pines 40, 38 y 42 del Arduino están conectados a los colores rojo (R), verde (G) y azul (B) del LED respectivamente, y están configurados en cortocircuito para operar como un único LED RGB. 

Este diseño permite que el sistema informe visualmente sobre posibles riesgos o eventos importantes en tiempo real, lo que resulta útil tanto para la supervisión externa durante pruebas como para mejorar la interacción con el entorno.






Para estos test seguimos un poco la idea del profe, pero los que usamos finalmente en el Piero fueron ligeramente distintos.

### Test Luces:

El primero del que voy a hablar es del Test Luces en models, este es uno de los test de luces, ya que hemos implementado dos lógicas dependiendo de la funcionalidad del led,  que actualmente se encuentra en la carpeta basura porque lo que nos interesa es el subprograma que se utiliza ahí, todos, los subprogramas se encuentran en la carpeta lib y se irán hablando de ellos debido a que se utilizan a lo largo de los distintos modelos. 

El subprograma Leds 1 es bastante distinto al dado por el profesor en clase, ya que se utilizará para el estado de la batería. La idea de este es coger la entrada dada por el sensor de voltaje y compararla con una constante calculada. Esta constante es para 11V == 450 y para 11,2== 458. De esta forma, dependiendo del dato que nos llegue del sensor de voltaje, distinguimos tres situaciones: Que nuestras baterías tengan más de 11,2V, en ese caso nada nos tiene que preocupar y el led se encenderá con una luz azul. El siguiente caso es para cuando ha bajado de 11,2 pero no de 11, lo cual hace que el led se mantenga en un color rojo fijo. Pero en cambio cuando ya ha bajado de 11 V, el led nos avisará de que lo tenemos que cargar por un brillo intermitente en rojo. Toda esta lógica se consigue implementar gracias a puetas lógicas and, or y not, a los comparadores de constantes, al pulse generator y a los bloques de digital write de la librería de Arduino.

El segundo subprograma de Leds se prueba en el subsistema llamado Sistema_Anticolision ubicado en lib, que a su vez, se utiliza en el TestTotal, este subsistema llamado Leds_Colision servirá para indicar de qué sensor se está recibiendo datos de un obstáculo. Aquí dividimos 4 respuestas: La primera, que se pongan verde si no recibe ni de la derecha ni de la izquierda, es decir, no hay obstáculos. Si se recibe de la izquierda se pone azul y si se recibe de la derecha en rojo. Por último, si se recibe de los dos lados se pondrá en rojo intermitente. Esta lógica utiliza los mismos bloques que el anterior subsistema.


 

### Test Encoders
El siguiente modelo del que se hablará será del TestMotores, bastante distinto al visto en clase.

### TestTotal



## Resultados prácticos:
•	Desempeño del robot en pruebas reales.
•	Comparación entre simulación y realidad.
•	Fotos, vídeos y gráficos relevantes.
## Conclusiones:
•	Reflexión sobre los logros.
•	Impacto del aprendizaje.
•	Propuestas para mejorar el robot en el futuro.
## Autoevaluación:
•	Desempeño grupal o individual.
•	Justificación de la nota asignada.

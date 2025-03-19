# Reporte técnico de DOFBOT-JetsonNANO

[TOC]


## Descripción del Sistema Mecánico

El **Dofbot Jetson Nano** Se caracteriza por su diseño estructural compacto y flexible, permitiendo una gran capacidad de manipulación en diversas aplicaciones.  

### Dimensiones y Peso  
- **Dimensiones:** 272 mm × 135 mm × 473 mm (con todas sus articulaciones completamente extendidas).  
- **Peso:** 1256 g.  

### Estructura y Materiales  
La estructura principal está fabricada en **aleación de aluminio anodizado en color verde**, con un espesor de **2 mm**. Esta elección de material proporciona:  
- **Ligereza** sin comprometer la resistencia mecánica.  
- **Rigidez estructural**, asegurando estabilidad y protección de los componentes internos.  
- **Mayor durabilidad**, gracias al proceso de anodizado que mejora la resistencia a la corrosión y al desgaste.  

### Grados de Libertad y Sistema de Movimiento  
El Dofbot Jetson Nano cuenta con **6 grados de libertad**, lo que le permite realizar movimientos complejos y alcanzar una amplia variedad de posiciones en el espacio.  

### Base y Estabilidad  
La base del chasis incorpora **ventosas** para proporcionar estabilidad al robot sobre superficies lisas. Esto es especialmente útil en tareas que requieren:  
- Aplicación de fuerzas.  
- Movimientos bruscos sin desplazamientos no deseados.  
- Alta precisión en la ejecución de movimientos.  

### Integración de Cámara  
El sistema incluye una **cámara acoplada** dentro del brazo robótico, lo que facilita la coordinación **ojo-mano**. Esto permite:  
- Captura de imágenes desde una perspectiva cercana al área de trabajo.  
- Implementación de visión artificial para reconocimiento y manipulación de objetos.  

### Sistema de Accionamiento  
El brazo robótico emplea un **conjunto de servomotores de bus serie de alta calidad**:  
- **5 servos** con un **par torsional de 15 kg**.  
- **1 servo adicional** con un **par torsional de 6 kg**.  

Estos servos inteligentes permiten:  
- **Control preciso** de la posición y velocidad de cada articulación.  
- **Lectura en tiempo real** del ángulo actual de cada servo.  
- **Menor complejidad de cableado**, gracias a la interfaz de bus serie.  

#### Características Adicionales de los Servos  
- **Engranaje metálico integrado**, resistente al desgaste.  
- **Potenciómetro de alta precisión**, que prolonga la vida útil del sistema.  

### Especificaciones Técnicas  
| Característica | Valor |
|--------------|------|
| **Carga útil** | 200 g (peso sostenido con el brazo extendido) |
| **Carga máxima** | 500 g (peso de sujeción y manipulación) |
| **Envergadura** | 350 mm |
| **Distancia máxima abierta de la abrazadera** | 6 cm |
| **Rango de rastreo efectivo** | Área con un radio ≤30 cm, con el eje central como un semicírculo |

## Descripción del Sistema Electrónico

El **corazón del sistema electrónico** del Dofbot Jetson Nano es la placa de desarrollo **Jetson Nano de 4GB RAM**, desarrollada por **NVIDIA**. Esta placa ofrece una potencia de cómputo considerable gracias a su arquitectura avanzada, ideal para la ejecución de algoritmos de inteligencia artificial y el control en tiempo real del robot.  

### Componentes Principales  

#### **Jetson Nano**  
La **Jetson Nano** integra:  
- **GPU:** NVIDIA Maxwell con **128 núcleos**.  
- **CPU:** Cuatro núcleos **ARM Cortex-A57**.  
- **Capacidad de cómputo:** **472 GFLOP**, ideal para tareas de **visión artificial** e **inteligencia artificial**.  

#### **Cámara HD**  
El Dofbot incorpora una **cámara de alta definición (HD)** que actúa como el **sensor principal** para funciones de visión artificial. Permite al robot:  
- Percibir su entorno visual.  
- Capturar imágenes para **reconocimiento de objetos**, **seguimiento de movimientos** e **identificación de gestos**.  

### **Placa de Expansión Multifuncional**  
Esta placa sirve como **interfaz** entre la **Jetson Nano** y diversos **periféricos** del robot, tales como:  
- **Servos**.  
- **Cámara**.  
- **Sensores y actuadores adicionales**.  

#### **Compatibilidad**  
La placa de expansión es compatible con múltiples plataformas de desarrollo:  
- **Jetson Nano**  
- **Raspberry Pi**  
- **Arduino**  
- **Micro:bit**  

Esto convierte al Dofbot en una plataforma **versátil** para aprendizaje y experimentación con distintos ecosistemas de microcontroladores.  

#### **Conectividad y Expansión**  
La placa de expansión incluye **puertos reservados** para:  
- **Receptor de mando PS2**.  
- **Módulo WiFi/Bluetooth**.  
- **Puerto I2C**, permitiendo la conexión de sensores y actuadores externos.  
- **Puerto Micro USB**, que facilita:  
  - Programación de otros microcontroladores (**Arduino, STM32, STC51**).  
  - Actualización del **firmware** del microcontrolador de bajo nivel.  

#### **Gestión Térmica y Energética**  
- **Interfaz para ventilador de refrigeración**, asegurando una adecuada **gestión térmica** ante la alta demanda de procesamiento de la Jetson Nano.  
- **Alimentación a través de un conector tipo T** para un **adaptador DC12V**.  
- **Interruptor de encendido** para controlar el suministro de energía al robot.  

#### **Interfaz y Control**  
La placa de expansión incorpora:  
- **Botones físicos (K1, K2, RESET)** para:  
  - **Reinicio de servos**.  
  - **Parada de emergencia**.  
  - **Reinicio del coprocesador**.  
- **Indicadores LED** de estado, que muestran:  
  - Estado del **microcontrolador**.  
  - Alimentación de **5V**.  
  - Alimentación de los **servos**.  
  - Conexión **WiFi**.  
- **Luces RGB** controladas por un **coprocesador STM8**, permitiendo efectos visuales para indicar distintos estados del robot.  
- **Zumbador**, proporcionando **retroalimentación audible**.  

#### **Interfaz para Sensores y Actuadores**  
- **Puerto para sensor ultrasónico**, permitiendo **detección de distancia** y **evitación de obstáculos**.  
- **Interfaces PWM para servos estándar**, compatibles con modulación por ancho de pulsos.  
- **Puerto serial** para conexión de módulos **WiFi o Bluetooth**, facilitando la comunicación inalámbrica.  

## Puertos e interfaces de comunicación de elementos
La arquitectura del sistema del Dofbot se caracteriza por la distinción entre la **placa base Jetson Nano **(que proporciona la capacidad de cómputo central y las interfaces de conectividad estándar) y la **placa de expansión personalizada **(que integra interfaces especializadas para el control de los servos, la conexión de la cámara y la adición de otros periféricos necesarios para la funcionalidad del robot). Esta separación de funcionalidades permite a los usuarios adaptar el diseño del robot para satisfacer las demandas específicas del robot, optimizando el hardware más allá de las capacidades genéricas de la placa Jetson Nano.
### Jetson Nano
La placa Jetson Nano cuenta con una variedad de puertos e interfaces diseñados para la conectividad y expansión de periféricos. Dispone de opciones de almacenamiento, alimentación y comunicación. Además, ofrece salidas de video junto con interfaces específicas como GPIO de 40 pines para la conexión de sensores y actuadores, y puertos especializados como I2C, MIPI CSI-2 para cámaras y PWM para control de servomotores. Estas conexiones permiten una integración flexible de dispositivos, facilitando aplicaciones en robótica, inteligencia artificial y visión artificial. A continuación se describe cada uno de los puertos:
- **Interfaz de Tarjeta TF (MicroSD): **Cumple la función primordial de instalar la tarjeta microSD, el cual es el almacenamiento principal para el sistema, el software de control del robot, los archivos de programa y los datos generados o utilizados por el usuario.* Nota: Es útil para la instalación de la imagen del sistema operativo, particularmente en la versión oficial B01 de la Jetson Nano, la cual carece de memoria eMMC integrada.*
- **Interfaz de Extensión GPIO de 40 Pines: **Es una interfaz versátil de propósito general que permite la interconexión con una amplia gama de periféricos de baja velocidad, sensores, actuadores y otros componentes electrónicos. Cada uno de los 40 pines puede configurarse individualmente como una entrada digital para la lectura de señales de sensores o como una salida digital para el control de dispositivos. Además de las capacidades de entrada/salida digital, la interfaz GPIO proporciona acceso a fuentes de alimentación de 3.3V y 5V, útiles para alimentar dispositivos externos, así como a pines de tierra necesarios para completar los circuitos eléctricos. También se incluyen pines dedicados para la implementación de protocolos de comunicación serial, como I2C (utilizado para conectar múltiples dispositivos en un bus) y UART (para la comunicación punto a punto). Algunos de los pines GPIO tienen funciones alternativas, incluyendo PWM.
- **Interfaz Micro USB: **Proporciona alimentación eléctrica a la placa Jetson Nano en configuraciones básicas o facilita la transferencia de datos cuando se conecta a una computadora host. El puerto Micro USB puede suministrar energía a 5V con una corriente máxima de 2A. Adicionalmente, esta interfaz se utiliza para iniciar la Jetson Nano en modo de recuperación, un paso necesario para flashear o instalar el sistema operativo desde una computadora externa.  *Nota: Para proyectos que involucren la conexión de múltiples periféricos, se recomienda el uso de la entrada de alimentación DC dedicada para asegurar un suministro energético estable y suficiente.*
- **Puerto Gigabit Ethernet: **Proporciona conectividad de red de alta velocidad, alcanzando tasas de transferencia de 10/100/1000 Mbps, lo que facilita la comunicación con otros dispositivos dentro de una red local o a través de Internet. Resulta esencial para diversas tareas, como el control remoto del robot utilizando ROS, la transmisión de datos provenientes de sensores a un servidor centralizado o la descarga de actualizaciones de software. En el contexto de aplicaciones de visión artificial, el puerto Ethernet puede utilizarse para recibir flujos de video de fuentes externas o para transmitir el video procesado a otros dispositivos o sistemas. La interfaz Gigabit Ethernet permite la integración del Dofbot en arquitecturas robóticas más complejas o en el ámbito del Internet de las Cosas (IoT).
- **Interfaz USB 3.0: **Permite la conexión de periféricos USB que requieren altas velocidades de transferencia de datos, como cámaras externas de alta resolución, unidades de almacenamiento masivo, teclados y ratones. *Nota: La placa Jetson Nano B01 generalmente incorpora cuatro puertos USB 3.0 de Tipo A. En la variante B01 SUB, el sistema operativo puede iniciarse directamente desde una unidad USB conectada a uno de estos puertos.*
- ** Interfaz HDMI: **Proporciona una salida de video digital de alta definición. Soporta la salida de video en resoluciones de hasta 4K a una frecuencia de actualización de 60Hz. La salida HDMI resulta esencial para la configuración inicial del sistema, la depuración de software y la visualización de los resultados obtenidos en las aplicaciones de visión artificial desarrolladas para el Dofbot.
- **Interfaz DisplayPort: **Similar a la interfaz HDMI, el puerto DisplayPort ofrece otra opción para la salida de video digital de alta definición a monitores y pantallas que sean compatibles con esta conexión. También es capaz de soportar resoluciones de hasta 4K.
- **Interfaz de Alimentación DC (Barrel Jack):** Entrada de alimentación de corriente continua dedicada, diseñada para suministrar la energía necesaria para el funcionamiento de la placa Jetson Nano y de los periféricos que puedan estar conectados a ella. Se recomienda la utilización de una fuente de alimentación de 5V con una capacidad de corriente de 4A  para asegurar un funcionamiento estable y óptimo, especialmente cuando el robot se utiliza en su máximo rendimiento o con una cantidad significativa de periféricos conectados. El conector típicamente presenta un diámetro exterior de 5.5mm y un diámetro interior de 2.1mm. *Nota: La versión Jetson Nano B01 SUB no incluye el interruptor de encabezado de pines para la alimentación DC.*
- **Interfaz de Cámara (MIPI CSI-2): **Permite la conexión directa de módulos de cámara que utilizan la interfaz MIPI CSI-2 diseñado para la transmisión de datos de video de alta velocidad desde sensores de imagen. La placa Jetson Nano generalmente incorpora conectores que soportan hasta 12 carriles de datos MIPI CSI-2, aunque la configuración específica en el Dofbot puede variar. La versión B01 de la placa base cuenta con dos conectores de cámara, cada uno compatible con 2 carriles MIPI CSI-2. La velocidad máxima de datos por carril es de 1.5 Gbps. Esta interfaz es compatible con una variedad de módulos de cámara, incluyendo aquellos basados en el sensor Sony IMX219 de 8 megapíxeles y el Raspberry Pi Camera Module v2. La interfaz MIPI CSI-2 de alta velocidad es fundamental para las aplicaciones de visión artificial del Dofbot, permitiendo la captura de video de alta resolución y la transmisión eficiente de datos a la unidad de procesamiento para su análisis y procesamiento.
- **Interfaz PoE (Power over Ethernet): **Permite que la Jetson Nano reciba alimentación eléctrica y datos de red a través de un único cable Ethernet, simplificando la instalación en ciertos entornos donde una conexión combinada es deseable.

| **Interfaz/Puerto**                  | **Características** |
|:--------------------------------------:|:------------:|
| **Tarjeta TF (MicroSD)**             | Almacenamiento principal para el sistema, software y datos. Necesaria en la Jetson Nano B01 sin eMMC. |
| **GPIO de 40 Pines**                 | Conexión para sensores, actuadores y periféricos. Soporta I2C, UART, PWM y alimentación de 3.3V/5V. |
| **Micro USB**                        | Alimentación de 5V/2A o transferencia de datos. También para flasheo del sistema operativo. |
| **Gigabit Ethernet**                 | Red de alta velocidad (10/100/1000 Mbps). Útil en control remoto, transmisión de datos y visión artificial. |
| **USB 3.0**                          | Conexión de periféricos rápidos (cámaras, almacenamiento, teclado, ratón). En B01 SUB permite arranque desde USB. |
| **HDMI**                             | Salida de video hasta 4K a 60Hz. Clave para configuración, depuración y visión artificial. |
| **DisplayPort**                      | Alternativa a HDMI con soporte hasta 4K. |
| **Alimentación DC (Barrel Jack)**    | Entrada de 5V/4A para estabilidad con múltiples periféricos. Conector de 5.5mm/2.1mm. |
| **Cámara (MIPI CSI-2)**              | Conexión de módulos de cámara de alta velocidad. Esencial en visión artificial. Hasta 1.5 Gbps por carril. |
| **PoE (Power over Ethernet)** | Alimentación y red en un solo cable Ethernet. Facilita la instalación. |

[![Puertos de placa Jetson Nano](2 "Puertos de placa Jetson Nano")](https://m.media-amazon.com/images/I/61hiGnBCTyL._AC_UF350,350_QL80_.jpg "Puertos de placa Jetson Nano")

### Puertos de la Placa de Expansión del Dofbot
La Placa de Expansión del Dofbot Jetson Nano, creada por Yahboom, incorpora diversas interfaces diseñadas para la conexión y control de periféricos esenciales en robótica. Cuenta con puertos para la comunicación inalámbrica mediante módulos WiFi y Bluetooth, así como una interfaz específica para el receptor de mando PS2, permitiendo un control remoto intuitivo. Estas conexiones optimizan la funcionalidad del Dofbot, permitiendo su uso en aplicaciones avanzadas de automatización e inteligencia artificial.
- **Interfaz de Receptor de Mango PS2: **Permite la conexión de un receptor inalámbrico para un mando de juegos PlayStation 2 (PS2), proporcionando una forma intuitiva y familiar de controlar el robot de forma remota.
- **Interfaz de Módulo WiFi/Bluetooth: **Proporciona la conectividad necesaria para integrar un módulo WiFi y/o Bluetooth, habilitando la comunicación inalámbrica con el robot. Esto permite el control remoto del Dofbot a través de diversas plataformas, incluyendo aplicaciones móviles para Android e iOS, software de PC o conexiones inalámbricas directas.
- ** Puerto I2C: **Proporciona una interfaz para la comunicación con dispositivos y sensores que utilizan el protocolo I2C (Inter-Integrated Circuit). Esto facilita la conexión de una amplia gama de sensores compatibles con I2C, como sensores de temperatura, humedad, presión, acelerómetros, giroscopios o incluso pantallas OLED para la visualización de información relevante.
- ** Interfaz de Módulo Ultrasónico: **Esta interfaz permite la conexión de un módulo de sensor ultrasónico. Esto dota al Dofbot con la capacidad de percibir su entorno y, potencialmente, evitar obstáculos o interactuar con objetos basándose en la información de distancia obtenida.
- **Interfaz de Servo de Bus: **Proporciona la conexión para los servos de bus que se utilizan para controlar el movimiento de las articulaciones del brazo robótico . Los servos de bus permiten un control preciso de la posición, la velocidad y el par de cada articulación, lo cual es esencial para la ejecución de movimientos complejos y coordinados. La placa de expansión típicamente reserva 6 interfaces para servos de bus, coincidiendo con el número de servos que componen el brazo robótico del Dofbot (5 de 15KG y 1 de 6KG). 
- **Interfaz de Servo PWM: **Además de las interfaces para servos de bus, la placa de expansión también incluye interfaces para conectar servos que se controlan mediante PWM. Se reservan 6 interfaces de servo PWM, lo que proporciona una flexibilidad adicional para la conexión de actuadores adicionales al robot en caso de ser necesario.

| **Interfaz/Puerto**              | **Características** |
|:----------------------------------:|:------------:|
| **Receptor de Mango PS2**       | Conexión de mando PS2 para control remoto. |
| **Módulo WiFi/Bluetooth**       | Habilita comunicación inalámbrica vía WiFi o Bluetooth. |
| **Puerto I2C**                  | Comunicación con sensores y dispositivos I2C. |
| **Módulo Ultrasónico**          | Conexión de sensor ultrasónico para detección de distancia. |
| **Servo de Bus**                | Control preciso de 6 servos para articulaciones del brazo robótico. |
| **Servo PWM**                   | Control de hasta 6 servos mediante señales PWM. |

[![Puertos de la Placa de Expansión del Dofbot](3 "Puertos de la Placa de Expansión del Dofbot")](https://cdn.shopify.com/s/files/1/0066/9686/1780/files/RaspberryPi_DOFBOT_Yahboom_16.jpg?v=1715937639 "Puertos de la Placa de Expansión del Dofbot")

*Diagrama de bloques de conexión*

```seq
    participant JetsonNano as Jetson Nano
    participant ExpansionBoard as Placa de Expansión
    participant GPIO_Serial as Dispositivo Externo (GPIO/Serial)
    participant Camera as Cámara (USB)
    participant Ethernet as Ethernet
    participant HDMI as Pantalla (HDMI)
    participant MicroUSB as Micro USB
    participant PWM_Servo as Servomotor (PWM Servo)
    participant Bus_Servo as Bus de Servos (Bus Servo)
    participant PS2Handle as Control PS2
    participant WiFi_Bluetooth as WiFi/Bluetooth
    participant Ultrasonic as Sensor Ultrasonido

    JetsonNano->>ExpansionBoard: Comunicación con la placa de expansión

    JetsonNano->>GPIO_Serial: GPIO/Serial
    GPIO_Serial-->>JetsonNano: Comunicación de datos

    JetsonNano->>Camera: USB
    Camera-->>JetsonNano: Transmisión de video

    JetsonNano->>Ethernet: Ethernet
    Ethernet-->>JetsonNano: Conexión a red

    JetsonNano->>HDMI: HDMI
    HDMI-->>JetsonNano: Señal de video

    JetsonNano->>MicroUSB: Micro USB
    MicroUSB-->>JetsonNano: Transferencia de datos

    JetsonNano->>PWM_Servo: PWM Servo
    PWM_Servo-->>JetsonNano: Control de servomotores

    JetsonNano->>Bus_Servo: Bus Servo
    Bus_Servo-->>JetsonNano: Comunicación con servos

    JetsonNano->>PS2Handle: PS2 Handle
    PS2Handle-->>JetsonNano: Entrada de control

    JetsonNano->>WiFi_Bluetooth: WiFi/Bluetooth
    WiFi_Bluetooth-->>JetsonNano: Comunicación inalámbrica

    JetsonNano->>Ultrasonic: Sensor Ultrasonido
    Ultrasonic-->>JetsonNano: Lectura de distancia
```




##***Descripción de software***
Para el control del Dofbot, se utilizarán diversos softwares para facilitar la programación y la interacción con el robot. Uno de los principales será JupyterLab, un entorno de desarrollo que nos permite visualizar y ejecutar código de manera sencilla. Este entorno facilita la escritura y comprensión de funciones con Python3, lo que mejora la experiencia de programación y el desarrollo de proyectos.

## JupyterLab

JupyterLab es una herramienta esencial que permite escribir, visualizar y ejecutar código de manera sencilla. Es un entorno muy adecuado para trabajar con Python3, facilitando la creación de scripts, la depuración y la ejecución del código de forma interactiva. Los participantes aprenderán a utilizar esta herramienta para desarrollar y ejecutar funciones que controlen las acciones y movimientos del robot.

## Programación del Movimiento y Funciones Esenciales del Dofbot

La programación inicial del Dofbot se centrará en diversas actividades que ayudarán a entender el control básico del robot. Estas actividades incluyen:

- **Manipulación de luces RGB**: Se enseñará a programar y controlar las luces RGB del robot para ofrecer un entendimiento de cómo controlar componentes básicos.
- **Control de servos individuales y combinados**: Los participantes aprenderán a controlar servos de manera individual y combinada para lograr el movimiento del robot.
- **Ejecución de movimientos básicos y acciones preprogramadas**: Se podrán crear secuencias de baile, funciones de memoria o cualquier otro tipo de movimiento básico que se pueda preprogramar en el robot.

Además, se profundizará en la **manipulación de objetos** mediante el uso del brazo robótico. Esto permitirá a los participantes experimentar con la programación de tareas más complejas, como el agarre de objetos, y sienta las bases para que el robot interactúe físicamente con su entorno.

## Visión Artificial con OpenCV

En el ámbito de la visión artificial, se empleará **OpenCV**, una de las bibliotecas más utilizadas para el procesamiento de imágenes y análisis visual. Con esta herramienta, el Dofbot podrá realizar tareas como:

- **Detección de colores**: El robot podrá identificar diferentes colores en su entorno y reaccionar en consecuencia.
- **Reconocimiento facial**: Se podrá programar para que el Dofbot reconozca caras y realice acciones basadas en este reconocimiento.
- **Análisis de gestos**: Utilizando la visión por computadora, se podrá reconocer diferentes gestos y realizar acciones basadas en ellos.

Además, se utilizará **Jetson-inference**, que aprovecha la capacidad de procesamiento de la **Jetson Nano** para ejecutar modelos de inteligencia artificial en tiempo real. Esta tecnología permitirá que el Dofbot pueda:

- Clasificar imágenes
- Detectar objetos
- Realizar segmentación semántica de una manera más eficiente, gracias a la aceleración de hardware proporcionada por la plataforma Jetson Nano.

## Control PID para Seguimiento

Para mejorar la capacidad de respuesta del robot en tareas de seguimiento, se implementará un **sistema de control PID** (Proporcional-Integral-Derivativo). Este sistema permitirá un seguimiento preciso de objetos y rostros basándose en características visuales, lo que facilitará movimientos más estables y eficientes en la interacción del Dofbot con su entorno.

Con el control PID, el robot será capaz de:

- Ajustar su posición de manera precisa en función de los datos obtenidos por la cámara.
- Realizar movimientos más estables y eficientes en la interacción con su entorno.

Además, el sistema de visión artificial será esencial para tareas de manipulación, como **agarrar y apilar bloques** basados en el color de los mismos o los gestos detectados por la cámara.

## Integración con ROS

La integración con **ROS (Robot Operating System)** será un componente clave para ampliar las capacidades del robot. **ROS** proporciona un marco robusto para desarrollar aplicaciones robóticas complejas, permitiendo que los diferentes módulos del robot puedan comunicarse entre sí de manera eficiente.

Se introducirá a los participantes en el uso de **ROS básico**, proporcionándoles las herramientas necesarias para la comunicación entre los distintos módulos del Dofbot. Posteriormente, se combinará ROS con OpenCV, lo que permitirá a los participantes desarrollar sistemas más avanzados que integren visión artificial con las funciones de movimiento y manipulación del robot. Esta combinación de herramientas es fundamental en la robótica moderna, ya que permite desarrollar sistemas autónomos más sofisticados.

## Control Avanzado con MoveIt

Para los participantes que busquen un control más avanzado del movimiento del robot, se utilizará **MoveIt**, una herramienta especializada en la planificación de trayectorias y la cinemática del brazo robótico. **MoveIt** es una herramienta muy poderosa que permite gestionar la planificación de movimientos complejos para brazos robóticos y otros actuadores.

En esta parte del curso, se explorarán conceptos avanzados como:

- **Detección de colisiones**: Asegurar que el brazo robótico no entre en contacto con objetos u obstáculos en su entorno.
- **Optimización de rutas**: Buscar las rutas más eficientes para que el robot realice movimientos precisos sin perder tiempo ni recursos.

Esto permitirá que el Dofbot ejecute movimientos más precisos y se adapte a su entorno de manera eficiente.



## Procedimiento de encendido, operación y apagado del robot

### Encendido
1. Verificar el cableado.
2. Asegurarse de que las conexiones de la fuente de alimentación sean correctas.
3. Encender el interruptor de alimentación.
4. Esperar a que la pantalla OLED muestre información del sistema.
5. Esperar a que el zumbador emita tres pitidos.

### Apagado
Un método seguro para apagar la Jetson Nano es utilizar el siguiente comando en la terminal:

``` bash
sudo shutdown -h now
```

O alternativamente:

```bash
sudo shutdown --poweroff
```

Este comando permite que el sistema cierre correctamente todos los procesos en ejecución, evitando así la posible corrupción de datos.

### Operación
- Los usuarios pueden controlar el robot a través de:
  - Una aplicación móvil para Android/iOS.
  - Una computadora personal.
  - Un mando de juegos.
- Se puede utilizar la interfaz JupyterLab como plataforma para ejecutar código.
- El robot permite el aprendizaje y almacenamiento de grupos de acciones fijas personalizadas.
- Se integra con **ROS (Robot Operating System)**, lo que simplifica el control de movimiento de los servos de bus serie.
- Se ofrecen cursos básicos y avanzados sobre **ROS**.

## Restricciones de software, hardware y mecánicas del robot

### Hardware
- Requiere una fuente de alimentación con un voltaje de **100~240V** y una frecuencia de **50/60Hz**.
- La Jetson Nano tiene modos de energía de **5W y 10W** (por defecto).
- Existen herramientas como `jtop` y `tegrastats` para monitorizar el consumo de energía de la Jetson Nano.
- La corriente máxima que puede manejar la Jetson Nano 2GB es de **5A**, aunque se recomienda una fuente de **3A o superior**.
- La Jetson Nano dispone de puertos **USB 3.0** para conectar dispositivos externos.
- Se aconseja utilizar **hubs USB con alimentación externa** para periféricos que consumen mucha energía y evitar sobrecargar la fuente de alimentación.

### Software
- El entorno de software del **DOFBOT-JetsonNANO** se basa en **Python3** como lenguaje de programación principal, especialmente en el contexto de **ROS**.
- Se facilita la ejecución de código a través de **JupyterLab**.
- La integración con **ROS** simplifica el control del movimiento.
- **OpenCV** se utiliza para el procesamiento de imágenes.

### Mecánicas
- La **calibración de servos** es fundamental para establecer límites y ajustar parámetros que garanticen un movimiento adecuado y seguro dentro de su rango operativo.
- Precisión de posicionamiento repetido: **±0.5mm**.
- No hay una especificación oficial clara sobre la capacidad de peso del robot, aunque se menciona una misión de recolección de minerales de hasta **1kg**.
- Un video sobre la calibración de servos destaca la importancia de asegurar que la ventosa inferior esté correctamente adherida para una operación estable.
- La construcción mecánica es sólida, y la estabilidad proporcionada por las ventosas es un aspecto positivo para la experimentación.
- La ausencia de una especificación clara sobre la capacidad de carga representa una limitación en la información disponible para los usuarios.

## Conclusión
El **Yahboom DOFBOT-JetsonNANO** se presenta como una plataforma versátil y accesible, especialmente diseñada para aquellos que se inician en el mundo de la inteligencia artificial y la robótica. Sus características clave incluyen capacidades avanzadas de visión artificial, una construcción mecánica robusta y múltiples opciones de control. Se recomienda a los usuarios explorar a fondo los cursos y tutoriales en línea proporcionados por *Yahboom* para aprovechar al máximo las funcionalidades del robot. Es importante prestar especial atención a las instrucciones de ensamblaje y al proceso de calibración de los servos para asegurar un funcionamiento óptimo. Asimismo, se aconseja seguir los procedimientos adecuados para el encendido y apagado de la *Jetson Nano* para evitar posibles problemas. La variedad de métodos de control permite a los usuarios experimentar con el robot de diversas maneras. Para aquellos que deseen profundizar en la robótica, la integración con **ROS** ofrece un camino para proyectos más avanzados.

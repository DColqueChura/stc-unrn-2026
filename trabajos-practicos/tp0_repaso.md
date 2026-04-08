## Temas abordados

## Consigna 1:  Modelo OSI
### A. Describa y brinde ejemplos de aplicación de los siguientes conceptos en relación a sistemas de comunicación:
- Unicast
- Multicast
- Broadcast

| Conceptos | Descripciones | Protocolo | Ejemplos |
|------|-------------|-------------|-------------|
| Unicast / Unidifusión | Transmisiones uno-a-uno | TCP (Protocolo de control de transmisión) o UDP | Un usuario solicita información de un servidor, sitio web u otro usuario, y la otra parte la envía después de establecer una conexión única. |
| Multicast / Multidifusión | Similar al broadcast, sólo que en multicast se envía a un grupo específico. | UDP (Protocolo de datagramas de usuario) | En sistemas de video vigilancia. Si hay 4 operadores, cada uno en su computadora, viendo el video de la misma cámara, Si se configura a la cámara con Multicast solo envías un flujo a los 4 operadores, los switches ya se encargan de replicar el flujo a los puertos que lo requieren (no a todos). |
| Broadcast / Difusión | Difunde la información de forma simultánea a todos los nodos de red.  | UDP | Un canal de radio o televisión. |

Algo en común: **Todas se utilizan para reenviar paquetes en una red.** 

### B. ¿Cuál es la diferencia entre un sistema de comunicaciones Half-duplex y uno Full-duplex?

La diferencia principal está en cómo fluye la comunicación entre dos extremos: \
`Half-duplex`: la comunicación puede ir en ambas direcciones, pero por turnos. \
***Idea clave**: “Ahora hablo yo, luego hablas tú”*. 

Ejemplo mental: un walkie-talkie \
Si una persona está hablando, la otra debe esperar para responder. 

`Full-duplex`: la comunicación puede ir en ambas direcciones simultáneamente. \
***Idea clave**: “Yo hablo mientras tú también hablas”*.

Ejemplo mental: una llamada telefónica moderna:
ambas personas pueden hablar y escucharse simultáneamente.

|  | Diferencia principal | Dirección de comunicación |Uso del canal |Eficiencia |Riesgo de colisiones / interferencia de acceso |
|-------|-------|------|-------------------|-------------|-------------|
| Half-duplex | Solo hay una dirección activa a la vez. Requiere algún mecanismo para decidir quién transmite y cuándo. | Ambas direcciones, pero por turnos | Compartido en el tiempo |Menor | Más probable si varios comparten el medio |
| Full-duplex | Hay dos direcciones activas simultáneamente. No hace falta “esperar turno” entre los dos extremos del enlace. | Ambas direcciones al mismo tiempo | Separado o simultáneo |Mayor | Mucho menor en enlaces punto a punto |

Fuente : CCNA oficial

### c. Realice una comparación entre los modelos de referencia TCP/IP y OSI.

| Capa | OSI | TCP/IP |
|------|-------------|-------------|
| Capa 7 | Aplicación | Aplicación |
| Capa 6 | Presentación | No tiene capa específica |
| Capa 5 | Sesión | No tiene capa específica |
| Capa 4 | Transporte | Transporte |
| Capa 3 | Red | Internet |
| Capa 2 | Enlace de datos | Acceso a la red |
| Capa 1 | Física | Acceso a la red |   

Aunque ambos modelos tienen capas que cumplen funciones similares, el modelo OSI es más detallado y teórico, mientras que el modelo TCP/IP es más práctico y se utiliza ampliamente en la implementación de redes reales. El modelo OSI se enfoca en la estandarización de protocolos y la interoperabilidad, mientras que el modelo TCP/IP se centra en la comunicación efectiva a través de Internet.

Por ejemplo, el modelo OSI tiene capas específicas para la presentación y sesión, mientras que el modelo TCP/IP no las tiene y asume que estas funciones se manejan dentro de la capa de aplicación. Además, el modelo OSI es un marco de referencia más general, mientras que el modelo TCP/IP se desarrolló específicamente para la comunicación en redes basadas en Internet.

**Curiosidad**: el modelo OSI fue desarrollado por la Organización Internacional de Normalización (ISO) en la década de 1980, mientras que el modelo TCP/IP fue desarrollado por el Departamento de Defensa de los Estados Unidos en la década de 1970.

### d. ¿A qué nivel del modelo OSI funciona cada dispositivo? Describa brevemente el principio de operación de cada uno.
- Router: Funciona a nivel de la capa 3 (Red).
- Hub: Funciona a nivel de la capa 1 (Física).
- Switch: Funciona a nivel de la capa 2 (Enlace de datos).

`Router`: Es un dispositivo que se encarga de dirigir el tráfico de datos entre diferentes redes. Utiliza tablas de enrutamiento para determinar la mejor ruta para enviar los paquetes de datos a su destino. Opera en la capa de red (capa 3) del modelo OSI, lo que le permite manejar direcciones IP y tomar decisiones basadas en la información de la red.

`Hub`: Es un dispositivo de red que se utiliza para conectar varios dispositivos en una red local (LAN). Funciona a nivel de la capa física (capa 1) del modelo OSI. Un hub simplemente recibe los datos de un dispositivo y los transmite a todos los demás dispositivos conectados al hub, sin realizar ningún tipo de filtrado o direccionamiento.

`Switch`: Es un dispositivo de red que también se utiliza para conectar varios dispositivos en una red local (LAN). Funciona a nivel de la capa de enlace de datos (capa 2) del modelo OSI. A diferencia de un hub, un switch es capaz de filtrar y dirigir los datos solo al dispositivo específico al que están destinados, utilizando direcciones MAC para identificar los dispositivos en la red. Esto mejora la eficiencia y reduce las colisiones en la red.

### e. Mencione las principales diferencias entre TCP y UDP.
| Característica | TCP (Protocolo de Control de Transmisión) | UDP (Protocolo de Datagramas de Usuario) |
|----------------|-------------------------------------------|-----------------------------------------|
| Conexión | Orientado a la conexión (requiere establecer una conexión antes de transmitir datos) | No orientado a la conexión (no requiere establecer una conexión) |
| Fiabilidad | Proporciona fiabilidad mediante el uso de acuses de recibo, retransmisiones y control de flujo | No proporciona fiabilidad, los datos pueden perderse o llegar fuera de orden |
| Velocidad | Más lento debido a la sobrecarga de control y verificación | Más rápido debido a la falta de control y verificación |
| Uso típico | Aplicaciones que requieren fiabilidad, como correo electrónico, transferencia de archivos y navegación web | Aplicaciones que requieren velocidad y pueden tolerar la pérdida de datos, como transmisión de video en tiempo real, juegos en línea y VoIP |
| Tamaño del encabezado | Más grande (20 bytes) debido a la información de control adicional | Más pequeño (8 bytes) debido a la falta de información de control |
| Control de flujo | Sí, utiliza ventanas para controlar el flujo de datos | No, no tiene control de flujo |
| Control de congestión | Sí, ajusta la velocidad de transmisión en función de la congestión de la red | No, no ajusta la velocidad de transmisión en función de la congestión de la red |  

Definiciones: \
`TCP (Protocolo de Control de Transmisión)` es un protocolo de comunicación orientado a la conexión que garantiza la entrega confiable de datos entre dispositivos en una red. Proporciona mecanismos para el control de flujo, la corrección de errores y la retransmisión de datos perdidos. \
`UDP (Protocolo de Datagramas de Usuario)` es un protocolo de comunicación no orientado a la conexión que permite la transmisión de datos sin garantizar su entrega. No proporciona mecanismos de control de flujo ni corrección de errores, lo que lo hace más rápido pero menos confiable que TCP.

Fuente: CCNA oficial

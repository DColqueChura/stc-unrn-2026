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
| Broadcast / Difusión | Difunde la información de forma simultánea a todos los nodos de red.  | UDP | La resolución de direcciones con ARP (Address Resolution Protocol) Y La asignación de IPs por DHCP, donde un paquete se envía obligatoriamente a todos los hosts de la LAN (dirección MAC FF:FF:FF:FF:FF:FF) |

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

### C. Realice una comparación entre los modelos de referencia TCP/IP y OSI.

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

### D. ¿A qué nivel del modelo OSI funciona cada dispositivo? Describa brevemente el principio de operación de cada uno.
- Hub: Funciona a nivel de la capa 1 (Física).
- Switch: Funciona a nivel de la capa 2 (Enlace de datos).
- Router: Funciona a nivel de la capa 3 (Red).


`Hub`: Es un dispositivo de red(*) que se utiliza para conectar varios dispositivos en una red local (LAN). Funciona a nivel de la capa física (capa 1) del modelo OSI. Un hub simplemente recibe los datos de un dispositivo y los transmite a todos los demás dispositivos conectados al hub, sin realizar ningún tipo de filtrado o direccionamiento.

`Switch`: Es un dispositivo de red que también se utiliza para conectar varios dispositivos en una red local (LAN). Funciona a nivel de la capa de enlace de datos (capa 2) del modelo OSI. A diferencia de un hub, un switch es capaz de filtrar y dirigir los datos solo al dispositivo específico al que están destinados, utilizando "Tabla MAC" o "CAM Table" para identificar los dispositivos en la red (el switch aprende dinámicamente qué dirección MAC está en cada puerto físico leyendo las tramas entrantes). Esto mejora la eficiencia y reduce las colisiones en la red.

`Router`: Es un dispositivo que se encarga de dirigir el tráfico de datos entre diferentes redes. Utiliza tablas de enrutamiento para determinar la mejor ruta para enviar los paquetes de datos a su destino. Opera en la capa de red (capa 3) del modelo OSI, lo que le permite manejar direcciones IP y tomar decisiones basadas en la información de la red.

(*) El hub se considera dispositivo de red porque hace posible la **infraestructura física de la red**, actuando como el punto central de unión.

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

## Consigna 2: Modulación digital
### A. ¿Qué diferencias existen entre una transmisión en banda base y una pasabanda? ¿Cómo se obtiene una a partir de la otra?

`Banda Base (Baseband)`: Es la señal digital o analógica tal cual sale de la fuente, sin sufrir ninguna modulación en frecuencia. Su espectro de frecuencias está centrada en 0 Hz (DC).

    Ejemplo: El tren de pulsos binarios que sale de un microcontrolador, o la señal de audio de un micrófono. No se puede propagar eficientemente por el aire mediante antenas porque requeriría antenas del tamaño de kilómetros.

`Pasabanda (Passband / Banda de Paso)`: Es una señal que ha sido desplazada en frecuencia hacia una banda superior, centrada alrededor de una frecuencia portadora (fc). Su espectro no toca el cero. Esto permite sintonizar diferentes canales en un mismo medio físico (FDM) y transmitir de forma inalámbrica de manera eficiente.

`¿Cómo se obtiene una a partir de la otra?`
- **De Banda Base a Pasabanda (Modulación)**: Se multiplica (mezcla) la señal de banda base (moduladora) por una señal senoidal de alta frecuencia (portadora). En sistemas digitales, los bits modifican la amplitud (ASK), fase (PSK) o frecuencia (FSK) de esa portadora.

- **De Pasabanda a Banda Base (Demodulación)**: En el receptor se realiza el proceso inverso (generalmente multiplicando de nuevo por la frecuencia portadora local y aplicando un filtro pasa-bajos) para recuperar la señal original de datos en banda base.

### B. Describa en forma conceptual cómo se determina el ancho de banda de transmisión en un esquema basado en:
- BASK
- BPSK
- BFSK

Para calcular el espacio que la señal va a ocupar en el aire (el BW), primero se necesita saber cuántos "paquetes" de información se  envía por segundo.
La "B" al principio de BASK, BPSK y BFSK significa Binary (Binario). Esto implica que el sistema **envía dentro de un símbolo, un solo bit**. 

Matemáticamente: $R_s = R_b$ (*) 

**Explicación Matemática**

$M = 2 \quad \text{(Símbolos posibles: Binario)}$ \
$k = log_2(M) \implies k = log_2(2) \implies k = 1 \text{ bit/símbolo}$ \
Ahora, la relación entre la Tasa de Símbolos ($R_s$) y la Tasa de Bits ($R_b$) se define formalmente como: \
$R_b = k \cdot R_s$ \
Como ya demostramos que $k = 1$: \
$R_b = 1 \cdot R_s \implies R_b = R_s$

`¿Cómo se relaciona esto con el Ancho de Banda (BW)?` \
El ancho de banda es, literalmente, el "ancho de la carretera" que necesitas para que tus símbolos viajen sin chocarse ni deformarse. \
Como los símbolos cambian a una velocidad de $R_s$ veces por segundo, esa velocidad de cambio genera frecuencias. Cuanto más rápido cambien los símbolos (mayor $R_s$), más rápido cambia la señal y **más ancho de banda necesitas**.

`BASK`: El `1` es una onda y el `0` es silencio (o una onda más chica). \
`BPSK`: El `1` es una onda normal y el `0` es la misma onda pero invertida (cambio de fase). \
`BFSK`: Aquí usas dos frecuencias $f_c$ distintas (una para el `1` y otra para el `0`). El ancho de banda no solo depende de la velocidad de conmutación ($R_s$), sino también de **qué tan separadas estén esas dos frecuencias entre sí** ($\Delta f = |f_1 - f_0|$). Por eso, BFSK suele ocupar más espacio en el espectro que BASK o BPSK.

- Para `BASK` y `BPSK`, el $BW = 2*R_S$ (o simplemente $R_s$ si se considera el ancho de banda de Nyquist ideal con filtros de coseno realzado perfectos).
- Para `BFSK`, el $BW \approx \Delta f + 2 \cdot R_s$ (o por la regla de Carson).

(*) 
- **Tasa de bits ($R_b$**) : es cuántos ceros y unos se transmiten en un segundo     (bits por segundo, bps).
- **Tasa de símbolos ($R_s$**): es cuántos símbolos se transmiten en un segundo (baudios, bauds).
### C. ¿Qué efectos tienen los siguientes fenómenos sobre un diagrama de constelación?
- AWGN
- Errores de fase
- Atenuación del canal

El diagrama de constelación muestra los puntos de señal en el plano Complejo (I/Q - En fase y Cuadratura).

`AWGN (Ruido Blanco Gaussiano Aditivo)` **Efecto**: Añade pequeñas variaciones aleatorias tanto en amplitud como en fase a cada símbolo. En la constelación, los puntos ideales dejan de ser "puntos perfectos" y se convierten en **nubes difusas o círculos borrosos** alrededor del lugar ideal. \
A mayor ruido (menor SNR), más grandes las nubes, provocando que se superpongan y generen errores de bit. 

`Errores de fase (Phase jitter / Desplazamiento de fase)` **Efecto**: Afectan el ángulo del vector de la señal pero no su longitud (amplitud). En la constelación, los puntos se ven **rotados o estirados en forma de arco circular** alrededor del origen (0,0). 

`Atenuación del canal` **Efecto**: Reduce la amplitud (magnitud) de la señal recibida uniformemente. En la constelación, todos los puntos **se encogen hacia el origen (0,0)**, reduciendo la distancia entre ellos y haciéndolos más vulnerables al ruido.
### D. Compare las constelaciones de 16-QAM y 16-APSK.
Ambas transmiten 16 símbolos posibles (4 bits por símbolo), pero la geometría de distribución de sus puntos es radicalmente distinta:

`16-QAM (Quadrature Amplitude Modulation)`: Sus puntos se distribuyen en una grilla u ordenamiento rectangular regular (matriz de 4x4).
- **Ventaja**: Es más fácil de implementar y modular/demodular en circuitos digitales. Tiene una excelente distancia de separación entre puntos en entornos lineales.
- **Desventaja**: Tiene una alta variación de envolvente (PAPR elevado). Esto significa que hay mucha diferencia de potencia entre los puntos de las esquinas y los del centro. Si pasa por un amplificador de alta potencia no lineal (como los de los satélites), la señal se distorsiona horriblemente.

`16-APSK (Amplitude and Phase Shift Keying)`: Sus puntos se organizan en anillos concéntricos (por ejemplo, un anillo interno de 4 puntos y un anillo externo de 12 puntos).
- **Ventaja**: Al estar distribuidos en círculos concéntricos de amplitudes fijas, presenta variaciones de amplitud mucho más controladas. Es altamente inmune a las no linealidades de los amplificadores, por lo que es el estándar indiscutido en transmisiones satelitales (como DVB-S2).

### E. Compare los conceptos de operación del filtro adaptado y el receptor de correlación.
Ambos son receptores óptimos en presencia de ruido AWGN; matemáticamente se demuestra que son equivalentes (dan exactamente la misma probabilidad de error), pero su implementación física y estructural es diferente:

`Filtro Correlador (o Receptor de Correlación)`: Requiere un oscilador local en el receptor que esté **perfectamente sincronizado en tiempo y fase** con la señal que viene del transmisor. 
- **Operación**: Multiplica la señal recibida por esta réplica local y luego se integra durante el período del símbolo ($T$).

`Filtro Adaptado (Matched Filter)`: No necesita generar una réplica de la señal en tiempo real; es un filtro físico (un circuito con componentes) cuya respuesta al impulso $h(t)$ es una versión invertida en el tiempo y desplazada del pulso de señal esperado $s(t)$, es decir, $h(t) = s(T - t)$. 
- **Operación**: La señal recibida pasa a través del filtro (operación de convolución). El filtro está diseñado para que, justo en el instante de muestreo $t = T$, la salida alcance su valor máximo de Relación Señal a Ruido (SNR).

### F. De una breve descripción del principio de funcionamiento de DSSS y FHSS. Mencione las principales ventajas y desventajas de los sistemas basados en espectro esparcido.

Las técnicas de espectro esparcido buscan transmitir una señal ocupando un ancho de banda muchísimo mayor que el mínimo necesario manteniendo la misma potencia de señal, así volviéndola inmune a interferencias.

`DSSS (Direct Sequence Spread Spectrum)`: Cada bit de datos se multiplica por una secuencia de código pseudoaleatorio (PN) de alta velocidad llamada bits de chip (o chipping code). Esto "estira" la señal en el dominio de la frecuencia, haciendo que parezca ruido de fondo para receptores no autorizados. El receptor original, al conocer el código, vuelve a multiplicar la señal y concentra la energía original.

`FHSS (Frequency Hopping Spread Spectrum)`: La señal de datos modula una portadora que va saltando de frecuencia constantemente a lo largo de un rango amplio de canales, siguiendo un patrón pseudoaleatorio determinado.

`Ventajas`
- **Inmunidad al ruido y a interferencias de banda angosta**: Si alguien interfiere una frecuencia específica, en DSSS solo afecta a una fracción mínima de la energía y en FHSS solo arruina el salto momentáneo que cayó ahí.
- **Seguridad / Baja probabilidad de interceptación**: La señal se camufla con el ruido térmico.
- **Acceso Múltiple**: Permite que varios usuarios usen la misma banda al mismo tiempo usando códigos distintos (CDMA).

`Desventajas`
- Requiere un **ancho de banda masivo**.
- Sistemas de **sincronismo extremadamente complejos** entre $T_x y R_x$ para alinearse con los códigos o los saltos de frecuencia.
## Temas abordados

## Consigna 1:  Modelo OSI
a. Describa y brinde ejemplos de aplicación de los siguientes conceptos en relación a sistemas de comunicación:
- Unicast
- Multicast
- Broadcast

| Conceptos | Descripciones | Protocolo | Ejemplos |
|------|-------------|-------------|-------------|
| Unicast / Unidifusión | Transmisiones uno-a-uno | TCP (Protocolo de control de transmisión) o UDP | Un usuario solicita información de un servidor, sitio web u otro usuario, y la otra parte la envía después de establecer una conexión única. |
| Multicast / Multidifusión | Similar al broadcast, sólo que en multicast se envía a un grupo específico. | UDP (Protocolo de datagramas de usuario) | En sistemas de video vigilancia. Si hay 4 operadores, cada uno en su computadora, viendo el video de la misma cámara, Si se configura a la cámara con Multicast solo envías un flujo a los 4 operadores, los switches ya se encargan de replicar el flujo a los puertos que lo requieren (no a todos). |
| Broadcast / Difusión | Difunde la información de forma simultánea a todos los nodos de red.  | UDP | |

Algo en común: **Todas se utilizan para reenviar paquetes en una red.** 

b. ¿Cuál es la diferencia entre un sistema de comunicaciones Half-duplex y uno Full-duplex?

c. Realice una comparación entre los modelos de referencia TCP/IP y OSI.

d. ¿A qué nivel del modelo OSI funciona cada dispositivo? Describa brevemente el principio de operación de cada uno.
- Router
- Hub
- Switch

e. Mencione las principales diferencias entre TCP y UDP.
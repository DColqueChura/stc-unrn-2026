**MACA** significa **Multiple Access with Collision Avoidance** (Acceso Múltiple con Prevención de Colisiones). Es, por así decirlo, el antepasado directo y la base teórica sobre la que se construyó el mecanismo **CSMA/CA** que usamos hoy en día en el Wi-Fi.

Fue propuesto en 1990 por Phil Karn para resolver un problema crítico en las redes inalámbricas que los cables no tenían: **el problema del nodo oculto**.

Aquí te explico cómo se relacionan, en qué se diferencian y por qué pasamos de uno a otro:

---

### La gran diferencia: ¿Escuchar o no escuchar?

La diferencia fundamental entre MACA y CSMA/CA radica en el **Carrier Sensing** (Detección de Portadora), es decir, en el acto de "escuchar" el aire antes de hablar.

* **MACA (Sin detección de portadora):** MACA **no escucha** el canal antes de transmitir. Confía ciegamente en un intercambio de tres vías (señalización) para apartar el canal.
* **CSMA/CA (Con detección de portadora):** Es una evolución que **sí escucha** el canal primero (el "CS" de CSMA). Si el canal está ocupado, se espera; si está libre, inicia el protocolo.

---

### ¿Cómo funciona MACA? (El origen de RTS/CTS)

Como MACA no podía escuchar el canal, introdujo por primera vez el famoso diálogo de tres vías para evitar colisiones:

1. **RTS (Request to Send):** La estación $A$ quiere hablar con $B$, así que le envía un paquete corto llamado RTS. Las estaciones cercanas a $A$ escuchan este RTS y se quedan calladas.
2. **CTS (Clear to Send):** La estación $B$ responde con un CTS. Las estaciones cercanas a $B$ (que quizás no escucharon a $A$, es decir, **nodos ocultos**) escuchan el CTS y se dan cuenta de que $B$ va a recibir datos, así que se quedan calladas.
3. **DATA:** La estación $A$ transmite sus datos de forma segura.

> **El problema de MACA:** Al no requerir un **ACK** (acuse de recibo) al final de la transmisión en la capa MAC, si el paquete de datos se corrompía por interferencia externa, la capa MAC no se enteraba. La recuperación del paquete dependía de capas superiores (como TCP), lo que hacía el proceso muy lento.

---

### ¿Por qué CSMA/CA es mejor?

El estándar Wi-Fi (802.11) tomó la idea de MACA pero la mejoró drásticamente para crear **CSMA/CA** añadiendo dos componentes vitales:

1. **Detección de Portadora (Carrier Sense):** Antes de mandar un RTS, el dispositivo escucha el aire. Si ya hay una transmisión en curso, ni siquiera gasta energía enviando el RTS, reduciendo drásticamente las colisiones de control.
2. **Acuse de Recibo (ACK):** CSMA/CA convirtió el proceso en un saludo de 4 vías (RTS $\rightarrow$ CTS $\rightarrow$ DATA $\rightarrow$ **ACK**). Si el ACK no llega inmediatamente, la tarjeta de red sabe que el paquete se perdió y lo retransmite en milisegundos, sin esperar a que TCP se dé cuenta.

### Resumen comparativo

| Característica | MACA (Protocolo Base) | CSMA/CA (Estándar Actual) |
| --- | --- | --- |
| **¿Escucha el canal antes?** | No. Envía el RTS directamente. | **Sí.** Solo envía si el canal se percibe libre. |
| **Flujo de paquetes** | RTS $\rightarrow$ CTS $\rightarrow$ DATA | RTS $\rightarrow$ CTS $\rightarrow$ DATA $\rightarrow$ **ACK** |
| **Uso de RTS/CTS** | Obligatorio siempre. | **Opcional.** Se usa solo para paquetes grandes o cuando se activa para mitigar nodos ocultos. |
| **Eficiencia** | Baja en canales muy congestionados. | Alta, gracias al algoritmo de espera aleatoria (*Backoff*). |
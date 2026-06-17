En el mundo de las telecomunicaciones y las redes, **MPDU** significa **Mac Protocol Data Unit** (Unidad de Datos de Protocolo de MAC).

Para entenderlo de forma sencilla: es el paquete de datos que se genera y se maneja específicamente en la capa **MAC (Medium Access Control)**, la cual es una subcapa de la Capa 2 (Enlace de Datos) del modelo OSI.

Aquí te explico cómo funciona y por qué es importante:

---

### ¿Cómo se forma una MPDU?

Cuando los datos bajan desde las capas superiores (como internet o aplicaciones) hacia la tarjeta de red, pasan por un proceso de "envoltura" o encapsulamiento:

1. **La carga útil (MSDU):** Los datos que vienen de arriba se conocen como **MSDU** (*Mac Service Data Unit*).
2. **El empaque (MPDU):** La capa MAC toma esa MSDU y le agrega su propia información de control: una cabecera (*MAC Header*) al principio y, generalmente, una cola de verificación (*MAC Footer/Trailer*) al final.

> **Fórmula básica:** > $\text{MPDU} = \text{Cabecera MAC} + \text{MSDU} + \text{Cola MAC}$

### ¿Qué contiene una MPDU?

Una MPDU es, en esencia, lo que comúnmente llamamos una **trama (frame)** de red (como una trama Wi-Fi o Ethernet). Contiene:

* **Direcciones MAC:** Tanto la del remitente como la del destinatario físico.
* **Información de control:** El tipo de trama (si es de datos, de control como un ACK, o de gestión como una baliza Wi-Fi).
* **Cuerpo del datos:** La información real que se quiere transmitir.
* **FCS (Frame Check Sequence):** Un código de verificación de errores (como el CRC) para asegurarse de que la trama no se corrompió en el camino.

### Un detalle clave: MPDU vs. Paquete de Aire

Una vez que la MPDU está lista, se pasa a la capa física (PHY), la cual le añade *otra* cabecera para convertirla en una **PPDU** (*Phy Protocol Data Unit*), que es lo que finalmente se transforma en ondas de radio (Wi-Fi) o pulsos eléctricos (Ethernet).

En tecnologías modernas como **Wi-Fi 802.11**, se utiliza una técnica llamada **A-MPDU** (Agregación de MPDU), que consiste en juntar varias MPDUs en una sola transmisión física para ahorrar tiempo y hacer el internet inalámbrico muchísimo más rápido.
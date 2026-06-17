

### 📝 PREGUNTA 2 (De tus exámenes reales - Capa 2 / Ethernet vs Wi-Fi)

**"¿Por qué Ethernet (802.3) utiliza el mecanismo CSMA/CD y Wi-Fi (802.11) se ve obligado a utilizar CSMA/CA?"**

* **Ethernet (CSMA/CD - Collision Detection):** Al ser un medio guiado (cable), una tarjeta de red puede transmitir datos y, al mismo tiempo, "escuchar" el cable para detectar variaciones de voltaje que indiquen una colisión. Si hay colisión, aborta inmediatamente, ahorrando ancho de banda.
* **Wi-Fi (CSMA/CA - Collision Avoidance):** En el aire (medio inalámbrico), un dispositivo **no puede transmitir y escuchar simultáneamente en la misma frecuencia** porque su propia señal de transmisión satura por completo su receptor local (atenuación extrema del canal). Por lo tanto, no puede *detectar* colisiones mientras transmite; tiene que diseñar una estrategia para *evitarlas* mediante espacios de intercomunicación (IFS) y backoffs aleatorios.




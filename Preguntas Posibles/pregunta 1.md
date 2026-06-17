
### 📝 PREGUNTA 1 (De tus exámenes reales - Capa 2 / Wi-Fi)

**"Explique el problema del Nodo Oculto en redes inalámbricas (802.11). ¿Cómo se resuelve mediante señalización y qué campo de la trama evita que otros nodos transmitan?"**

* **Nodo Oculto:** El problema ocurre cuando dos estaciones (A y C) no se escuchan entre sí debido a la distancia o un obstáculo, pero ambas ven a un punto de acceso central (B). Si A y C transmiten al mismo tiempo hacia B, sus señales colisionan en B.
* **Mecanismo de solución:** Se resuelve mediante el intercambio opcional de paquetes de señalización **RTS (Request to Send)** y **CTS (Clear Point to Send)**.
* **La palabra clave para el puntaje:** Cuando el nodo B responde con un CTS, este paquete incluye el campo **NAV (Network Allocation Vector)**. El NAV funciona como un temporizador que le indica a todos los nodos que escucharon el CTS (incluyendo al nodo oculto C) cuánto tiempo deben permanecer en silencio porque el canal estará ocupado.


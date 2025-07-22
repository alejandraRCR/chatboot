## 🗄️ Base de Datos

### Conexión a Oracle Cloud

La base de datos se encuentra alojada en **Oracle Cloud**. La conexión se realiza a través de la configuración `TNS_ADMIN` y los archivos de wallet, que se montan desde tu sistema local al contenedor Docker.

### ❓ Preguntas del Chatbot (Estado Inicial)

La base de datos contiene inicialmente 10 preguntas predefinidas que el chatbot puede responder:

1.  ¿Cuál es tu nombre?
2.  ¿Cómo estás hoy?
3.  ¿Qué hora es?
4.  ¿Cuál es la capital de Francia?
5.  ¿Quién descubrió América?
6.  ¿Puedes contar un chiste?
7.  ¿Cuál es la montaña más alta del mundo?
8.  ¿Cómo funciona la fotosíntesis?
9.  ¿Qué es la inteligencia artificial?
10. ¿Cómo describe la prueba realizada?

### 🧠 Funcionalidad del Chatbot

1.  **Búsqueda Exacta (Ignorando Mayúsculas/Minúsculas):**
    * El chatbot primero intenta encontrar una respuesta exacta a la pregunta, sin distinguir entre mayúsculas y minúsculas.

2.  **Búsqueda por Palabras Clave (`keywords`):**
    * Si no se encuentra una pregunta exacta, el sistema busca coincidencias con palabras clave definidas para las respuestas existentes.
    * **Nuevo Escenario:** Si una pregunta coincide con palabras clave que están asociadas a **múltiples posibles respuestas**, el chatbot informará al usuario que hay "posibles respuestas" y procederá a listar las opciones relevantes para que el usuario pueda elegir o clarificar.

3.  **Registro de Preguntas No Respondidas:**
    * Si una pregunta no se encuentra (ni exacta ni por palabras clave), el chatbot indica que necesita ser "entrenado" y **registra la pregunta** para una futura respuesta.

4.  **Gestión de Preguntas en Espera:**
    * Mientras una pregunta registrada no ha sido respondida por un administrador (o el sistema), si un usuario la vuelve a formular, el chatbot le informará que la pregunta **"está registrada pero aún no ha sido respondida"** (`PENDING_QUESTION`).

**Nota sobre Expansión:**
* Para este ejercicio, se validan escenarios clave de funcionalidad. Sin embargo, el potencial de un chatbot es vasto, incluyendo la integración de servicios avanzados de **aprendizaje automático (Machine Learning)** para respuestas más complejas y una comprensión más profunda del lenguaje natural.

---

## 🔒 Seguridad y Código

* El microservicio de seguridad (`chatboot.security`) se configuró para manejar la autenticación y autorización mediante **JWT (JSON Web Tokens)**.
* Se configuró **CORS** para asegurar que solo el frontend (puerto `5001`) pueda interactuar con los backends.
* Se empleó el menor código posible en los repositorios, utilizando las capacidades de los frameworks y evitando la necesidad de queries repetitivos.
* Las entidades Java están diseñadas para que sus nombres coincidan directamente con los nombres de las tablas en la base de datos.
* Se utilizó la librería **Lombok** para reducir al máximo el boilerplate code (código repetitivo).
* En el frontend, se manejaron los escenarios de interacción de forma muy sencilla con JavaScript.
* Los usuarios para el login ya están creados en la base de datos. Por motivos de seguridad, las credenciales se proporcionarán al equipo de forma privada.


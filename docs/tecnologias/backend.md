## **Tecnología Backend**

El backend de Mockbank es la columna vertebral que soporta la infraestructura digital del neobanco, garantizando un rendimiento escalable, seguro y eficiente. Nuestro enfoque está centrado en utilizar tecnologías modernas que permitan a Mockbank ofrecer un servicio bancario sin fricciones, con un manejo efectivo de datos, procesamiento rápido de transacciones y alta disponibilidad.

### **Arquitectura del Backend**
Mockbank sigue una arquitectura de **microservicios** para garantizar flexibilidad y escalabilidad. Cada microservicio se encarga de un conjunto específico de funcionalidades dentro del sistema, como la gestión de cuentas, procesamiento de pagos, análisis de datos, etc. Esta arquitectura desacoplada permite actualizaciones más fáciles, escalabilidad independiente y un manejo de fallos eficiente.

---

### **Principales Tecnologías Utilizadas**

#### 1. **Node.js**
- **¿Por qué Node.js?**
  - Node.js se utiliza para manejar las solicitudes y respuestas HTTP rápidas, garantizando una alta concurrencia sin sacrificar el rendimiento. Esto es especialmente útil en el contexto de un banco digital, donde las transacciones deben ser procesadas de manera instantánea.
  - **Express.js** se utiliza como marco para construir las APIs RESTful que permiten la interacción de los usuarios con los diferentes servicios del neobanco.

- **Ventajas:**
  - Velocidad en el procesamiento de transacciones.
  - Asincronía y capacidad para manejar un gran número de conexiones simultáneas.
  - Compatible con las aplicaciones en tiempo real gracias a su naturaleza basada en eventos.

#### 2. **Spring Boot (Java)**
- **¿Por qué Spring Boot?**
  - Spring Boot se utiliza para servicios más complejos y transacciones que requieren un alto nivel de seguridad, como la autenticación, la gestión de usuarios y la integración con servicios financieros externos (como plataformas de pagos y criptomonedas).
  - Spring Boot facilita la creación de aplicaciones Java con configuraciones mínimas, lo que mejora la eficiencia en el desarrollo y la implementación de nuevos microservicios.

- **Ventajas:**
  - Extensa comunidad y robusta documentación.
  - Integración fluida con otras tecnologías de Java, como Spring Security para la gestión de autenticaciones y Spring Data para la interacción con bases de datos.
  - Compatible con contenedores Docker y Kubernetes para la implementación en la nube.

#### 3. **Bases de Datos**
Mockbank utiliza **PostgreSQL** y **MongoDB** como bases de datos primarias para manejar datos estructurados y no estructurados respectivamente.

- **PostgreSQL:**
  - Utilizado para manejar transacciones financieras, datos de usuarios y auditoría. PostgreSQL es una base de datos relacional robusta y confiable, capaz de manejar grandes volúmenes de datos transaccionales.
  - Soporta operaciones ACID, garantizando que las transacciones sean atómicas, consistentes, aisladas y duraderas.

- **MongoDB:**
  - Utilizada para almacenar información menos estructurada, como registros de actividad de los usuarios, logs de eventos y datos en tiempo real de las integraciones con plataformas externas como criptomonedas.
  - Permite flexibilidad en el esquema de datos, lo que facilita el manejo de datos con estructuras dinámicas.

#### 4. **Kafka (Sistema de Mensajería)**
- **¿Por qué Kafka?**
  - Apache Kafka es la tecnología seleccionada para el procesamiento de eventos en tiempo real y la transmisión de datos entre microservicios. Esto es esencial para las transacciones financieras, donde las operaciones deben ser procesadas de forma secuencial y eficiente.
  - Kafka permite gestionar eventos de manera asincrónica, como el procesamiento de pagos, notificaciones y actualizaciones de estado de las cuentas.

- **Ventajas:**
  - Alta disponibilidad y tolerancia a fallos.
  - Escalabilidad horizontal, permitiendo la adición de más consumidores y productores de eventos según sea necesario.
  - Facilidad de integración con otros sistemas de procesamiento y almacenamiento de datos.

#### 5. **Docker y Kubernetes**
- **¿Por qué Docker y Kubernetes?**
  - Docker es utilizado para contenerizar todos los microservicios, lo que facilita su despliegue, escalabilidad y portabilidad. Cada microservicio se ejecuta dentro de un contenedor independiente, lo que asegura que las dependencias no interfieran entre sí.
  - Kubernetes gestiona la orquestación de estos contenedores, garantizando que el sistema se mantenga eficiente, escalable y disponible en todo momento, incluso durante fallos o picos de tráfico.

- **Ventajas:**
  - **Docker** permite un desarrollo ágil con entornos locales idénticos a los de producción.
  - **Kubernetes** proporciona alta disponibilidad y recuperación automática en caso de fallos.

#### 6. **API Gateway**
- **¿Por qué un API Gateway?**
  - Mockbank utiliza un **API Gateway** para centralizar las solicitudes entrantes a los microservicios. Esto permite gestionar de forma centralizada la autenticación, el enrutamiento y la limitación de tasa (rate-limiting), mejorando la seguridad y el rendimiento.
  - **AWS API Gateway** es la herramienta de elección debido a su integración con otros servicios de AWS, y su capacidad para manejar una gran cantidad de solicitudes simultáneas de manera eficiente.

- **Ventajas:**
  - Facilidad para agregar nuevas API y servicios sin afectar la arquitectura principal.
  - Seguridad y control de acceso centralizados.

#### 7. **Seguridad**
La seguridad es un aspecto fundamental en la infraestructura backend de Mockbank. Para proteger los datos de los usuarios y garantizar la integridad de las transacciones, implementamos diversas capas de seguridad:

- **OAuth 2.0 & JWT:** Autenticación basada en OAuth 2.0 y JSON Web Tokens (JWT) para gestionar el acceso a las APIs de forma segura.
- **Spring Security:** Framework para manejar la seguridad de la autenticación y autorización en las aplicaciones basadas en Spring Boot.
- **Cifrado de Datos:** Se emplea **AES-256** para cifrar datos sensibles, tanto en tránsito como en reposo, garantizando la protección de la información financiera.

---

### **Flujo de Datos en el Backend**
1. **Autenticación de Usuario:**
   - El proceso comienza cuando el usuario realiza una solicitud de inicio de sesión a través de la app o la web.
   - El **API Gateway** verifica la autenticación mediante OAuth 2.0 o JWT y, en caso de éxito, redirige al servicio adecuado (como el microservicio de cuentas).
  
2. **Procesamiento de Transacciones:**
   - Las transacciones, como pagos y transferencias, son gestionadas por el microservicio de transacciones, el cual se conecta con el sistema de pagos (como SWIFT o Stripe).
   - Los datos de las transacciones son enviados a **Kafka**, que los distribuye a otros microservicios para su procesamiento y auditoría.

3. **Análisis Financiero:**
   - Los microservicios encargados de análisis utilizan inteligencia artificial para procesar y categorizar los gastos de los usuarios.
   - Estos datos se almacenan en **MongoDB** y se integran con otras plataformas, como **Plaid** para el análisis de datos bancarios.

---

### **Escalabilidad y Resiliencia**

Mockbank está preparado para crecer. Gracias a la arquitectura basada en microservicios, la contenedorización con Docker y la orquestación con Kubernetes, los servicios pueden escalar de forma independiente, asegurando que el sistema pueda manejar picos de tráfico y transacciones sin perder rendimiento. Además, la arquitectura distribuida garantiza que si un servicio falla, otros pueden continuar operando sin interrupciones.

---

El backend de Mockbank está diseñado para ser flexible, seguro y capaz de manejar millones de usuarios y transacciones de manera eficiente. La integración de tecnologías avanzadas asegura que podamos ofrecer una experiencia bancaria sin fricciones y con la última tecnología disponible.

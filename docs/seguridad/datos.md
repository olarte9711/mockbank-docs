## **Seguridad de Datos**

En Mockbank, la **seguridad de los datos** es una prioridad fundamental. Dado que nuestra plataforma maneja información altamente sensible, como datos bancarios, transacciones financieras y datos personales de los usuarios, implementamos una serie de medidas y tecnologías avanzadas para proteger estos datos tanto en reposo como en tránsito.

### **Enfoque General de Seguridad de Datos**

Mockbank sigue un enfoque integral para garantizar la protección de los datos a lo largo de su ciclo de vida. Esto incluye desde la **captura de datos**, pasando por su **almacenamiento seguro**, hasta la **protección durante la transmisión** y su **eliminación** segura cuando ya no es necesario conservarlos.

---

### **1. Encriptación de Datos en Reposo**

La encriptación es un aspecto fundamental en la protección de los datos almacenados en nuestras bases de datos. Todos los datos sensibles, como información personal, transacciones y detalles de cuentas, son **encriptados en reposo** utilizando tecnologías avanzadas.

#### **Métodos de Encriptación Utilizados:**
- **AES-256**: Utilizamos **AES (Advanced Encryption Standard)** con una clave de 256 bits para asegurar que todos los datos almacenados estén cifrados.
- **Encriptación a nivel de campo**: Para datos sensibles como contraseñas y detalles de tarjetas de crédito, se emplea un cifrado adicional de nivel de campo para proteger la información antes de ser almacenada.
- **Base de datos encriptada**: Las bases de datos en la nube (AWS RDS para PostgreSQL, MongoDB Atlas para MongoDB) están configuradas para encriptar todos los datos almacenados en disco.

#### **Proceso de Encriptación:**
1. Los datos se cifran automáticamente al ser almacenados en la base de datos.
2. Las claves de cifrado se gestionan de forma segura utilizando servicios como **AWS KMS (Key Management Service)** para garantizar que solo las aplicaciones autorizadas puedan acceder a los datos descifrados.
3. El acceso a las claves de encriptación está restringido mediante políticas de seguridad estrictas.

---

### **2. Encriptación de Datos en Tránsito**

La protección de los datos mientras se trasladan entre los clientes (aplicaciones móviles, web) y los servidores de Mockbank es igualmente crucial. Implementamos las mejores prácticas de **encriptación de datos en tránsito** para proteger la información de posibles interceptaciones o ataques.

#### **Protocolos Utilizados:**
- **TLS (Transport Layer Security)**: Todos los datos que viajan entre el cliente y el servidor están protegidos mediante **TLS 1.2/1.3**, asegurando que la transmisión de datos sea confidencial y no pueda ser interceptada por terceros.
- **Certificados SSL/TLS**: Utilizamos certificados SSL/TLS de proveedores confiables para asegurar que todos los canales de comunicación estén protegidos mediante cifrado de extremo a extremo.
- **Autenticación basada en certificados**: Para las interacciones entre servicios de backend, utilizamos autenticación basada en certificados SSL para validar las conexiones y asegurar la integridad de la comunicación.

---

### **3. Gestión de Identidades y Accesos**

Para proteger el acceso a los datos, Mockbank utiliza un **sistema robusto de gestión de identidades y accesos (IAM)**. Esto garantiza que solo los usuarios y servicios autorizados tengan acceso a datos sensibles y recursos críticos.

#### **Prácticas y Tecnologías de IAM:**
- **Principio de menor privilegio**: Los usuarios, servicios y aplicaciones reciben solo los permisos necesarios para realizar sus tareas específicas, limitando la exposición de datos sensibles.
- **Autenticación Multifactor (MFA)**: Requerimos autenticación multifactor (MFA) para todos los accesos a la plataforma, especialmente para las cuentas de administración y operaciones financieras.
- **Control de acceso basado en roles (RBAC)**: Implementamos **RBAC (Role-Based Access Control)** para controlar el acceso a los datos según los roles de los usuarios dentro de la organización. Esto asegura que solo los empleados con los roles adecuados puedan acceder a información crítica.

---

### **4. Protección Contra Filtraciones de Datos**

Mockbank implementa tecnologías avanzadas para detectar y prevenir accesos no autorizados y filtraciones de datos, lo que garantiza la integridad y confidencialidad de la información.

#### **Tecnologías y Estrategias de Prevención:**
- **Firewall de Aplicaciones Web (WAF)**: Utilizamos **WAFs** para proteger nuestras aplicaciones web contra amenazas comunes como inyecciones SQL, XSS (Cross-site scripting), CSRF (Cross-Site Request Forgery), y otros ataques de seguridad.
- **Detección y Prevención de Intrusiones (IDS/IPS)**: Se utilizan sistemas de detección y prevención de intrusiones para identificar actividades sospechosas en tiempo real y bloquear posibles amenazas antes de que afecten a la infraestructura.
- **Pruebas de seguridad periódicas**: Se realizan pruebas de penetración y auditorías de seguridad regulares para identificar vulnerabilidades y asegurar que las defensas estén actualizadas.

---

### **5. Auditoría y Monitoreo de Datos**

Para garantizar la seguridad continua, Mockbank implementa un sistema de **auditoría y monitoreo** constante de todos los accesos y acciones realizadas sobre los datos.

#### **Monitoreo y Registro:**
- **Registros de acceso (Access Logs)**: Todos los accesos a datos sensibles son registrados y monitoreados para identificar actividades inusuales o no autorizadas.
- **Análisis en tiempo real**: Los registros son analizados en tiempo real para detectar comportamientos anómalos, posibles brechas de seguridad o accesos no autorizados.
- **Alerta temprana**: Se configuraron alertas automáticas que notifican a los administradores de seguridad en caso de detectar cualquier acceso o modificación sospechosa de los datos.

---

### **6. Destrucción Segura de Datos**

Cuando los datos ya no son necesarios, Mockbank asegura que se destruyan de manera segura para evitar filtraciones o recuperaciones no autorizadas.

#### **Métodos de Destrucción de Datos:**
- **Eliminación segura**: Utilizamos algoritmos de **eliminación segura** para asegurar que los datos sensibles sean completamente borrados de las bases de datos y sistemas de almacenamiento.
- **Destrucción física**: Para dispositivos de almacenamiento que ya no se van a utilizar, como discos duros, se implementan procedimientos de destrucción física (triturado, desmagnetización) para garantizar que no se pueda recuperar la información.

---

### **7. Cumplimiento de Normativas y Regulaciones**

Mockbank cumple con todas las regulaciones y estándares internacionales de protección de datos, incluyendo:

- **GDPR (Reglamento General de Protección de Datos)**: Protege la privacidad y los derechos de los usuarios de la Unión Europea.
- **PCI DSS (Estándar de Seguridad de Datos para la Industria de Tarjetas de Pago)**: Asegura que las transacciones de tarjetas de crédito sean seguras y cumplan con las normativas de la industria.
- **ISO 27001**: Un estándar internacional para la gestión de seguridad de la información.

Mockbank realiza auditorías periódicas para garantizar el cumplimiento con estas normativas y mejorar continuamente las prácticas de seguridad.

---

### **Conclusión sobre la Seguridad de Datos**

La **seguridad de los datos** es un pilar fundamental en Mockbank. A través de una combinación de **encriptación avanzada**, **gestión de accesos** basada en el principio de menor privilegio, **protección contra filtraciones** y un enfoque riguroso de **auditoría y monitoreo**, Mockbank garantiza que la información de sus usuarios esté protegida en todo momento. Estas medidas, junto con la **destrucción segura de datos** y el **cumplimiento con normativas internacionales**, aseguran que Mockbank sea una plataforma de confianza para la gestión de las finanzas digitales.

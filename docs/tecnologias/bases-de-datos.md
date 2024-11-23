## **Tecnología de Bases de Datos**

Las bases de datos son el núcleo donde se almacenan todos los datos fundamentales en Mockbank, como la información de los usuarios, transacciones, balances, operaciones bancarias, y mucho más. La elección adecuada de las tecnologías de bases de datos garantiza un rendimiento robusto, una alta disponibilidad y una recuperación rápida de datos en tiempo real.

### **Arquitectura de Bases de Datos**

Mockbank utiliza una **arquitectura híbrida** que combina bases de datos relacionales y no relacionales para garantizar un almacenamiento de datos eficiente y flexible.

- **Bases de Datos Relacionales (SQL)**: Utilizadas para almacenar datos estructurados y transaccionales, donde la consistencia y la integridad de los datos son esenciales.
- **Bases de Datos No Relacionales (NoSQL)**: Utilizadas para almacenar datos no estructurados o semi-estructurados que requieren una escalabilidad horizontal y flexibilidad en el modelo de datos.

---

### **Bases de Datos Relacionales (SQL)**

#### **PostgreSQL**
- **¿Por qué PostgreSQL?**
  - **PostgreSQL** es una de las bases de datos relacionales más poderosas y avanzadas, conocida por su rendimiento y escalabilidad. Es el sistema de base de datos principal para el almacenamiento de datos críticos y transacciones bancarias en Mockbank.
  - Su **soporte ACID** (Atomicidad, Consistencia, Aislamiento y Durabilidad) es crucial para garantizar que las operaciones financieras se realicen de manera consistente y segura.
  - Utilizamos **PostgreSQL** para almacenar datos estructurados, como información de usuarios, cuentas, transacciones y registros de auditoría.

- **Ventajas:**
  - **Integridad referencial**: El sistema permite la creación de claves primarias y foráneas para garantizar la consistencia de los datos entre tablas relacionadas.
  - **Consultas complejas**: PostgreSQL soporta consultas SQL avanzadas, lo que permite realizar análisis de datos, informes y operaciones complejas.
  - **Escalabilidad**: Aunque es una base de datos SQL, **PostgreSQL** permite escalar de manera eficiente para manejar grandes volúmenes de datos.
  - **Extensiones**: PostgreSQL ofrece extensiones como **PostGIS** para trabajar con datos espaciales y **pgcrypto** para cifrado de datos.

#### **Estructura de Datos en PostgreSQL**
- **Usuarios y Cuentas**: Los datos del usuario y la información de la cuenta se almacenan en tablas relacionadas que incluyen información personal, saldo de cuenta, histórico de transacciones y detalles de autenticación.
- **Transacciones**: Cada transacción (depósito, retiro, transferencia) se registra con un identificador único y detalles de la operación.
- **Auditoría**: Todas las acciones relevantes, como accesos a cuentas y modificaciones de datos, son registradas para su trazabilidad.

#### **Ejemplo de Modelo Relacional en PostgreSQL**
```sql
CREATE TABLE usuarios (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(255) NOT NULL,
    correo VARCHAR(255) UNIQUE NOT NULL,
    telefono VARCHAR(15),
    fecha_registro TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE cuentas (
    id SERIAL PRIMARY KEY,
    id_usuario INT REFERENCES usuarios(id),
    saldo DECIMAL(15,2) DEFAULT 0,
    tipo VARCHAR(50),
    fecha_creacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE transacciones (
    id SERIAL PRIMARY KEY,
    id_cuenta INT REFERENCES cuentas(id),
    tipo VARCHAR(50),
    monto DECIMAL(15,2),
    fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    estado VARCHAR(50) DEFAULT 'pendiente'
);
```

---

### Bases de Datos No Relacionales (NoSQL)
MongoDB
¿Por qué MongoDB?

MongoDB es una base de datos no relacional de tipo documento que permite el almacenamiento flexible de datos. Es utilizada para almacenar información menos estructurada o que cambia con frecuencia, como configuraciones personalizadas, datos históricos y logs.
MongoDB es ideal para almacenar datos que no necesitan un esquema fijo, lo que nos permite adaptarnos rápidamente a nuevas características del producto sin necesidad de realizar cambios complicados en la base de datos.
Ventajas:

Escalabilidad horizontal: MongoDB permite distribuir datos en múltiples servidores para manejar grandes volúmenes de datos.
Flexibilidad en el esquema: No requiere un esquema predefinido, lo que facilita la adición de nuevos campos y colecciones.
Alto rendimiento: Ofrece operaciones rápidas de lectura y escritura, lo que es crucial para aplicaciones que requieren una alta velocidad de acceso a datos, como el sistema de pagos en tiempo real.
Estructura de Datos en MongoDB
Historial de Transacciones: MongoDB almacena el historial de transacciones para acceder rápidamente a los registros históricos de cada usuario, sin la necesidad de realizar complejas consultas SQL.
Logs y Auditoría: Todos los eventos y logs, como las actividades de usuario, errores y métricas de rendimiento, son almacenados en MongoDB.
Personalización de Cuentas: Los usuarios pueden tener configuraciones personalizadas, como preferencias de notificación y alertas, que se almacenan en colecciones de MongoDB.
Ejemplo de Documento en MongoDB



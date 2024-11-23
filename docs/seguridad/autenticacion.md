## **Autenticación en Seguridad**

La **autenticación** es un componente crítico en la seguridad de Mockbank. Dado que Mockbank maneja información financiera sensible, como cuentas bancarias, transacciones y datos personales de los usuarios, es esencial garantizar que solo usuarios autorizados puedan acceder a sus cuentas y realizar operaciones. Por ello, se han implementado múltiples capas de autenticación y protección para asegurar que los accesos estén protegidos de manera eficaz y que las operaciones se realicen de forma segura.

### **Enfoque General de Autenticación**

Mockbank utiliza un enfoque multifacético para la autenticación, que incluye:

- **Autenticación Basada en Contraseñas Seguras**
- **Autenticación Multifactor (MFA)**
- **Autenticación Biométrica**
- **OAuth 2.0 y OpenID Connect**
- **Tokens JWT (JSON Web Tokens)**
- **Autenticación con Criptografía y Blockchain**

---

### **1. Autenticación Basada en Contraseñas Seguras**

Para la autenticación inicial, Mockbank obliga a los usuarios a crear contraseñas seguras, siguiendo los estándares más exigentes. 

#### **Requisitos de la Contraseña:**
- Longitud mínima de 12 caracteres.
- Combinación de letras mayúsculas, minúsculas, números y caracteres especiales.
- No permitir contraseñas comunes o previamente filtradas en bases de datos públicas.
- Encriptación de contraseñas con algoritmos de hashing seguros como **bcrypt**.

#### **Proceso:**
1. El usuario crea una cuenta y establece su contraseña.
2. La contraseña se cifra utilizando **bcrypt** antes de almacenarse en la base de datos.
3. En el proceso de inicio de sesión, la contraseña proporcionada se cifra nuevamente y se compara con el hash almacenado para verificar la autenticidad.

---

### **2. Autenticación Multifactor (MFA)**

Para agregar una capa adicional de seguridad, Mockbank implementa la **autenticación multifactor (MFA)**. Esto significa que, además de la contraseña, el usuario debe proporcionar un segundo factor para autenticar su identidad.

#### **Factores de Autenticación Utilizados:**
- **Factor de Conocimiento (algo que el usuario sabe)**: La contraseña.
- **Factor de Posesión (algo que el usuario tiene)**: Un código generado por una aplicación de autenticación (como **Google Authenticator** o **Authy**) o un mensaje SMS.
- **Factor de Inherencia (algo que el usuario es)**: Autenticación biométrica, como huella digital o reconocimiento facial, a través de la app móvil.

#### **Proceso:**
1. Tras ingresar la contraseña, el sistema solicita un código de autenticación que se genera dinámicamente (a través de una aplicación de autenticación o mensaje SMS).
2. El sistema verifica el código ingresado con el generado y, si coincide, permite el acceso del usuario.

---

### **3. Autenticación Biométrica**

La autenticación biométrica permite a los usuarios autenticarse usando características físicas únicas, lo que mejora la seguridad y la experiencia del usuario. Mockbank implementa métodos biométricos como:

- **Reconocimiento facial**: Utilizado a través de la app móvil para verificar la identidad del usuario.
- **Lectura de huellas dactilares**: Disponible en dispositivos móviles compatibles, para autenticación rápida y segura.

#### **Proceso:**
- Durante el proceso de inicio de sesión en la aplicación móvil, los usuarios pueden optar por utilizar su **huella digital** o el **reconocimiento facial** en lugar de la contraseña.
- Estos métodos biométricos se integran con la plataforma de seguridad, asegurando que solo el propietario de la cuenta pueda acceder.

---

### **4. OAuth 2.0 y OpenID Connect**

Mockbank utiliza **OAuth 2.0** y **OpenID Connect** para proporcionar autenticación federada y autorización de acceso a terceros. Este sistema es ideal para permitir que los usuarios inicien sesión en la aplicación de Mockbank utilizando sus credenciales de otras plataformas de confianza como **Google**, **Facebook**, **Apple** y otros proveedores de identidad.

#### **Flujo de Autenticación:**
1. El usuario selecciona el proveedor de identidad con el que desea iniciar sesión (Google, Facebook, etc.).
2. El sistema redirige al usuario al servidor de autorización del proveedor de identidad para autenticar su identidad.
3. Una vez autenticado, el proveedor de identidad devuelve un **token de acceso** al sistema de Mockbank, que permite al usuario acceder a sus servicios sin tener que crear una nueva cuenta o contraseña.

Este enfoque reduce la necesidad de crear nuevas credenciales para cada servicio y mejora la experiencia del usuario.

---

### **5. Tokens JWT (JSON Web Tokens)**

Mockbank utiliza **JWT (JSON Web Tokens)** para la autenticación de usuarios en aplicaciones web y móviles. Los JWT permiten que las aplicaciones móviles y web verifiquen la identidad del usuario sin tener que almacenar información sensible como contraseñas en el cliente.

#### **Proceso:**
1. Cuando el usuario se autentica exitosamente (con contraseña, MFA o biometría), el sistema genera un **JWT** firmado digitalmente.
2. Este JWT se envía al cliente y se almacena de forma segura (por ejemplo, en un almacenamiento local o en una cookie HTTP-only).
3. Cada vez que el cliente realiza una solicitud a los servidores de Mockbank, el JWT se incluye en los encabezados de la solicitud como un **Bearer token**.
4. Los servidores de Mockbank verifican la validez del JWT para autenticar la solicitud y autorizar la acción.

---

### **6. Autenticación con Criptografía y Blockchain**

Mockbank explora el uso de **blockchain** y **criptografía avanzada** para mejorar aún más la seguridad en la autenticación de usuarios. Con tecnologías de registro descentralizado, Mockbank puede ofrecer una autenticación más robusta y segura, minimizando el riesgo de hackeos en los servidores centralizados.

#### **Blockchain en Autenticación:**
- **Verificación Descentralizada**: Las credenciales de los usuarios pueden almacenarse de forma descentralizada, garantizando que no haya un único punto de fallo en la infraestructura.
- **Autenticación Basada en Firmas**: Los usuarios pueden autenticarse mediante firmas digitales generadas en sus dispositivos, y las transacciones de autenticación pueden registrarse en un ledger de blockchain para garantizar la integridad y trazabilidad.

---

### **Conclusión sobre Autenticación**

La autenticación es un pilar fundamental en la seguridad de Mockbank. Con la implementación de contraseñas seguras, MFA, biometría, OAuth 2.0, JWT, y criptografía avanzada, Mockbank asegura que el acceso a las cuentas y la realización de transacciones estén protegidos con las mejores tecnologías de seguridad disponibles. Esto permite a los usuarios realizar operaciones financieras con confianza y tranquilidad, sabiendo que sus datos están protegidos por capas robustas de autenticación y seguridad.


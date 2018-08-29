# SABIS-OASS: Requisitos de Seguridad

## Tabla de contenidos

- Introduccion y Objetivos
- Cumplimineto: tipos de requisitos
    - Legal
    - Regualación / estándar
    - Normativos / políticas internas
- Anexos

-----------------------------------------

## Introducción y objectivos

Este documento ha de servir como pauta a la hora de identificar y comprobar los requisitos durante el desarrollo de Software. Los puntos aquí redactados han de dirigirse al personal con rol de desarrollador, mostrando claramente cada punto junto con su ejemplo y mitigación i/o corrección. 

-----------------------------------------

## Cumplimiento: tipos de requisitos

### **Legal**

- [GDPR](https://ec.europa.eu/info/law/law-topic/data-protection_en)
- [BOE Protección de datos](https://www.boe.es/legislacion/codigos/codigo.php?id=055_Proteccion_de_Datos_de_Caracter_Personal&modo=1)
- [BOE Ciberseguridad](https://www.boe.es/legislacion/codigos/codigo.php?id=173_Codigo_de_Derecho__de_la_Ciberseguridad&modo=1)
- [PSD/PSD2](https://ec.europa.eu/info/law/payment-services-psd-2-directive-eu-2015-2366_en)

### **Regulación / estándar**

### **Normativos / políticas internas**

Podemos establecer un conjunto de reglas a cumplir durante la implementación de nuestro código, agrupadas en diferentes categorias.

**Validación de la entrada de información:**

- Realizar la validación de la información en un sistema de confianza (por ejemplo un servidor propio).
- Identificar los orígenes de datos y clasificarlos segun si son de confianza o no. Validar toda la información que provenga de origenes no seguros.
- Debe haber un proceso de validación de la información de entrada centralizado y común para toda la aplicación.
- Especificar una codificación de carácteres adecuada para todos los origenes de datos (por ejemplo UTF-8).
- Canviar la codificación de carácteres a la acordada antes de hacer cualquier validación.
- Cualquier validación fallida debe provocar un rechazo de los datos.
- Validar toda la información proveniente del cliente antes de procesarla, incluyendo todos los parámetros, URLs y cabezeras HTTP.
- Validar que las cabezeras, tanto en las peticiones como en las respuestas, contengan solo carácteres ASCII.
- Validar la información que proviene de las redirecciones.
- Validar que la información de entrada sea de los tipos esperados para cada caso.
- Acotar los posibles valores de la información.
- Validar la longitud de la información.
- Cuando sea posible, establecer un listado de carácteres permitidos.
- Si algun carácter especial (< > " ' % ( ) & + \ \' \") debe ser permitido, hay que añadir controles adicionales como codificación de la salida, controles específicos para las API i autorización/identificación para su uso en la aplicación.
- Comprobar de forma cuidadosa los siguientes carácteres: bytes nulos (%00), carácteres para salto de linea (%0d, %0a, \r, \n), carácteres para escalar directorios (../ or .., o %c0%ae%c0%ae/).

**Codificación de la salida:**

- Llevar toda la información codificada a un sistema de confianza.
- Utilizar un procedimiento estándar y comprovado para cada tipo de dato codificado.
- Codificar todos los carácteres a menos que sean seguros para el interprete deseado.
- Comprobar y limpiar la salida de información no confiable antes de dirigirla a consultas SQL, XML o LDAP.
- Comprobar y limpiar la salida de la información no confiable antes de utilizarla para realizar comandos del sistema operativo.

**Autenticación i gestión de contraseñas:**

- Requerir autenticación para todas las páginas y recursos, excepto aquellos específicamente públicos.
- Todos los procesos de autenticación han de realizarse en entornos seguros.
- Utilizar servicios de autenticación estándars y comprobados.
- Usar una implementación centralizada para todos los procesos de autenticación, incluyendo las librerias que llaman a servicios externos.
- Separar la lógica de la autenticación del recurso solicitado y redireccionar a/desde el sistema de autenticación centralizado.
- Las contraseñas nunca se podran guardar en texto plano, únicamente sus hashes. Estos hashes deberan ser con salto, de un único sentido y con algorismos considerados seguros (por ejemplo SHA-2). Además, la tabla o ficheros donde se almacenan debe ser escribible solo por la aplicación.
- La encriptacíón de contraseñas debe realizarse solo en sistemas seguros.
- Validar la información de autenticación solo cuando se haya obtenido toda ella, sobretodo en implementaciones secuenciales.
- Los fallos de autenticación no deben mostrar cual parte de la autenticación es erronea, ni en visualización ni en código. Por ejemplo, NUNCA indicar si el error está en el nombre de usuario o en la contraseña.
- Autentificar siempre al connectar con sistemas externos que disponen de información o funciones sensible.
- Utilizar solo peticiones HTTPS POST para transmitir las credenciales de autenticación.
- Las contraseñas no temporales se deben enviar solo a través de conexiones seguras.
- Forzar que las contraseñas sean suficientemente complejas, acorde a las políticas establecidas (por ejemplo 8 carácteres mínimos y 3 tipos diferentes).
- El input de contraseña debe ser ocultado en la pantalla del usuario (por ejemplo usar input type=password en formularios).
- Deshabilitar la cuenta después de succesivos intentos fallidos de autenticación. El tiempo debe ser de pocos minutos.
- Canviar i resetear la contraseñas deben requerir el mismo nivel de control que la creación i la autenticación.
- Las preguntas para restablecer la contraseña deben permitir un número elevado de respuestas aleatorias
- Si las contraseñas se resetean a través de correo, utilizar solo direcciones previmente registradas y contraseñas/links temporales.
- Las contraseñas y links temporales deben expirar después de un periodo corto de tiempo.
- Procurar que las contraseñas temporales sean cambiadas por el usuario al siguiente uso.
- Notificar al usuario cada vez que la contraseña sea cambiada.
- No permitir que se puede cambiar la contraseña por una ya utilizada anteriormente.
- Las contraseñas deben tener como mínimo un dia antes de poder ser cambiadas nuevamente.
- Forzar el cambio de contraseñas segun las políticas establecidas. Los sistemas mas críticos requieren cambios mas frecuentes.
- Deshabilitar la funcionalidad de "recuerdame" en los campos de contraseña.
- El último intento (válido o no) de autenticación debe ser notificado al usuario en el siguiente login correcto.
- Monitorear para identificar el intento de autenticación en distintas cuantas con la misma contraseña.
- Cambiar todas las contraseñas por defecto i identificadores de usuario o deshabilitar las cuentas asociadas.
- Volver a autenticar a los usuarios antes de realizar operaciones críticas.
- Utilizar autenticación en múltiples pasos para operaciones o información sensible. (Algo que sabes, algo que tienes, algo que eres).
- Si se utiliza código de terceros para autenticarse, inspeccionar el código detalladamente.

**Gestión de la sessión:**

- Utiliza los controles de session propios del servidor o framework. La aplicación solo deberia reconocer estos como válidos.
- La creación del identificador de sesión siempre ha de realizarse en un sistema de confianza.
- Los controles de sesión deberan usar algorismos comprobados que proporcionen suficientes identificadores de sesión aleatorios.
- Definir el dominio y la ruta de las cookies que contienen identificadores de sesión a un valor restringido para el sitio.
- La funcionalidad de logout deberia terminar completamente con la sesión o conexión asociada.
- La funcionalidad de logout deberia estar disponible en todas páginas protegidas con autenticación previa.
- Establecer un tiempo de inactividad para terminar la sesión tan corto como sea posible, considerando el riesgo y la funcionalidad del negocio.
- Desactivar los logins permanentes y forzar la terminación de la sesión incluso estando la sesión activa.
- Si la sesión fué establecida antes del login, termina esa sesión y establece una nueva después de autenticarse correctamente.
- Generar un nuevo identificador de sesión en cada autenticación.
- No permitir logins simultaneos con el mismo identificador de usuario.
- No exponer los identificadores de sesión en URLs, mensajes de error o logs.
- Proteger la información de sesión de accesos no autorizados desde otros usuarios de la aplicación.
- Generar un nuevo identificador de sesión si la conexión cambia de HTTP a HTTPS. De todos modos, se deberia usar siempre HTTPS.
- Añade mas mecanismos de control de sesion para operaciones críticas en el servidor, controles por cada petición, como tokens aleatorios o parámetros.
- Verifica el atributo "secure" para las cookies transmitidas a través de una conexión SSL/TLS.
- Define las cookies con el atributo "HttpOnly", a menos que necesites acceder a ellas des de scripts en el cliente.

**Control de acceso:**

- No permitir ningún acceso en caso de que la aplicación no pueda acceder a su información de la configuación de seguridad.
- Implementar los controles de autenticación en cada petición, incluso aquellas que provengan de scripts del servidor, "includes" o peticiones asíncronas (por ejemplo AJAX) des del cliente.
- Separar la lógica de permisos del resto del código de la aplicación.
- Restringir el acceso a ficheros y otros recursos solo para usuarios autorizados.
- Restringir el acceso a URLs protegidas solo para usuarios autorizados.
- Restringir el acceso a funciones protegidas solo para usuarios autorizados.
- Restringir el acceso a servicios solo para usuarios autorizados.
- Restringir el acceso a la información de la aplicación solor para usuarios autorizados.
- Restringir el acceso a la información sobre los usuarios a través de controles de acceso.
- Restringir el acceso a la información sobre la configuracion de seguridad.
- Si el estado de la información debe almaenarse en el cliente, una mecanismos de encriptación y comprobaciones de integridad en el lado del servidor.
- Limita el número de transacciones que un solo usuario o dispositivo puede hacer durante un peridodo de tiempo.
- Si se permiten sesiones de larga duración, válida periodicamente que los permisos del usuario no hayan cambiado. En caso de cambio, haz un logout y fuerza al usuario a autenticarse nuevamente.
- Audita las cuentas de usuario y fuerza la desactivación de aquellas sin uso.
- Las cuentas asociadas a servicios o aquellas que permitan conexiones desde/para sistemas externos deberan tenir los mínimos permisos posibles.

**Prácticas criptográficas:**

- Todas los algorismos de encriptación usados para proteger información confidencial deben ejecutarse en sistemas de confianza.
- Los módulos de encriptación deben fallar de forma segura.
- Establecer y utilizar una política y procedimiento sobre como seran gestionadas las claves necesarias en algorismos de encriptación.

**Captura de errores y registro:**

**Seguridad de la comunicacióm:**

**Configuración del sistema:**

**Seguridad de la base de datos:**

**Gestión de los archivos:**

**Gestión de la memoria:**

**Prácticas generales de programación:**

------------------------------------------

## Anexos

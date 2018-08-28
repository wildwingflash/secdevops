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

Primero nos enfocaremos en las principales amenazas actuales, recopiladas por OWASP (Open Web Application Security Project), ya que son las vulnerabilidades a nivel de desarrollo de software que más impacto han causado.

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

**Control de acceso:**

**Funciones criptográficas:**

**Captura de errores y registro:**

**Seguridad de la comunicacióm:**

**Configuración del sistema:**

**Seguridad de la base de datos:**

**Gestión de los archivos:**

**Gestión de la memoria:**

**Prácticas generales de programación:**

------------------------------------------

## Anexos

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

**Autenticación i gestión de contraseñas:**

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
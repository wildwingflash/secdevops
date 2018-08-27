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

Primero nos enfocaremos en las principales amenazas actuales, recopiladas por OWASP (Open Web Application Security Project), ya que son las vulnerabilidades a nivel de desarrollo de software que más impacto han causado.

#### **Inyección**

Un ataque por inyección es aquel en el que se ejecuta una comanda o consulta no deseada dentro de un input. Este input puede estar como parte de un formulario (principalmente en peticions POST, PUT) o como parte de la URL (principalmente peticiones GET).

Un trozo de código como el siguiente permitiria inyectar la comanda SQL que quisíeramos para modificar la base de datos:

```
txtUserId = getRequestString("UserId");
txtSQL = "SELECT * FROM Users WHERE UserId = " + txtUserId;
```

De esta forma, un valor como el siguiente podria eliminar los usuarios de la base de datos: ``105; DROP TABLE Supplierss``, ejecutando en la base de datos la siguiente sentencia: ``SELECT * FROM Users WHERE UserId = 105; DROP TABLE Suppliers;``

Una inyección puede afectar a una base de datos SQL o NoSQL, ejecutar comandas del Sistema Operativo o atacar un repositorio LDAP, todo depende de cual sistema sea el receptor de los datos introducidos por el usuario.

Sea cual sea el caso, HA DE COMPROBARSE SIEMPRE los datos introducidos por el usuario y recortar esas partes que podrian ser perjudiciales, poniendo mucha atención a carácteres como final de comanda (;) o inicio/final de Strings(" o ').

------------------------------------------

## Anexos
# 

# 

### Fundamentos de Seguridad y Auditoría.

## **Módulo**: Digitalización Aplicada a los Sistemas Productivos.

**Autor**: Guillermo Eugui Sánchez.

**Profesora**: Willman Acosta Lugo.

# 

# 

# 

# 


# 2\. Fase de Investigación: Comprendiendo el corazón del sistema {#2.-fase-de-investigación:-comprendiendo-el-corazón-del-sistema}

* ### **Reto de Investigación 1** {#reto-de-investigación-1}

    
  Syslog es un estándar de mensaje para poder comunicarse con un servidor de registro, y sirve como recurso para poder facilitar el monitoreo de dispositivos a través de una red y los dispositivos pueden usar un agente syslog para enviar notificaciones mensajes bajo muchas condiciones específicas, los mensajes de registro incluyen una marca de tiempo, una clasificación de gravedad, un ID de dispositivo e información específica del evento, pero tiene deficiencias, el protocolo Syslog se usa porque es fácil de implementar y es bastante abierto, lo que permite muchas implementaciones y sobretodo, la capacidad de monitorear casi cualquier dispositivo conectado, funciona en todos los Unix, Linux y otros \*nix, y en  MacOS, los servidores basados en Windows no admiten Syslog de forma nativa, pero hay muchas herramientas de terceros disponibles para permitir que los dispositivos Windows se comuniquen con un servidor Syslog.  
    
  Las facilidades del Syslog son el proceso del sistema que genera un evento del Syslog puede abarcar por ejemplo un evento generado por el kernel, por el sistema de correo, por procesos de seguridad o autorización …etc… , las facilidades actúa como un filtro   
   indicando a SMS que reenvíe al servidor Syslog remoto únicamente aquellos eventos cuya facilidad coincida con la definida en este campo, entonces al cambiar el número de función o el nivel de gravedad, se modifica el número mensajes que se envían al servidor Syslog remoto.  
    
  El valor de la función es una forma de determinar qué proceso de la máquina creó el mensaje como el protocolo Syslog se escribió originalmente en BSD Unix, las funciones reflejan los nombres de los procesos y Daemons de UNIX.\[1\]  
    
    
    
  


| Número | Descripción | Número | Descripción |
| :---- | :---- | :---- | :---- |
| 0 | Mensaje de kernel | 12 | subsistema de NTP |
| 1 | mensajes a nivel de usuario | 13 | auditoría del log |
| 2 | sistema de mail | 14 | alerta del log |
| 3 | sistema de daemons | 15 | reloj del daemon |
| 4 | \*\*mensajes de seguridad o autorización | 16 | uso local 0 (local0) |
| 5 | mensajes generados internamente por el Syslog | 17 | uso local 1 (local1) |
| 6 | subsistema de impresora de línea  | 18 | uso local 2 (local2) |
| 7 | subsistema de noticias de red | 19 | uso local 3 (local3) |
| 8 | subsistema UUCP | 20 | uso local 4 (local4) |
| 9 | reloj de daemon | 21 | uso local 5 (local5) |
| 10 | mensajes de seguridad o autorización | 22 | uso local 6 (local6) |
| 11 | FTP de daemon | 23 | uso local 7 (local7) |


  

Cada mensaje Syslog incluye un valor de prioridad al principio del texto, el valor de prioridad oscila entre 0 y 191 y no lleva espacios ni ceros a la izquierda. La prioridad se encuentra entre los delimitadores «\< y \>». Por ejemplo: \<PRI\>HEADER MESSAGE.

El valor de prioridad se calcula mediante la fórmula (Prioridad \= Facilidad \* 8 \+ Nivel). Por ejemplo, un mensaje del núcleo (Facility=0) con una gravedad de Emergencia (Severity=0) tendría un valor de prioridad de 0\. Asimismo, un mensaje de «uso local 4» (Facility=20) con una gravedad de Aviso (Severity=5) tendría un valor de prioridad de 165\.

El archivo de registro de autenticación es muy importante y es una negligencia grave que este archivo tenga permisos de lectura para usuarios no privilegiados, por que el log contiene información sensible que una persona con malas intenciones  podría utilizar para reconocer información, por ejemplo: identificadores de proceso, nombres de usuario, direcciones IP de origen…. La diferencia técnica entre un fallo de acceso local y uno remoto es que el intento por SSH registra específicamente la dirección IP de origen y el puerto efímero utilizado, mientras que un fallo local frente a la pantalla carece de estos metadatos de red.\[2\]

* ### **Reto de Investigación 2** 

  A nivel empresarial y legal, la gestión centralizada de registros ofrece ventajas vitales de protección, como por ejemplo:  
* **Custodia Externa:** Enviar los logs a un servidor externo seguro evita que los registros permanezcan dispersos e indefensos en una máquina que podría ser vulnerada.  
* **Integridad de Evidencias:** Si un atacante compromete el servidor, su primera acción suele ser borrar los logs locales; la centralización asegura que el rastro digital permanezca intacto para el análisis forense.\[3\]

* ### **Fuentes/Citas:**

### 

\[1\]¿Qué es un servidor Syslog y cómo funciona?

- whatsupgold **{** [https://success.trendmicro.com/en-US/solution/KA-0017337](https://success.trendmicro.com/en-US/solution/KA-0017337) }

\[2\]¿What are Syslog Facilities and Levels?

- success.trendmicro{ [https://www.whatsupgold.com/es/blog/que-es-un-servidor-syslog-y-como-funciona](https://www.whatsupgold.com/es/blog/que-es-un-servidor-syslog-y-como-funciona) } 

\[3\]Modelo de madurez para la gestión de logs en centros de datos

- dialnet { [https://dialnet.unirioja.es/servlet/articulo?codigo=10398407](https://dialnet.unirioja.es/servlet/articulo?codigo=10398407) }

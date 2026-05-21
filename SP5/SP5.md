# Monitorización del sistema

Supervisar el rendimiento en Ubuntu implica analizar y cuantificar el consumo de recursos del equipo o servidor en tiempo real. Esta práctica es fundamental para diagnosticar el estado del sistema y anticiparse a posibles situaciones de saturación.

<img width="447" height="257" alt="image" src="https://github.com/user-attachments/assets/cfedd6e3-25fd-4e17-9f77-0ba32b89ecc0" />

Al ejecutar la aplicación, se visualizan todos los procesos activos del sistema. Tal y como se trabajó en prácticas anteriores, este entorno gráfico ofrece una funcionalidad equivalente a herramientas de terminal como `htop`, `etop` o `btop`.

<img width="1190" height="770" alt="image" src="https://github.com/user-attachments/assets/1ced7a4c-1f80-4472-bbc5-6a1dc0bc394c" />

Como se observa en la interfaz, tenemos la posibilidad de finalizar procesos, cerrarlos o ajustar parámetros como la afinidad de CPU y la prioridad de ejecución. Estas operaciones ya se han tratado detalladamente en apartados anteriores.

<img width="440" height="373" alt="image" src="https://github.com/user-attachments/assets/7e29efbc-5c00-47af-899d-90ee972962ff" />

<img width="791" height="261" alt="image" src="https://github.com/user-attachments/assets/e8723348-bcfc-4945-95c6-44ec455d3347" />

Asimismo, tal y como se ha mencionado previamente, disponemos de una visión global del rendimiento de todos los recursos de la máquina. Los principales indicadores son:

### CPU

Refleja la carga de trabajo que está procesando la unidad central. Si el porcentaje de uso se mantiene constantemente al máximo, el sistema perderá fluidez al no poder gestionar todas las tareas simultáneamente.

### Memoria RAM

Representa el entorno donde se ejecutan las aplicaciones activas. En caso de agotarse la memoria física, Ubuntu utilizará el espacio de intercambio (**Swap**) del disco duro; este recurso de emergencia provoca una caída considerable en el rendimiento general del sistema.

### Red

Monitoriza el flujo de datos de entrada y salida del dispositivo, además de supervisar el estado de las conexiones activas y los puertos abiertos.

### Almacenamiento (Disco)

Supervisa tanto la ocupación del espacio disponible como la tasa de transferencia en operaciones de lectura y escritura. Una actividad excesiva del disco puede generar cuellos de botella que afecten a la velocidad del sistema.

<img width="1201" height="756" alt="image" src="https://github.com/user-attachments/assets/08d9bdc1-458c-4c6e-a510-10f54ca162e7" />

<img width="1210" height="121" alt="image" src="https://github.com/user-attachments/assets/a5208d73-cb41-4bb0-8110-b891ea2cdd2a" />

---

# Logs - Lluc y Manu

Para consultar el historial de eventos, visualizaremos el contenido del archivo `syslog` mediante el comando `cat`, lo que nos permitirá revisar todos los registros del sistema.

<img width="1200" height="668" alt="2026-03-05_13-24" src="https://github.com/user-attachments/assets/86dcd351-9f35-453f-bbf8-4aa489de0097" />

En este directorio podemos personalizar la rotación de logs.

<img width="958" height="70" alt="2026-03-05_13-26" src="https://github.com/user-attachments/assets/2f210a51-698f-4186-b999-d20a5c628fd8" />

Tenemos la posibilidad de editar este archivo para configurar y ajustar los parámetros de rotación de registros según nuestras necesidades.

<img width="500" height="483" alt="2026-03-05_13-26_1" src="https://github.com/user-attachments/assets/c55ecb28-0215-49bc-b41e-71a0ee9e8d4e" />

Este archivo nos indica la ruta de la configuración por defecto de los registros; a continuación, accederemos a ella para realizar las modificaciones necesarias.

<img width="942" height="704" alt="2026-03-05_13-27" src="https://github.com/user-attachments/assets/ad30daea-147c-4dd6-8668-347e7d267f24" />

En primer lugar, realizaremos una prueba para analizar el impacto de una notificación de correo e identificar en qué archivos de registro queda reflejada. Mediante una simulación, verificaremos si el envío genera una entrada inmediata en `syslog` y si posteriormente queda registrada en `mail.log`. Para ello utilizaremos dos terminales: una para enviar el mensaje y otra para monitorizar `syslog` en tiempo real.

<img width="1209" height="725" alt="2026-03-05_13-30" src="https://github.com/user-attachments/assets/e5e7a95f-c91d-438b-ae25-f5cd938dd785" />

Realizaremos una segunda prueba modificando la configuración del servicio de correo. El objetivo es restringir el archivo `mail.log` para que únicamente registre mensajes de nivel `error`, descartando tanto los niveles inferiores como los superiores. Hay que recordar que, si utilizáramos el comodín `*`, el sistema volvería a almacenar todos los registros sin distinción.

<img width="990" height="638" alt="2026-03-05_13-31" src="https://github.com/user-attachments/assets/5fa4e89e-d0ba-4c6a-b2f4-9a3ee889bbb6" />

Cuando modificamos la configuración, debemos reiniciar el servicio.

<img width="621" height="39" alt="2026-03-05_13-36" src="https://github.com/user-attachments/assets/f60fac00-8463-4fb5-ab15-f8f256dc040d" />

Al repetir la prueba anterior, observamos que el registro no se almacena en `mail.log`. Esto se debe a que la notificación enviada tiene una prioridad de tipo `notice`, la cual queda excluida por el filtro configurado exclusivamente para niveles `err`.

<img width="1213" height="759" alt="2026-03-05_13-37" src="https://github.com/user-attachments/assets/00e0f8f3-490a-4a97-96c6-ff1065a7d765" />

Finalmente, si sustituimos la prioridad `mail.notice` por `mail.err`, comprobaremos que el registro se almacena correctamente en el archivo de logs, ya que ahora sí coincide con el filtro configurado.

<img width="1202" height="452" alt="2026-03-05_13-38" src="https://github.com/user-attachments/assets/7d1ad8e3-ea8d-4f5b-93f2-0e7b155ee077" />

Procederemos a modificar nuevamente el filtrado de los registros de correo, esta vez eliminando el signo `=`. Con este cambio, el sistema almacenará no solo las entradas de tipo `err`, sino también todas aquellas que tengan una prioridad superior.

<img width="936" height="724" alt="2026-03-05_13-38_1" src="https://github.com/user-attachments/assets/3c16831d-bce9-4b69-8d52-96117582d730" />

Reiniciamos el servicio y continuamos.

Para validar este funcionamiento, cambiaremos el nivel de alerta a `crit` (criticidad superior) y comprobaremos que el sistema lo registra correctamente en el archivo de logs.

<img width="1211" height="478" alt="2026-03-05_13-40" src="https://github.com/user-attachments/assets/c5259d84-7d40-492b-887f-e217ec5990e9" />

Es posible definir una ruta personalizada para almacenar los registros que consideremos más relevantes. En este caso, configuraremos el sistema para capturar todas las entradas de tipo `crit`, indicaremos el directorio de destino deseado y, finalmente, reiniciaremos el servicio para aplicar los cambios.

<img width="1215" height="773" alt="2026-03-05_13-41" src="https://github.com/user-attachments/assets/8e534e00-cf2c-49a0-805b-c96f1645aea5" />

Al enviar una notificación de tipo `cron.crit`, observamos que se ha generado automáticamente un nuevo archivo llamado `mireia.log`. Esta es la ruta específica que habíamos definido en el paso de configuración anterior.

<img width="1202" height="386" alt="2026-03-05_13-42" src="https://github.com/user-attachments/assets/21276dd7-e3c6-45a6-8bae-353d2bdbac9c" />

Con este comando podemos visualizar todos los logs de tipo `crit`.

<img width="1205" height="185" alt="2026-03-05_13-43" src="https://github.com/user-attachments/assets/8a125f3b-5893-4e0c-b198-63202aadb3d6" />

Dependiendo de los parámetros añadidos, podemos filtrar las búsquedas para acotar los resultados. En este caso, nos centraremos en consultar los registros de tipo `mail` generados anteriormente.

<img width="588" height="164" alt="2026-03-05_13-44" src="https://github.com/user-attachments/assets/4e26257b-89d6-4699-ad8d-fbda0a04fbfe" />

---

# Ejercicio Logs

Para esta práctica configuraremos un entorno con dos máquinas Ubuntu: un cliente encargado de enviar sus registros a la red (manteniéndolos también de forma local) y un servidor que actuará como receptor centralizado de toda la información.

## Máquina servidor

En primer lugar, en la máquina servidor (la encargada de recibir y almacenar los registros), procederemos a configurar la redirección. Crearemos un nuevo archivo de configuración para desviar todos los logs remotos hacia una carpeta específica, la cual generaremos en este mismo paso.

<img width="242" height="53" alt="image" src="https://github.com/user-attachments/assets/7bf3735f-2939-4b30-9602-e52360bdd99b" />

<img width="824" height="37" alt="image" src="https://github.com/user-attachments/assets/98294a48-7cd7-45a5-9033-00c8e3e29e69" />

Dentro del nuevo archivo, debemos añadir las siguientes líneas para habilitar la recepción de registros mediante los protocolos UDP y/o TCP.

<img width="817" height="250" alt="image" src="https://github.com/user-attachments/assets/d725df1f-269e-47c1-b6d8-2c6bee319107" />

Finalmente, permitimos el tráfico TCP y UDP en el firewall.

<img width="161" height="37" alt="image" src="https://github.com/user-attachments/assets/807548eb-85da-40b5-82a7-cf615db3562d" />

<img width="143" height="36" alt="image" src="https://github.com/user-attachments/assets/5578e789-7d1d-4530-81ae-698d0043523f" />

Una vez completados estos pasos de configuración, debemos reiniciar el servicio para que el sistema aplique y active los nuevos parámetros.

<img width="227" height="38" alt="image" src="https://github.com/user-attachments/assets/b4528e88-0f98-4681-8a31-43f75289dc7d" />

---

## Máquina cliente

Dentro de un nuevo archivo llamado `90-forward.conf`, añadiremos la dirección IP del servidor para indicar hacia dónde deben reenviarse los registros.

<img width="664" height="55" alt="image" src="https://github.com/user-attachments/assets/9c49c5da-af25-4343-8901-c4aedc2a23b4" />

Reiniciamos el servicio `rsyslog`.

<img width="635" height="51" alt="image" src="https://github.com/user-attachments/assets/ae7c064b-2cb4-4902-b7b8-21a2ed167f38" />

### Comprobación con logger

Una vez configurado el reenvío, ejecutaremos un `logger` desde el cliente para generar un mensaje de prueba y verificar que llega correctamente al servidor.

<img width="485" height="25" alt="image" src="https://github.com/user-attachments/assets/4ecc8852-5202-477f-937b-006d94b390c1" />

Podemos comprobar que se han generado varios archivos dentro del directorio `remote`. Entre ellos encontramos la carpeta correspondiente a `ClientSP5`, confirmando que el servidor ha organizado correctamente los registros recibidos por cada nodo.

<img width="287" height="66" alt="image" src="https://github.com/user-attachments/assets/535f1f6f-6409-4251-9c39-b85d2d36041d" />

Si accedemos al directorio recién creado, podremos localizar el archivo de registro y visualizar el log de prueba enviado anteriormente desde el cliente.

<img width="1215" height="535" alt="image" src="https://github.com/user-attachments/assets/02807902-269b-4fd7-98cb-8bd8fd085885" />

---

# Servidor de actualizaciones

Implementar un servidor de actualizaciones centralizado en un entorno con múltiples nodos Ubuntu es fundamental para garantizar la eficiencia operativa.

### Optimización del ancho de banda

Las actualizaciones se descargan una sola vez desde Internet. El resto de equipos de la infraestructura las obtienen directamente desde el servidor local, reduciendo drásticamente el tráfico externo.

### Gestión del ciclo de vida y control de riesgos

Permite establecer un entorno de pruebas con equipos piloto para validar los parches antes del despliegue masivo, minimizando el impacto de actualizaciones inestables.

### Monitorización centralizada de seguridad

Facilita la supervisión del estado de cada nodo, identificando qué equipos requieren acciones urgentes o reinicios pendientes.

### Soporte para entornos aislados

Es una solución indispensable para mantener actualizados servidores críticos que no disponen de acceso directo a Internet por motivos de seguridad.

---

## Servidor

Instalamos `apache` y `apt-mirror` en el servidor.

<img width="517" height="17" alt="2026-03-12_13-08" src="https://github.com/user-attachments/assets/0cdd446f-291e-4b02-a6a0-7c3ba2e039b4" />

<img width="525" height="22" alt="2026-03-12_13-09" src="https://github.com/user-attachments/assets/6bce5ff9-b748-4d01-adc5-3bc2d89f3200" />

Accederemos al archivo `mirror.list` y comentaremos todas las líneas por defecto para evitar descargas innecesarias. A continuación, añadiremos exclusivamente el repositorio o paquete específico que queremos instalar y mantener sincronizado.

<img width="872" height="481" alt="2026-03-12_13-12" src="https://github.com/user-attachments/assets/1168ceec-56cf-4a8b-b994-47bd6d0a30fb" />

Una vez configurado el archivo, ejecutaremos el comando `apt-mirror` para comenzar a descargar y sincronizar el repositorio definido previamente.

<img width="1015" height="648" alt="2026-03-12_13-13_1" src="https://github.com/user-attachments/assets/d204a29b-75eb-40b0-b9c1-b058816309df" />

Cuando finalice la descarga, comprobaremos que se ha instalado correctamente y enlazaremos el contenido con Apache para hacerlo accesible a través de la red.

<img width="881" height="98" alt="2026-03-12_13-16" src="https://github.com/user-attachments/assets/f33d0024-88e1-4bed-8bfa-b35829e01630" />

---

## Cliente

En la máquina cliente accederemos al archivo `sources.list` para añadir el nuevo repositorio. En lugar de apuntar a los servidores oficiales de Ubuntu, utilizaremos la dirección del enlace simbólico creado previamente en el servidor local.

<img width="747" height="446" alt="2026-03-12_13-19" src="https://github.com/user-attachments/assets/378d2947-5294-4a8c-bac9-462a87c57cb9" />

Este paso es indispensable antes de instalar el paquete, ya que primero es necesario firmarlo (o importar la clave de firma) para que el sistema lo reconozca como una fuente de confianza.

<img width="1055" height="76" alt="2026-03-12_13-22" src="https://github.com/user-attachments/assets/df1d0af8-1aaf-41c3-984e-56cb20a4c471" />

Ahora, al ejecutar un `apt update` en el cliente, podremos observar cómo el sistema obtiene uno de los repositorios directamente desde la máquina servidor en lugar de buscarlo en Internet.

<img width="1205" height="283" alt="2026-03-12_13-26" src="https://github.com/user-attachments/assets/e83baf97-3ca5-4bf2-b737-9d1cdcf63c89" />

Una vez verificado el repositorio, procederemos a instalar el paquete deseado; podremos comprobar que la descarga se realiza directamente desde nuestro servidor local.

<img width="1208" height="520" alt="2026-03-12_13-29" src="https://github.com/user-attachments/assets/67287764-6f98-412f-948e-5a6783ef1dea" />

---

# Ejercicio

## Servidor

He elegido la aplicación AnyDesk porque es una de las que menos recursos consume, lo que facilita una instalación rápida. A continuación, procederemos a añadir su repositorio al servidor.

<img width="771" height="419" alt="2026-03-12_13-57" src="https://github.com/user-attachments/assets/0d392833-4682-4682-8cad-fcdb49a8f96d" />

Ejecutamos `apt-mirror` y comprobamos que descarga correctamente el paquete.

<img width="1202" height="719" alt="2026-03-12_14-00" src="https://github.com/user-attachments/assets/eeb24ad7-4b5b-4d8d-bfd5-8e3400a85b10" />

Enviamos el paquete a Apache.

<img width="753" height="76" alt="2026-03-12_14-06" src="https://github.com/user-attachments/assets/8e172d06-c1bf-43c1-9b72-73689081ec01" />

---

## Cliente

En la máquina cliente accederemos al archivo `sources.list` para añadir el nuevo repositorio. En lugar de apuntar a los servidores oficiales, utilizaremos la dirección del enlace simbólico creado previamente en el servidor local.

<img width="807" height="492" alt="2026-03-12_14-11" src="https://github.com/user-attachments/assets/5fc6109e-1087-4fb0-b137-1d0ea8dab38f" />

Este paso es indispensable antes de instalar el paquete, ya que primero debemos firmar el repositorio (o importar la clave de confianza) para que el sistema valide su autenticidad.

<img width="800" height="89" alt="2026-03-12_14-17" src="https://github.com/user-attachments/assets/cad604b4-673b-4436-8fa8-e76544e810d7" />

Ahora, al ejecutar un `apt update`, vemos que el cliente se conecta correctamente al servidor local para obtener la lista de paquetes del repositorio configurado.

<img width="807" height="338" alt="2026-03-12_14-18" src="https://github.com/user-attachments/assets/a6b29a41-41a6-4789-943d-fe5cb92212c6" />

Finalmente, ya podemos instalar el paquete y confirmar que el sistema lo descarga directamente desde nuestro servidor local.

<img width="923" height="507" alt="2026-03-12_14-19" src="https://github.com/user-attachments/assets/882b9f43-3e7e-4143-87a5-92ca7b294f60" />

Una vez finalizada la instalación, la aplicación ya está operativa y puede utilizarse con total normalidad en la máquina cliente.

<img width="644" height="240" alt="image" src="https://github.com/user-attachments/assets/0e572098-4a87-4909-bb34-64485ba8ef11" />

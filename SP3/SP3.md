# Sprint 3: Administració de Dominis i Seguretat 

## Configuración del servidor

Primero, abrimos un terminal dentro de la máquina servidor, ejecutamos el comando **ip a**, anotamos la dirección IP que recibimos por DHCP y la configuraremos de forma estática mediante la interfaz gráfica. Cuando configuramos un servidor, **siempre debemos poner la dirección IP estática**, ya que una dirección dinámica complicaría el acceso a los servicios que ofrece, debido a que cada día podría tener una dirección diferente.

<img width="746" height="459" alt="Captura de pantalla de 2026-01-08 13-24-13" src="https://github.com/user-attachments/assets/9a3ec543-8a7e-4345-83bc-fcec314ada22" />

<img width="786" height="302" alt="2026-05-22_00-06" src="https://github.com/user-attachments/assets/13b72184-44a5-4d15-85a7-3718c254e04d" />

A continuación, accedemos a **/etc/hostname** con el comando **nano**, donde **modificaremos el nombre del dispositivo**.

<img width="504" height="48" alt="2026-05-22_00-06_1" src="https://github.com/user-attachments/assets/da0225d1-026a-4372-b06b-7cbba1cb6fb2" />

Haremos lo mismo en **/etc/hosts** y pondremos el nuevo hostname en la dirección de loopback del dispositivo. También añadiremos el dominio que crearemos próximamente asociado a la dirección IP que hemos configurado de forma estática.

<img width="492" height="89" alt="2026-05-22_00-07" src="https://github.com/user-attachments/assets/b3d5d3c2-f494-4d84-8993-b05b50de3d4f" />

A continuación, instalamos los servicios necesarios para instalar y gestionar LDAP.

<img width="780" height="153" alt="image" src="https://github.com/user-attachments/assets/0a30a644-0d52-45bd-9e02-394bf293a2af" />

Durante la instalación, nos pedirá una contraseña para el usuario administrador de LDAP, que más adelante deberemos recordar.

<img width="652" height="300" alt="image" src="https://github.com/user-attachments/assets/d6da4609-d432-471d-976f-dba29410869d" />

Usamos el comando **slapcat** para ver todos los elementos del dominio.

<img width="761" height="483" alt="image" src="https://github.com/user-attachments/assets/52c97ac2-bc84-4031-98ef-72cc74827359" />

Ahora vamos a **Descargas** y descomprimimos el archivo ZIP que hemos descargado de Moodle.

<img width="773" height="305" alt="image" src="https://github.com/user-attachments/assets/c32eaa7f-ce22-4652-abd4-bfb65a94d6de" />

Con **dpkg-reconfigure slapd**, podemos configurar y añadir elementos al dominio más fácilmente. Alternativamente, podemos utilizar los archivos de configuración **.ldif** que hemos descomprimido, pero estos no son tan prácticos.

<img width="194" height="18" alt="image" src="https://github.com/user-attachments/assets/ac2c2b66-2ddc-4747-9c62-e1bf8aa9471b" />

Introducimos el dominio que hemos indicado previamente en **/etc/hosts**.

<img width="768" height="359" alt="image" src="https://github.com/user-attachments/assets/dc385436-be5b-44cc-bc78-febcfc178e27" />

Indicamos el nombre de la organización.

<img width="751" height="369" alt="image" src="https://github.com/user-attachments/assets/4596e391-d4b5-432e-80f1-e7a0af226daa" />

Introducimos una contraseña. Podemos poner la misma que antes.

<img width="556" height="233" alt="image" src="https://github.com/user-attachments/assets/98401836-90b1-4ee4-bfbd-2e046ebc89a3" />

Eliminaremos la base de datos al purgar.

<img width="555" height="230" alt="image" src="https://github.com/user-attachments/assets/1a6004dd-9342-42a4-a2b4-91a72385e54d" />

Finalmente, movemos la base de datos antigua y ejecutamos el comando **slapcat** para comprobar que todos los cambios que acabamos de configurar se han aplicado correctamente.

<img width="556" height="242" alt="image" src="https://github.com/user-attachments/assets/a3bb3730-8c0e-4997-9f84-df402069fb57" />

De momento no tenemos elementos, como usuarios, grupos o unidades organizativas, pero el dominio ya aparece configurado correctamente.

<img width="763" height="462" alt="image" src="https://github.com/user-attachments/assets/d983ffbd-7436-4457-988c-d3cf294bbb2a" />

Ahora crearemos una unidad organizativa mediante un archivo llamado **uo.ldif**, que hemos descargado. Lo editaremos para que se adapte a nuestros parámetros. En este caso, habría que cambiar **dc=nick,dc=cat**, que corresponde a nuestro dominio.

<img width="753" height="210" alt="image" src="https://github.com/user-attachments/assets/5c509ca5-47f8-44af-9be0-afd34aa8535c" />

Para ejecutarlo utilizaremos este comando, que sirve para añadir contenido al servidor LDAP leyéndolo desde un archivo.

**ldapadd:** Es el comando principal para añadir entradas a la base de datos LDAP.

**-c (continue):** Si encuentra un error, por ejemplo, si una entrada ya existe, no se detiene; continúa añadiendo el resto de elementos del archivo.

**-x:** Utiliza autenticación simple, es decir, con contraseña normal, en lugar de mecanismos de autenticación más complejos.

**-D "cn=admin...":** Es el usuario con el que te identificas para hacer los cambios. En este caso, estás accediendo como administrador del dominio nick.cat.

**-W:** Pide la contraseña después de pulsar Intro, por seguridad, para que no quede guardada en el historial de comandos.

**-f uo.ldif:** Indica el archivo desde donde debe leer los datos que quieres añadir. En este caso, el archivo **uo.ldif**.

<img width="791" height="84" alt="image" src="https://github.com/user-attachments/assets/26a7f477-70b4-4d4e-9e5f-c4c2a0dfe603" />

Ahora toca crear un usuario con el archivo **usu.ldif**. Igual que antes, cambiaremos los parámetros para adaptarlos a los nuestros.

<img width="758" height="627" alt="image" src="https://github.com/user-attachments/assets/5b40df47-b756-4f20-957f-77f107f9b5a5" />

Seguidamente, ejecutaríamos el mismo comando para añadirlo, cambiando únicamente el nombre del archivo.

<img width="621" height="66" alt="image" src="https://github.com/user-attachments/assets/29991643-1cf1-4663-902a-70d319bc33cf" />


Ahora toca el último archivo, **grup.ldif**, en el que cambiaríamos los mismos parámetros que en los dos archivos anteriores.

<img width="742" height="267" alt="image" src="https://github.com/user-attachments/assets/3feae02a-b3a1-40dc-ab23-5cb826988e64" />

Y usamos la misma orden, cambiando el nombre del archivo.

<img width="620" height="69" alt="image" src="https://github.com/user-attachments/assets/bfe280e5-25bb-4b3f-95ec-e5ec60cd8e3a" />

Mediante el comando **slapcat**, podemos confirmar que se ha creado correctamente.

<img width="610" height="677" alt="image" src="https://github.com/user-attachments/assets/7f81a643-f6e5-4682-b943-5a8dcf975fe0" />

<img width="591" height="765" alt="image" src="https://github.com/user-attachments/assets/30f562c8-9ee4-41bd-b38b-ddc7286177ad" />

<img width="712" height="425" alt="image" src="https://github.com/user-attachments/assets/c564ae41-957d-46fc-bc0a-7eb09797140f" />

## Configuración del cliente

Ahora sería el turno del cliente. Previamente, habríamos comprobado que hay conexión entre los dos equipos. Después, descargaremos los paquetes necesarios.

<img width="381" height="17" alt="image" src="https://github.com/user-attachments/assets/c99a90b0-a451-4c43-bc05-e6adcd858913" />

Durante la instalación, aparecerá el asistente, que nos pedirá la dirección IP del dominio.

<img width="689" height="308" alt="image" src="https://github.com/user-attachments/assets/985a1e76-9238-436c-a9ba-cd8d3a00294c" />

También pondremos el nombre.

<img width="717" height="319" alt="image" src="https://github.com/user-attachments/assets/ea6372da-ba7e-471a-866f-1f513924010e" />

Elegiremos la versión de LDAP 3.

<img width="696" height="327" alt="image" src="https://github.com/user-attachments/assets/d97b2edf-d168-4024-8a9a-17e1397a3087" />

Seleccionaremos Sí en las dos opciones siguientes.

<img width="690" height="390" alt="image" src="https://github.com/user-attachments/assets/43838a43-c1ec-45f0-ac20-c61bb25ced4a" /> <img width="698" height="360" alt="image" src="https://github.com/user-attachments/assets/e1a2ceeb-1e97-49a3-8ecb-d72cbf28c769" />

Introduciremos el usuario administrador.

<img width="708" height="422" alt="image" src="https://github.com/user-attachments/assets/fd0afbf9-945b-479d-a96b-9e64e57d4214" />

Después, introduciremos su contraseña.

<img width="692" height="339" alt="image" src="https://github.com/user-attachments/assets/403daf51-35ff-4c90-8607-183a33cce760" />

Con esto ya lo tendríamos configurado, pero en caso de que nos hubiéramos equivocado en algún punto, podemos volver a configurarlo con este comando.

<img width="343" height="20" alt="image" src="https://github.com/user-attachments/assets/9e1632ce-e516-4e7d-a36c-4c3be3c46557" />

Seguidamente, editaremos el archivo /etc/nsswitch.conf y añadiremos files systemd en medio de cada línea.

<img width="697" height="231" alt="image" src="https://github.com/user-attachments/assets/6b668762-554f-400c-a17e-23ab29ba254d" />

Después, en el archivo /etc/pam.d/common-password, tendremos que borrar esta parte de una línea.

<img width="699" height="284" alt="image" src="https://github.com/user-attachments/assets/01334baa-b0ac-4213-8f12-8a9d32669867" />

Ya casi estaríamos terminando. Dentro del archivo /etc/pam.d/common-session, añadiremos la última línea que se ve en la captura. Esta sirve para que, cuando un usuario cambie su contraseña, se actualice automáticamente en el servidor LDAP sin que tenga que escribirla dos veces.

<img width="698" height="410" alt="image" src="https://github.com/user-attachments/assets/93849ed2-821e-4710-801c-75473ba49c96" />

Ahora modificaremos el archivo /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf y añadiremos lo siguiente:

<img width="680" height="94" alt="image" src="https://github.com/user-attachments/assets/c001bfe0-d237-4e93-82e8-262041223899" />

Una vez hecho todo esto, ya podríamos cerrar sesión con nuestro usuario e iniciar sesión con el nuevo usuario que hemos creado, que se llama alu1.

<img width="563" height="609" alt="image" src="https://github.com/user-attachments/assets/92aa1a5a-0598-41d3-bc1a-599eaea50f17" />

## Gestión del dominio mediante comandos

### Requisitos previos

* Haz un `dpkg-reconfigure slapd` en el servidor para dejar la base de datos vacía y solo con el dominio y el usuario administrador creados. Compruébalo con un `slapcat`.

<img width="2171" height="724" alt="image" src="https://github.com/user-attachments/assets/5912be5b-1f35-4c7b-b0d6-8b99ca5027c9" />

<img width="1617" height="973" alt="image" src="https://github.com/user-attachments/assets/52ce8285-3cee-46ca-879a-6b651fb12cb6" />


* Descarga el archivo `dades_pt10.ldif` de Moodle y, con el comando `ldapadd`, carga los usuarios, grupos y UO. Ten en cuenta que el dominio es `vesper.cat`, por lo que tendrás que modificarlo por el tuyo.

<img width="1708" height="921" alt="image" src="https://github.com/user-attachments/assets/19b851bc-ea67-4594-98e8-162e2b9fc7f8" />

Y añadimos el **.ldif** con **ldapadd**.

<img width="1746" height="901" alt="image" src="https://github.com/user-attachments/assets/2044a705-e712-428d-9deb-1794aa2dcac0" />


* Haz otro `slapcat` para comprobar que los datos se han cargado correctamente.

<img width="1231" height="1278" alt="image" src="https://github.com/user-attachments/assets/a404209c-6e4a-4dbd-83ac-cab4a342d983" />


### Actividades

* ¿Cuántas UO hay? **Hay 2 UO**. ¿Cuántos usuarios hay en el dominio? **Hay 3 usuarios**.

<img width="1979" height="795" alt="image" src="https://github.com/user-attachments/assets/06e1e949-63b0-46aa-8d3c-e6a52996db6d" />

* Crea una nueva UO llamada `asix`.

<img width="755" height="164" alt="image" src="https://github.com/user-attachments/assets/4f8103b3-2367-4b6c-b2ef-1607c51404cf" />

* Borra los atributos `roomNumber` y `homeDirectory` del usuario `ejohnson`.

En este caso, no existe ningún usuario **ejohnson** y ninguno de los usuarios tiene asignados los atributos `roomNumber` y `homeDirectory`; por tanto, primero los añadiré y después los borraré.

Como el usuario está presente, no permite eliminar el atributo `homeDirectory`, pero sí su `roomNumber`.

<img width="738" height="123" alt="image" src="https://github.com/user-attachments/assets/63dc258c-22da-4fab-b6f5-d5d98aa60b8a" />

Aquí ya lo habríamos creado y se puede ver.

<img width="1272" height="1236" alt="image" src="https://github.com/user-attachments/assets/daa850eb-2836-4362-b04f-ad6582ecb859" />

Ejecutaríamos el siguiente comando.

<img width="788" height="88" alt="image" src="https://github.com/user-attachments/assets/21617e71-c607-4295-a171-fdca05463381" />

Y ya se habría borrado.

<img width="1309" height="1202" alt="image" src="https://github.com/user-attachments/assets/b4a2beed-be7e-46b8-8d2d-5f7427dc17e9" />

* ¿En cuántos grupos encontramos al usuario `kvaughan` como `uniqueMember` y cuáles son?

Utilizando el usuario `xavier` como sustituto de `kvaughan`:

Número de grupos: 1

Grupos donde aparece como `memberUid`: `informatica`.

<img width="808" height="85" alt="image" src="https://github.com/user-attachments/assets/332d6426-454c-4e1c-b81e-03883cd86e12" />

* Saca de la UO `People` a 3 usuarios y añádelos a la UO `asix`.

Este sería el archivo que he creado.

<img width="1421" height="1107" alt="image" src="https://github.com/user-attachments/assets/67d63c60-90c9-4483-b331-54d8a8984c16" />


Con su comando para ejecutarlo.

<img width="776" height="182" alt="image" src="https://github.com/user-attachments/assets/177dd476-5325-45b2-8995-f16546a514a1" />

Comprobación:

<img width="1310" height="1200" alt="image" src="https://github.com/user-attachments/assets/9db5010d-a76d-4842-a109-836c1c6e9e72" />


* ¿Cuántos grupos hay dentro de la UO `Groups`?

En este caso, 0.

<img width="811" height="93" alt="image" src="https://github.com/user-attachments/assets/5bca67a4-b0ca-483c-9d11-397c1a73a46b" />

* Borra la UO `People`.

En este caso, borraría la UO de `rrhh`, ya que la de `People` no existe.

<img width="801" height="61" alt="image" src="https://github.com/user-attachments/assets/50033580-013c-4ed1-8aa4-3bb85b598cb8" />


* Modifica el `uid` del usuario `hmiller` a `hamiller`.

Como el usuario `hamiller` no existe, lo haré con el usuario `xavier`, con este archivo.

<img width="808" height="158" alt="image" src="https://github.com/user-attachments/assets/be75f2d3-fc85-4087-b754-13d95496bc8b" />

Y esta es la orden.

<img width="701" height="89" alt="image" src="https://github.com/user-attachments/assets/33a64693-7a1f-4810-b709-6e2d2abd5b67" />


Comprobación:

<img width="1324" height="1188" alt="image" src="https://github.com/user-attachments/assets/e7e9f482-9aec-4d45-bfb1-a6153971d064" />

* Crea un nuevo usuario con dos atributos opcionales para la clase `posixAccount`. Lo haré con este archivo.

<img width="1447" height="1087" alt="image" src="https://github.com/user-attachments/assets/49dbf014-3d46-4d92-a014-bf5df04634da" />

Comando:

<img width="794" height="87" alt="image" src="https://github.com/user-attachments/assets/e5f94566-7e44-42fb-99b0-1bc1da40b580" />

* Añade un par de atributos opcionales más al usuario anterior.

<img width="2153" height="730" alt="image" src="https://github.com/user-attachments/assets/62aee637-9a6e-4f36-b85a-39e54eef6750" />

Comando:

<img width="806" height="91" alt="image" src="https://github.com/user-attachments/assets/5f031a75-2fa5-4785-9dd2-cd22d030e9ca" />

* Modifica el correo del usuario `jburrell` por `jburrell@gmail.com`.

Como el usuario `jburrell` no existe, lo he hecho con `ramon`.

<img width="800" height="187" alt="image" src="https://github.com/user-attachments/assets/74905ab9-2571-4a8f-acf3-ac9ad4f5ce5f" />

Comando:

<img width="788" height="87" alt="image" src="https://github.com/user-attachments/assets/daed430c-ccd2-4502-8646-26f4f5016343" />

Comprobación:

<img width="277" height="72" alt="2026-02-20_13-35" src="https://github.com/user-attachments/assets/bf626264-87a0-40f8-816d-455d4a8f7d70" />

* Crea un nuevo grupo dentro de la UO `Groups` y añade 3 usuarios.

Como previamente he mostrado que no existe la UO `Groups`, lo haré sobre la de `asix`.

<img width="2033" height="773" alt="image" src="https://github.com/user-attachments/assets/794fcb46-6378-45ba-8386-09e8bf8a0dbf" />

Comando:

<img width="810" height="90" alt="image" src="https://github.com/user-attachments/assets/54a87f00-fdfd-410f-8024-7bbb4f6fd409" />

Comprobación:

<img width="1779" height="884" alt="image" src="https://github.com/user-attachments/assets/352b81ce-c36f-40e2-9536-fb9d485b8931" />

* Quita del grupo creado anteriormente a un usuario.

<img width="798" height="161" alt="image" src="https://github.com/user-attachments/assets/3299d01c-68fd-420b-a434-f0a6d5ec1609" />


Comando:

<img width="782" height="89" alt="image" src="https://github.com/user-attachments/assets/8571f0f0-5f62-4f51-ad8e-5ce3c386bf63" />

* Muestra todos los usuarios de la UO `Asix` cuyo `uid` empiece por la letra `x` y que formen parte también de la UO `Recursos Humanos`.

<img width="797" height="107" alt="image" src="https://github.com/user-attachments/assets/029959d3-0d28-4472-97e3-6212b73c21d1" />

* Muestra todos los usuarios del dominio cuyo `uidNumber` esté entre 1010 y 1030, ambos incluidos. ¿Cuántos son?

<img width="807" height="111" alt="image" src="https://github.com/user-attachments/assets/d7f1bc01-3d69-4420-be5b-0aa7d0f008e9" />

* Usuarios cuyo teléfono acabe en un 2 o cuyo apellido acabe en una n. ¿Cuántos?

En este caso son 0 usuarios.

<img width="810" height="69" alt="image" src="https://github.com/user-attachments/assets/366e1ab1-838f-4cc2-bf68-3dd5cba2a1b6" />

* De una sola vez, en el usuario que tú quieras, borra un atributo, añade otro y modifica un tercero.

<img width="1618" height="972" alt="image" src="https://github.com/user-attachments/assets/beb4ee07-6a60-46bd-bd8d-f7369398a766" />

Comprobación:

<img width="2170" height="725" alt="image" src="https://github.com/user-attachments/assets/d8ff7549-d83e-4a7e-80bd-11666eb995f4" />

## Entorno gráfico

Para configurar LDAP en un entorno gráfico tenemos muchas opciones, como por ejemplo:

* phpldapadmin
* apache directory studio
* jxplorer
* ldap account manager (LAM)

En este caso he escogido LAM, ya que me parece muy fácil de utilizar y muy intuitivo.

### Requisitos previos

Primero debemos instalar todos estos paquetes, ya que LAM utiliza PHP y necesitamos instalar todos sus requisitos para que funcione correctamente.

<img width="733" height="196" alt="2026-02-18_17-21" src="https://github.com/user-attachments/assets/2e67a43a-7ae1-421d-9c12-90c343c3a69c" />

Y ahora descargaré el binario **.deb**.

<img width="734" height="134" alt="2026-02-18_17-23" src="https://github.com/user-attachments/assets/4f8f4c3b-7e2f-4b3d-ab51-56dd18ea5d0a" />

<img width="735" height="131" alt="2026-02-18_17-24" src="https://github.com/user-attachments/assets/cf3658e4-0da9-4c6f-b9ff-3510e2f024fd" />


## Configuración del entorno gráfico

Una vez ya instalado, podemos acceder mediante la IP al directorio **/lam**. Aquí pondremos una contraseña para entrar al panel administrativo. Una vez introducida, ya estaremos dentro para poder gestionar el **LDAP**.

<img width="693" height="401" alt="2026-02-18_17-27" src="https://github.com/user-attachments/assets/ecbd687c-afe4-442e-af19-12fdb5106fde" />

Ahora, cuando guardemos, nos “expulsará” y nos hará iniciar sesión.

<img width="791" height="527" alt="2026-02-18_17-41" src="https://github.com/user-attachments/assets/105f0a65-aa52-4feb-9230-21765132fabb" />

Ahora debemos crear un usuario para la gestión. Para ello, iremos a **"Editar perfiles del servidor"**.

<img width="440" height="338" alt="2026-02-18_17-42" src="https://github.com/user-attachments/assets/c78f32b8-1756-4669-bebc-466c336f6554" />

Y aquí haremos clic en esta opción.

<img width="787" height="455" alt="2026-02-18_17-42_1" src="https://github.com/user-attachments/assets/1cf79ab5-4dca-4981-885a-95744a8505cd" />

<img width="621" height="353" alt="2026-02-18_18-00" src="https://github.com/user-attachments/assets/f7f2eaee-9f3b-472a-adcd-c57aaa0c7a56" />

Y ya estamos dentro como usuario LAM.

<img width="816" height="477" alt="2026-02-18_18-04" src="https://github.com/user-attachments/assets/157aa314-e1d0-45d0-b1b8-b30798c30442" />

Aquí introduciremos nuestra configuración LDAP.

<img width="2069" height="760" alt="image" src="https://github.com/user-attachments/assets/bea2c8da-b4f2-42f1-8a7f-4af0e835725d" />

También tendremos que ir a **Account Types** y cambiar esta configuración.

<img width="627" height="262" alt="image" src="https://github.com/user-attachments/assets/27d5a79e-118a-4b4f-a912-2369fbc6259a" />

Ahora ya podemos iniciar sesión con el usuario administrador de nuestro dominio LDAP.

<img width="389" height="312" alt="2026-02-18_18-18" src="https://github.com/user-attachments/assets/6b005c3f-aff0-49b6-8b59-2929a11b307f" />

Desde aquí ya podemos ver los usuarios que tenemos creados.

<img width="1724" height="912" alt="image" src="https://github.com/user-attachments/assets/3f60c897-d7c0-420a-b916-71467dac5bc3" />


### Creación de una nueva OU

Para crear una nueva OU, primero debemos ir a **"Tools"** y después a **"OU Editor"**.

<img width="356" height="236" alt="2026-02-18_18-20" src="https://github.com/user-attachments/assets/f71694c9-d757-46cf-a677-24a63484e4ae" />

Aquí introducimos el nombre que queremos que tenga esta OU.

<img width="1015" height="209" alt="2026-02-18_18-20_1" src="https://github.com/user-attachments/assets/76341059-402a-41f2-ae37-33f436ec313d" />

Hacemos clic en **OK** y ya la tenemos creada.

<img width="344" height="152" alt="2026-02-18_18-21" src="https://github.com/user-attachments/assets/5590605c-da92-4c54-925f-4cc3d6ab326c" />

### Creación de un nuevo grupo

Para crear un nuevo grupo, primero debemos ir a **"Accounts"** y después a **"Groups"**.

<img width="449" height="130" alt="2026-02-18_18-21_1" src="https://github.com/user-attachments/assets/38fe7d4a-8637-4a21-a180-386ae6089c67" />

Una vez aquí, iremos a **"New Group"**.

<img width="549" height="320" alt="2026-02-18_18-22_1" src="https://github.com/user-attachments/assets/af0a0b76-c244-42b9-9b14-3c372b5a19d5" />

Finalmente, crearemos el grupo. En este caso, le pondremos un nombre y un UID.

<img width="905" height="269" alt="2026-02-18_18-30" src="https://github.com/user-attachments/assets/2364fdff-a0e6-46cf-88d0-6174f670778a" />

El grupo se ha creado correctamente.

<img width="715" height="171" alt="2026-02-18_18-31" src="https://github.com/user-attachments/assets/2ba32186-af59-4d43-b134-a955fb8fe001" />

Comprobación:

<img width="889" height="341" alt="2026-02-18_18-31_1" src="https://github.com/user-attachments/assets/9e0e1286-b179-408d-8bd6-ce75bc0b177f" />

### Creación de un nuevo usuario

Para crear un nuevo usuario, primero debemos ir a **"Accounts"** y después a **"Users"**.

<img width="298" height="66" alt="2026-02-18_18-32" src="https://github.com/user-attachments/assets/4df0d191-0c57-4d8e-b335-8407ca67ad4f" />

Aquí iremos a **"New User"**.

<img width="848" height="426" alt="2026-02-18_18-32_1" src="https://github.com/user-attachments/assets/dff5a5c2-0367-4f98-99d8-59748dfe6eb1" />

Una vez aquí, pasaremos a la gestión personal.

<img width="782" height="157" alt="image" src="https://github.com/user-attachments/assets/414bdf7f-99b0-45df-94e7-d0fd96b55f36" />

Y ahora a la gestión UNIX.

<img width="797" height="212" alt="image" src="https://github.com/user-attachments/assets/ae7c08ff-dd26-4d90-85c5-25bcc982c6f5" />

Finalmente, podemos ponerle una contraseña de la siguiente manera.

<img width="683" height="423" alt="2026-02-18_18-37" src="https://github.com/user-attachments/assets/3ea00955-bde9-4848-8651-89fa37c525d4" />

Y ya tenemos el usuario creado correctamente.

<img width="676" height="155" alt="2026-02-18_18-38" src="https://github.com/user-attachments/assets/1240daec-b4d5-4e44-bd81-d1d9c69e44b4" />

Verificación:

<img width="856" height="456" alt="2026-02-18_18-38_1" src="https://github.com/user-attachments/assets/790f3576-958d-4aeb-8401-3b505e829020" />

### Acceder desde el cliente con este nuevo usuario creado

Para hacerlo, he abierto el cliente y he accedido mediante la interfaz gráfica. Para comprobarlo, he ejecutado el comando `id`.

<img width="619" height="81" alt="image" src="https://github.com/user-attachments/assets/ef104953-3f64-4e22-aa37-e8324fefe537" />


## Servidor Samba

Finalmente, configuraremos Samba para permitir el acceso a recursos compartidos con autenticación LDAP o local.

Primero instalamos el paquete `samba`.

<img width="622" height="129" alt="image" src="https://github.com/user-attachments/assets/6c21fb8f-d466-4d52-9e53-1d8fb23e8cdf" />

Primeramente, procederemos a la creación del directorio que queremos compartir y ajustaremos sus permisos y su propiedad. Definiremos el usuario y el grupo correspondientes para garantizar que solo los miembros autorizados tengan acceso al recurso compartido.

<img width="420" height="173" alt="image" src="https://github.com/user-attachments/assets/8ab7f83b-485b-4a4e-98a3-51467352719f" />

Después crearé los usuarios y grupos necesarios para realizar las pruebas.

<img width="488" height="303" alt="image" src="https://github.com/user-attachments/assets/670f67b6-a377-4988-9efd-24839d04e292" />

Y a cada usuario le he asignado su contraseña.

<img width="333" height="292" alt="image" src="https://github.com/user-attachments/assets/732d6887-6da7-4272-8e70-b8f8a5960f74" />

Procederé a editar el archivo `smb.conf` para añadir la declaración del recurso compartido. Esto incluye configurar los parámetros necesarios para que el directorio sea visible y accesible desde la red para los clientes autorizados.

<img width="494" height="377" alt="image" src="https://github.com/user-attachments/assets/ebdfe297-c9ca-491a-bcc8-95adc2d3c96f" />

Para que los cambios realizados en el archivo de configuración se apliquen correctamente, será necesario reiniciar el servicio de Samba. Esto permitirá que el sistema cargue la nueva definición del recurso compartido.

<img width="697" height="393" alt="image" src="https://github.com/user-attachments/assets/b237032d-2590-45d2-bf9f-0655f9bb4984" />

## Configuración del cliente SMB

Accedemos al cliente, que se encuentra en la misma red, como hemos comprobado mediante el comando `ping`.

<img width="1877" height="838" alt="image" src="https://github.com/user-attachments/assets/09237282-2512-4c76-8ab5-a0e350f68321" />

El paquete que debemos instalar es **smbclient**.

<img width="598" height="157" alt="image" src="https://github.com/user-attachments/assets/599e7b12-d689-4383-9e90-fc769d0020b4" />

Y ya podemos conectarnos mediante el navegador de archivos.

<img width="443" height="44" alt="image" src="https://github.com/user-attachments/assets/b119e755-1af1-4368-80b5-5e2c511e6df2" />

Para empezar, entraremos con el usuario anónimo.

<img width="622" height="507" alt="image" src="https://github.com/user-attachments/assets/e3484772-52a0-4194-a94b-ed377b95efee" />

Crearemos una carpeta llamada `anonim`.

<img width="436" height="127" alt="image" src="https://github.com/user-attachments/assets/589511c5-4f21-4a4c-bc69-024c098bc898" />

Y vemos que se crea correctamente.

<img width="251" height="142" alt="image" src="https://github.com/user-attachments/assets/4cca0f9a-53ee-43a5-ad3b-f5f88feaa2da" />

Saldremos.

<img width="213" height="214" alt="image" src="https://github.com/user-attachments/assets/8f96bf84-775c-4799-9dd1-bd055d5482cb" />

Y volveremos a entrar con el usuario `naim`.

<img width="469" height="429" alt="image" src="https://github.com/user-attachments/assets/d43f61a2-0339-4dac-9c7e-8bb924459bd7" />

Creamos una carpeta.

<img width="433" height="113" alt="image" src="https://github.com/user-attachments/assets/6ee1f356-c671-4e98-86ff-f3dce4145ac3" />

Y se crea sin ningún problema.

<img width="240" height="140" alt="image" src="https://github.com/user-attachments/assets/4d0112ca-4f97-4c38-a86e-779daf2f0748" />

Ahora probaremos con el usuario `eros`.

<img width="466" height="429" alt="image" src="https://github.com/user-attachments/assets/457724ab-ef5e-4057-965a-aa287b3b732d" />

Y podemos ver que, con este usuario, no se puede crear ninguna carpeta.

<img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/c087c19b-30f5-4d34-a184-9b1ab245368f" />


## NFS

### 1 ejercicio NFS sin LDAP

En este apartado configuraremos un servidor NFS para compartir directorios con un cliente, sin utilizar autenticación LDAP inicialmente.

Actualizaremos todos los paquetes.

<img width="776" height="233" alt="image" src="https://github.com/user-attachments/assets/68053bfe-5b5c-4193-8ebe-f53d823b4713" />

Primero, en el **servidor**, instalamos el paquete `nfs-kernel-server`.

<img width="775" height="246" alt="image" src="https://github.com/user-attachments/assets/2e988b18-e7fa-4e2e-abf6-eb69aa6b163f" />

Creamos el directorio que queremos compartir y le asignamos los permisos necesarios. En este caso, creamos `/1exercici`.

<img width="778" height="222" alt="image" src="https://github.com/user-attachments/assets/4bca7fa9-e5e6-46fa-bf38-afca5a6033b8" />

Editamos el archivo `/etc/exports` para definir quién puede acceder al recurso y con qué permisos. Añadimos la línea correspondiente a nuestro directorio y a la red o cliente.

<img width="629" height="344" alt="image" src="https://github.com/user-attachments/assets/17e968d5-6660-4dfa-994d-cc05501b0376" />

Aplicamos la nueva configuración y reiniciamos el servicio `nfs-kernel-server` para asegurarnos de que los cambios se aplican correctamente.

<img width="806" height="256" alt="image" src="https://github.com/user-attachments/assets/48a92b86-56ed-472b-b285-c37fe4704200" />

Ahora crearemos un archivo llamado `hola` en la carpeta `/1exercici`.

<img width="359" height="58" alt="2026-02-10_13-00" src="https://github.com/user-attachments/assets/3ce9553d-93d1-4404-9ddb-98e26fc5a809" />

Ahora pasamos al **cliente**. Instalamos los paquetes `nfs-common` y `rpcbind`, y creamos el punto de montaje donde vincularemos el directorio remoto.

<img width="777" height="222" alt="image" src="https://github.com/user-attachments/assets/8959dece-2a68-42d7-91c2-9e1c356936ce" />

Montamos manualmente el recurso compartido NFS en el punto de montaje creado. Utilizamos la IP del servidor y la ruta del directorio exportado.

<img width="772" height="266" alt="image" src="https://github.com/user-attachments/assets/33555c4b-07a7-4c67-a603-7e073bbf22c7" />

Verificamos que tenemos acceso de escritura, si así lo hemos configurado, creando un archivo de prueba dentro del directorio montado.

<img width="769" height="256" alt="image" src="https://github.com/user-attachments/assets/d5185b04-5018-4c4c-b9ee-769d27386c1c" />

Para hacer que el montaje sea permanente y se mantenga después de reiniciar, añadimos la entrada correspondiente al archivo `/etc/fstab`.

<img width="803" height="280" alt="image" src="https://github.com/user-attachments/assets/8331fe14-4987-457c-a6e6-6cc070899a58" />

Finalmente, podemos reiniciar el cliente o ejecutar `mount -a` para comprobar que el recurso se monta automáticamente sin errores.

<img width="194" height="49" alt="image" src="https://github.com/user-attachments/assets/3f33c8f9-cf53-4418-91ec-c656a7ae4522" />

<img width="681" height="104" alt="image" src="https://github.com/user-attachments/assets/23971487-44ea-4c30-b351-91378bd8d42b" />

### NFS con LDAP

Primero, en nuestro servidor prepararemos el directorio.

<img width="413" height="156" alt="2026-02-10_13-51" src="https://github.com/user-attachments/assets/6a237ed6-da20-4b4b-935f-c8ae490b63ce" />

Y, tal como hemos hecho anteriormente, pondremos esta ruta, **/homes**, en el archivo **/etc/exports**.

<img width="508" height="324" alt="2026-02-10_13-53" src="https://github.com/user-attachments/assets/cda2076d-3900-4af4-9a52-47da22df2ed1" />

Ahora iremos a nuestro cliente y haremos lo siguiente.

<img width="723" height="219" alt="image" src="https://github.com/user-attachments/assets/343beb44-7ab9-4eea-b823-d88aac9aa024" />

En el archivo `fstab` pondremos esta línea, tal como hemos hecho anteriormente.

<img width="803" height="306" alt="image" src="https://github.com/user-attachments/assets/0488f3f2-2415-4ecb-a33c-b9970b3a72fb" />

Guardamos y volvemos a la parte del servidor. Ahora crearemos el usuario Marcel. **MUY IMPORTANTE: indica su HOME**, en este caso **/homes**.

<img width="704" height="481" alt="image" src="https://github.com/user-attachments/assets/f485ee1c-975c-4bee-bddd-8eb2d4a291b8" />

Y con `ldapadd` lo añadimos.

<img width="741" height="82" alt="image" src="https://github.com/user-attachments/assets/a1d524d9-dbff-4657-9c4d-e4d91926c139" />

Una vez realizada esta configuración por parte del cliente y del servidor, reiniciaremos el cliente e iniciaremos sesión como el usuario **marcel**. Si todo ha funcionado correctamente, dentro de **/homes/marcel** deberíamos ver las carpetas básicas, como **Descargas**, **Documentos**, etc.

Y sí, se muestran correctamente.

<img width="728" height="155" alt="image" src="https://github.com/user-attachments/assets/3f73369f-4084-40f6-b1a8-84296605c1df" />

<img width="524" height="67" alt="2026-02-18_10-32_1" src="https://github.com/user-attachments/assets/18da9858-f630-4765-b20d-4e8d89038a1d" />

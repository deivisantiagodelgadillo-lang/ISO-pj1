
# Configuración del servidor

Primero, abrimos una terminal dentro de la máquina servidor y ejecutamos el comando **ip a**. Nos apuntaremos la dirección IP que recibimos por DHCP y posteriormente la configuraremos de forma estática desde la interfaz gráfica. Cuando configuramos un servidor, **siempre es recomendable utilizar una dirección IP estática**, ya que una IP dinámica dificultaría el acceso a los servicios que ofrece el servidor, debido a que podría cambiar constantemente.

<img width="746" height="459" alt="Captura de pantalla de 2026-01-08 13-24-13" src="https://github.com/user-attachments/assets/9a3ec543-8a7e-4345-83bc-fcec314ada22" />

<img width="804" height="335" alt="Captura de pantalla de 2026-01-08 13-24-33" src="https://github.com/user-attachments/assets/281fa3ae-7b3e-4150-aad1-dfeac7709e19" />

A continuación, accedemos al archivo **/etc/hostname** utilizando **nano**, donde modificaremos el nombre del dispositivo.

<img width="513" height="92" alt="Captura de pantalla de 2026-01-08 13-26-39" src="https://github.com/user-attachments/assets/2561caec-30f0-4f96-8a15-62777ef3ac9d" />

Haremos lo mismo en el archivo **/etc/hosts**, añadiendo el nuevo hostname a la dirección loopback del equipo. También añadiremos el dominio que configuraremos más adelante asociado a la IP estática configurada anteriormente.

<img width="512" height="134" alt="Captura de pantalla de 2026-01-08 13-28-39" src="https://github.com/user-attachments/assets/e27650e9-98c6-4c48-915c-a8cd61e8e403" />

Ahora instalaremos los servicios necesarios para instalar y administrar LDAP.

<img width="642" height="132" alt="Captura de pantalla de 2026-01-08 13-29-46" src="https://github.com/user-attachments/assets/78e2337c-fb76-42ce-b949-c8f86cc4bf31" />

Durante la instalación, se nos pedirá una contraseña para el usuario administrador de LDAP. Más adelante necesitaremos recordarla.

<img width="671" height="374" alt="Captura de pantalla de 2026-01-08 13-31-56" src="https://github.com/user-attachments/assets/5392226b-889e-4e41-a255-5bccb631efa7" />

Con el comando **slapcat** podremos visualizar todos los elementos del dominio.

<img width="454" height="279" alt="image" src="https://github.com/user-attachments/assets/655e7727-4a91-4b40-9967-c8011ebdcd58" />

Ahora iremos a **Descargas** y descomprimiremos el archivo ZIP descargado desde Moodle.

<img width="560" height="209" alt="image" src="https://github.com/user-attachments/assets/29d8f3b4-fe45-46b1-9b69-f6e78299bddc" />

Con el comando **dpkg-reconfigure slapd** podremos configurar y añadir elementos al dominio de una forma más sencilla. También podríamos utilizar archivos de configuración **.ldif**, aunque resultan menos prácticos.

<img width="561" height="18" alt="image" src="https://github.com/user-attachments/assets/66131f3e-973c-4abc-b772-652b85e35fbf" />

Introducimos el dominio que configuramos previamente en el archivo **/etc/hosts**.

<img width="553" height="282" alt="image" src="https://github.com/user-attachments/assets/793b33e6-413f-4346-b200-07e5a1daef42" />

Indicamos el nombre de la organización.

<img width="559" height="240" alt="image" src="https://github.com/user-attachments/assets/811115e3-1ab1-4134-a40e-1ee3612ff251" />

Asignamos una contraseña, que puede ser la misma utilizada anteriormente.

<img width="558" height="264" alt="image" src="https://github.com/user-attachments/assets/de8287b0-7aa8-46cd-8daa-47bf738354bf" />

Elegimos eliminar la base de datos al purgar.

<img width="557" height="257" alt="image" src="https://github.com/user-attachments/assets/7d7478e7-c514-49ee-8822-d53268df0aa0" />

Finalmente, movemos la base de datos antigua y ejecutamos nuevamente **slapcat** para comprobar que todos los cambios se han aplicado correctamente.

<img width="559" height="266" alt="image" src="https://github.com/user-attachments/assets/fe1d9ac2-ff6b-4567-8da6-73b4a271012a" />

De momento no tendremos elementos creados (usuarios, grupos o unidades organizativas), pero el dominio ya aparecerá correctamente configurado.

<img width="474" height="275" alt="image" src="https://github.com/user-attachments/assets/3d073a90-8fd4-4aa7-bfa3-af6a6c547c54" />

# Configuración del cliente

Ahora pasaremos a configurar el cliente. Previamente comprobaremos que existe conectividad entre cliente y servidor. Después instalaremos los paquetes necesarios.

<img width="557" height="21" alt="image" src="https://github.com/user-attachments/assets/98a56ec0-7bb9-4c6f-b8aa-bb0b82a307ba" />

Durante la instalación aparecerá el asistente de configuración, donde indicaremos la dirección IP o dominio del servidor LDAP.

<img width="562" height="279" alt="image" src="https://github.com/user-attachments/assets/de5f7ed7-10ad-4da0-84fa-19ebae6ac55b" />

También introduciremos el nombre del dominio.

<img width="562" height="274" alt="image" src="https://github.com/user-attachments/assets/06d2f696-d34f-4f5b-8df3-524e36b9b16f" />

Seleccionaremos la versión LDAP 3.

<img width="560" height="291" alt="image" src="https://github.com/user-attachments/assets/58f0f443-5d90-4ba1-82c5-50877bade699" />

En las siguientes opciones seleccionaremos “Sí”.

<img width="554" height="337" alt="image" src="https://github.com/user-attachments/assets/aa5bf757-42d2-4adf-9562-a091abd39a02" />

<img width="561" height="317" alt="image" src="https://github.com/user-attachments/assets/af2d330d-4249-4c3e-abaa-b941072cf15f" />

Indicaremos el usuario administrador.

<img width="503" height="314" alt="image" src="https://github.com/user-attachments/assets/0b4abaf2-fc1c-4adf-868d-ae4acfdb8384" />

Y posteriormente su contraseña.

<img width="556" height="299" alt="image" src="https://github.com/user-attachments/assets/e20e6492-1a5b-47b0-90a8-7910ec183fe1" />

En caso de equivocarnos en algún paso, podremos volver a ejecutar el asistente mediante el siguiente comando.

<img width="552" height="22" alt="image" src="https://github.com/user-attachments/assets/55bb59b4-7b15-4b0d-884f-75d212aacfe9" />

A continuación editaremos el archivo **/etc/nsswitch.conf** y añadiremos **files systemd** en las líneas correspondientes.

<img width="561" height="212" alt="image" src="https://github.com/user-attachments/assets/e1bc2fdc-bbb5-4c4d-a96d-a6a3487bb2f1" />

Después editaremos el archivo **/etc/pam.d/common-password** y eliminaremos la parte indicada de la línea.

<img width="561" height="245" alt="image" src="https://github.com/user-attachments/assets/da692876-b4ee-4f83-a05e-d5d20bea2353" />

Por último, dentro del archivo **/etc/pam.d/common-session** añadiremos la última línea mostrada en la captura. Esto permitirá que, cuando un usuario cambie su contraseña, se actualice automáticamente también en el servidor LDAP.

<img width="560" height="362" alt="image" src="https://github.com/user-attachments/assets/c1f8beab-69ea-48d5-b795-e5cf52e23324" />

Ahora modificaremos el archivo **/usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf** añadiendo la configuración correspondiente.

<img width="559" height="111" alt="image" src="https://github.com/user-attachments/assets/6a1dcfc2-ec1b-4108-84c9-953dd2b8415e" />

Una vez realizado todo el proceso, ya podremos cerrar sesión e iniciar con el nuevo usuario LDAP creado, llamado **alu1**.

<img width="468" height="573" alt="image" src="https://github.com/user-attachments/assets/6622b21f-43f3-4dfb-9b2c-a1fd8196be19" />

# Gestión del dominio mediante comandos

En este apartado se han realizado distintas actividades utilizando comandos LDAP y archivos `.ldif`.

## Requisitos previos

Primero ejecutaremos `dpkg-reconfigure slapd` para dejar la base de datos vacía y únicamente con el dominio y el usuario administrador creados.

<img width="762" height="177" alt="2026-02-20_08-55" src="https://github.com/user-attachments/assets/400fae27-894c-4b4e-a29a-0faf500c713c" />

<img width="505" height="306" alt="2026-02-20_08-57" src="https://github.com/user-attachments/assets/caf7e644-af67-4baa-9ab1-0f5a70df8026" />

Después descargaremos el archivo `dades_pt10.ldif` desde Moodle y lo cargaremos mediante `ldapadd`, modificando previamente el dominio.

<img width="522" height="312" alt="2026-02-20_09-03" src="https://github.com/user-attachments/assets/128dff1e-5d9e-4ad1-902c-f9c534c5d87e" />

<img width="808" height="421" alt="2026-02-20_09-06" src="https://github.com/user-attachments/assets/16d6b624-a920-4ebd-bd1f-c2f9c4db43e2" />

Finalmente utilizaremos nuevamente `slapcat` para verificar que todos los datos se han cargado correctamente.

<img width="508" height="530" alt="2026-02-20_09-09" src="https://github.com/user-attachments/assets/12e342aa-852d-43a9-8e5c-1e971f7f7163" />

# Entorno gráfico

Para administrar LDAP desde una interfaz gráfica existen varias opciones:

* phpLDAPadmin
* Apache Directory Studio
* JXplorer
* LDAP Account Manager (LAM)

En este caso se ha escogido **LAM**, ya que resulta muy intuitivo y sencillo de utilizar.

## Requisitos previos

Primero instalaremos todos los paquetes necesarios para el correcto funcionamiento de LAM y PHP.

<img width="733" height="196" alt="2026-02-18_17-21" src="https://github.com/user-attachments/assets/2e67a43a-7ae1-421d-9c12-90c343c3a69c" />

A continuación descargaremos el paquete `.deb`.

<img width="734" height="134" alt="2026-02-18_17-23" src="https://github.com/user-attachments/assets/4f8f4c3b-7e2f-4b3d-ab51-56dd18ea5d0a" />

<img width="735" height="131" alt="2026-02-18_17-24" src="https://github.com/user-attachments/assets/cf3658e4-0da9-4c6f-b9ff-3510e2f024fd" />

## Configuración del entorno gráfico

Una vez instalado, podremos acceder vía navegador mediante la IP del servidor y el directorio `/lam`. Aquí estableceremos una contraseña para acceder al panel administrativo.

<img width="693" height="401" alt="2026-02-18_17-27" src="https://github.com/user-attachments/assets/ecbd687c-afe4-442e-af19-12fdb5106fde" />

Después de guardar la configuración, el sistema solicitará iniciar sesión.

<img width="791" height="527" alt="2026-02-18_17-41" src="https://github.com/user-attachments/assets/105f0a65-aa52-4feb-9230-21765132fabb" />

A continuación accederemos a **Editar perfiles del servidor**.

<img width="440" height="338" alt="2026-02-18_17-42" src="https://github.com/user-attachments/assets/c78f32b8-1756-4669-bebc-466c336f6554" />

Y seleccionaremos la opción indicada.

<img width="787" height="455" alt="2026-02-18_17-42_1" src="https://github.com/user-attachments/assets/1cf79ab5-4dca-4981-885a-95744a8505cd" />

<img width="621" height="353" alt="2026-02-18_18-00" src="https://github.com/user-attachments/assets/f7f2eaee-9f3b-472a-adcd-c57aaa0c7a56" />

Una vez dentro configuraremos los parámetros LDAP.

<img width="700" height="267" alt="2026-02-18_18-06" src="https://github.com/user-attachments/assets/9f9a40db-6f54-4ff1-ad7d-7fe0878d9f7c" />

También deberemos acceder a **Account Types** y modificar la configuración correspondiente.

<img width="826" height="368" alt="2026-02-18_18-11" src="https://github.com/user-attachments/assets/2900ac29-6e4e-4c2e-8b69-0d84b6ab9ea0" />

Finalmente ya podremos iniciar sesión con el usuario administrador del dominio LDAP.

<img width="389" height="312" alt="2026-02-18_18-18" src="https://github.com/user-attachments/assets/6b005c3f-aff0-49b6-8b59-2929a11b307f" />

Aquí podremos visualizar todos los usuarios creados.

<img width="1073" height="545" alt="2026-02-18_18-18_1" src="https://github.com/user-attachments/assets/cc7177d7-9757-4061-8fb3-2dece95f9b86" />

# Servidor Samba

A continuación configuraremos Samba para permitir el acceso a recursos compartidos mediante autenticación local o LDAP.

Primero instalaremos el paquete `samba`.

<img width="703" height="155" alt="image" src="https://github.com/user-attachments/assets/3cbde56f-b1f3-4b70-b3eb-324d4d48ed76" />

Después crearemos el directorio que queremos compartir y ajustaremos sus permisos y propietario.

<img width="604" height="202" alt="image" src="https://github.com/user-attachments/assets/1cebacd2-3e71-4a7e-ac6f-711db3fe35f0" />

Posteriormente crearemos los usuarios y grupos necesarios para realizar las pruebas.

<img width="562" height="304" alt="image" src="https://github.com/user-attachments/assets/40433e5a-d777-442a-b67e-a162f2970699" />

A cada usuario le asignaremos su contraseña.

<img width="333" height="292" alt="image" src="https://github.com/user-attachments/assets/732d6887-6da7-4272-8e70-b8f8a5960f74" />

Ahora editaremos el archivo `smb.conf` para añadir la configuración del recurso compartido.

<img width="494" height="377" alt="image" src="https://github.com/user-attachments/assets/ebdfe297-c9ca-491a-bcc8-95adc2d3c96f" />

Finalmente reiniciaremos el servicio Samba para aplicar todos los cambios.

<img width="697" height="393" alt="image" src="https://github.com/user-attachments/assets/b237032d-2590-45d2-bf9f-0655f9bb4984" />

# Configuración cliente SMB

Accedemos al cliente y comprobamos la conectividad mediante `ping`.

<img width="627" height="247" alt="image" src="https://github.com/user-attachments/assets/6b247cf5-9c9b-4c71-bb17-37fcdc317169" />

Instalaremos el paquete `smbclient`.

<img width="607" height="154" alt="image" src="https://github.com/user-attachments/assets/7e04ced9-4fbf-4d32-86dd-8be3c7b87685" />

Una vez instalado ya podremos conectarnos mediante el explorador de archivos.

<img width="443" height="44" alt="image" src="https://github.com/user-attachments/assets/b119e755-1af1-4368-80b5-5e2c511e6df2" />

Primero accederemos con el usuario anónimo.

<img width="463" height="437" alt="image" src="https://github.com/user-attachments/assets/fb849993-4bf2-4554-b008-bb6d308d19d8" />

Crearemos una carpeta llamada `anonim`.

<img width="436" height="127" alt="image" src="https://github.com/user-attachments/assets/589511c5-4f21-4a4c-bc69-024c098bc898" />

Y comprobaremos que se crea correctamente.

<img width="251" height="142" alt="image" src="https://github.com/user-attachments/assets/4cca0f9a-53ee-43a5-ad3b-f5f88feaa2da" />

Después cerraremos sesión.

<img width="261" height="260" alt="image" src="https://github.com/user-attachments/assets/9e3a2c98-11de-41e3-85c5-25ae746493a2" />

Ahora accederemos con el usuario `naim`.

<img width="469" height="429" alt="image" src="https://github.com/user-attachments/assets/d43f61a2-0339-4dac-9c7e-8bb924459bd7" />

Crearemos una carpeta.

<img width="433" height="113" alt="image" src="https://github.com/user-attachments/assets/6ee1f356-c671-4e98-86ff-f3dce4145ac3" />

Y veremos que se crea correctamente.

<img width="240" height="140" alt="image" src="https://github.com/user-attachments/assets/4d0112ca-4f97-4c38-a86e-779daf2f0748" />

Finalmente probaremos con el usuario `eros`.

<img width="466" height="429" alt="image" src="https://github.com/user-attachments/assets/457724ab-ef5e-4057-965a-aa287b3b732d" />

Y comprobaremos que este usuario no tiene permisos para crear carpetas.

<img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/c087c19b-30f5-4d34-a184-9b1ab245368f" />

# NFS

## Primer ejercicio NFS sin LDAP

En este apartado configuraremos un servidor NFS para compartir directorios con un cliente sin utilizar LDAP.

Primero actualizaremos todos los paquetes del sistema.

<img width="803" height="238" alt="2026-02-10_12-50" src="https://github.com/user-attachments/assets/be38697b-61f7-43e2-b3f8-41886a244f46" />

En el servidor instalaremos el paquete `nfs-kernel-server`.

<img width="708" height="219" alt="2026-02-10_12-50_1" src="https://github.com/user-attachments/assets/48d5b0d9-8c9a-4982-8f5c-547c53d813ed" />

Crearemos el directorio que queremos compartir y asignaremos los permisos correspondientes.

<img width="632" height="180" alt="2026-02-10_12-53" src="https://github.com/user-attachments/assets/17215ed7-922b-4686-86b4-b7d49a086eef" />

Después editaremos `/etc/exports` para definir el recurso compartido.

<img width="507" height="310" alt="2026-02-10_12-57" src="https://github.com/user-attachments/assets/8b0dc7a1-c06e-4bf5-971f-d58e9d3c5b20" />

Aplicaremos la configuración y reiniciaremos el servicio.

<img width="809" height="268" alt="2026-02-10_12-58" src="https://github.com/user-attachments/assets/9ea595ec-0125-4bf8-8b7c-56010b3f9131" />

Crearemos un archivo llamado `hola` dentro del directorio compartido.

<img width="359" height="58" alt="2026-02-10_13-00" src="https://github.com/user-attachments/assets/3ce9553d-93d1-4404-9ddb-98e26fc5a809" />

En el cliente instalaremos `nfs-common` y `rpcbind`.

<img width="642" height="178" alt="2026-02-10_13-03" src="https://github.com/user-attachments/assets/fa5ca1eb-1728-4cef-b7ff-c2292e3fa016" />

Montaremos manualmente el recurso compartido utilizando la IP del servidor.

<img width="597" height="198" alt="2026-02-10_13-09" src="https://github.com/user-attachments/assets/d37a100c-4231-4079-90b2-f2c0d5d33007" />

Verificaremos que tenemos acceso creando un archivo de prueba.

<img width="623" height="204" alt="2026-02-10_13-10" src="https://github.com/user-attachments/assets/60cd3a43-a916-46f2-b0fe-5f8b8255d8a6" />

Para que el montaje sea permanente añadiremos la entrada correspondiente en `/etc/fstab`.

<img width="917" height="356" alt="2026-02-10_13-23" src="https://github.com/user-attachments/assets/4d42a169-bb0f-4fae-85aa-221d550d09ef" />

Finalmente podremos reiniciar el cliente o ejecutar `mount -a` para comprobar el montaje automático.

<img width="290" height="46" alt="2026-02-10_13-16_1" src="https://github.com/user-attachments/assets/2dfff157-33cb-47b2-a83e-ad2070582c8d" />

<img width="336" height="70" alt="2026-02-10_13-20" src="https://github.com/user-attachments/assets/136d4a63-b6ea-44f0-b797-d207a753bbc9" />

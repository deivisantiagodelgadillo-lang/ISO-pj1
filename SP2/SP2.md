# SPRINT 2: INSTAL·LACIÓ, CONFIGURACIÓ DE PROGRAMARI DE BASE I GESTIÓ DE FITXERS

---

##  1. Sistemes de fitxers i particions

### Mida sector

Es la unidad mínima física en la que se guardan los datos en un disco.
Por defecto, el tamaño del sector es de 512 bytes y no puede modificarse.

<img width="556" height="116" alt="2025-12-01_19-18" src="https://github.com/user-attachments/assets/f51a3d1f-de2a-4776-b321-5b89d51f2e11" />

### Mida block

Es la unidad mínima lógica en la que se guardan los datos a nivel de sistema operativo.
Por defecto, el tamaño es de 4096 bytes (8 sectores) y sí se puede modificar cuando se formatea la partición.
Cada partición del disco puede tener un tamaño de blog y un sistema de archivos diferente.

<img width="324" height="19" alt="2025-12-01_19-20" src="https://github.com/user-attachments/assets/6957d4bc-62d9-4810-900e-ad8fe477fc2b" />

### Fragmentación interna

Se produce cuando los blogs son demasiado grandes para lo que se quiere guardar y se acaba desperdiciando espacio en el disco.

### Fragmentación externa

Se produce cuando un archivo no está guardado en bloques consecutivos de la memoria.
Esto provoca que los accesos sean más lentos y, por tanto, baja el rendimiento.

<img width="970" height="276" alt="2025-12-01_19-23" src="https://github.com/user-attachments/assets/9e523ebc-7593-41aa-95bd-37d24c887cd7" />

### Sistemes de fitxers

Hay muchos tipos, cada uno optimizado para diferentes usos, y cada sistema tiene unas limitaciones.

Windows: NTFS y FAT32

<img width="520" height="88" alt="2025-10-27_13-02_1" src="https://github.com/user-attachments/assets/f49d0d6d-0100-4308-a376-8c80b559eb54" />

Ubuntu: ext4

<img width="733" height="259" alt="2025-10-27_13-02" src="https://github.com/user-attachments/assets/fb7fb3ca-ffdd-4128-874a-0b8aff9af04f" />

### Tipus de formateig

Bajo nivel:
Borra archivos y el sistema de archivos. Trate de reparar sectores defectuosos, pero requiere programas específicos y no se puede realizar mediante el SO.

Medio nivel:
Al igual que el de alto nivel, pero marca los sectores defectuosos si los hay.

Alto nivel:
No borra los archivos, sólo el sistema de archivos. Si encuentra sectores defectuosos, los ignora.

### Partició

Una partición es un pedazo físico del disco duro.
Con GPARTED podemos gestionar particiones, pero no podemos modificar el tamaño de blog.

### Volum

Es una capa de abstracción que se coloca sobre las particiones y/o discos.

### Gestió de particions

Herramienta GPARTED

<img width="867" height="541" alt="2025-10-27_12-34" src="https://github.com/user-attachments/assets/6a44195d-807f-4bd1-b402-d7931d014edd" />

<img width="621" height="462" alt="2025-10-27_12-43" src="https://github.com/user-attachments/assets/714874eb-b0cc-41a6-96e7-5ec6afdde4f8" />

<img width="809" height="556" alt="2025-10-27_12-42" src="https://github.com/user-attachments/assets/daf80ee5-00a0-4a88-b527-680403a6ff2b" />

Comandos: herramientas CLI para gestionar particiones Particiones

<img width="705" height="246" alt="2025-10-27_12-51" src="https://github.com/user-attachments/assets/f3b766fd-0afc-4058-b9a6-8f1443ea49bc" />

Medida de las particiones

<img width="784" height="384" alt="2025-10-27_13-04" src="https://github.com/user-attachments/assets/438b800b-23e8-4db1-a760-48a065228aca" />

Crearemos la carpeta p1 y montamos la partición de disco /dev/sdb1 en el directorio /mnt/p1

<img width="585" height="223" alt="2025-10-27_13-10" src="https://github.com/user-attachments/assets/443f8da4-1061-4772-b5fe-c52b22589bf6" />

<img width="641" height="209" alt="2025-10-27_13-14" src="https://github.com/user-attachments/assets/46862cf1-5807-42ed-85fa-a3d27500101b" />

Añadimos la partición /dev/sdb1 al archivo /etc/fstab para montarla automáticamente como **ext4** en el punto /mnt/p1 cada vez que el sistema se encienda.

<img width="721" height="391" alt="2025-10-27_13-18" src="https://github.com/user-attachments/assets/9575fd73-a2be-45a8-adfd-1e7dd7c12040" />

<img width="499" height="133" alt="2025-10-27_13-21" src="https://github.com/user-attachments/assets/478d26af-97da-49f5-8845-508455395929" />

---

## 2. Gestió de processos

Configuración Previa y Archivos del Sistema Antes de empezar con la creación de usuarios, hicimos una revisión de los principales archivos de configuración para entender dónde se almacena la información en el sistema.
Revisión del Entorno Gráfico En primer lugar, comprobamos el estado de los usuarios desde la interfaz gráfica para ver las opciones disponibles y confirmar la existencia del usuario ClienteUsuari.

<img width="792" height="481" alt="2025-11-04_12-50" src="https://github.com/user-attachments/assets/ad5ba4c7-8981-4d1a-88b5-60d7cf82834a" />

Función del Archivo /etc/passwd: Iremos a mirar el archivo /etc/passwd, que es fundamental porque contiene la lista de todos los usuarios del sistema. Para cada usuario, nos indica el nombre, el identificador de usuario (UID), el identificador de grupo primario (GID), el directorio personal y la shell que se ejecutará al iniciar la sesión.

<img width="1036" height="567" alt="2025-11-04_12-53" src="https://github.com/user-attachments/assets/27414ad4-93ad-478e-90be-9439807abdcb" />

Función de Archivo /etc/shadow: Este archivo es crítico para la seguridad. Comprobamos su contenido, sabiendo que guarda los hashes (contraseñas cifradas) de los usuarios y la información sobre la antigüedad y caducidad de las contraseñas. Sólo el usuario root tiene permiso para leerlo.

<img width="740" height="481" alt="2025-11-04_12-55" src="https://github.com/user-attachments/assets/a13793ed-2924-4f8c-8e70-95d6c1587b38" />

Función de Archivo /etc/group: Hemos examinado el archivo /etc/group, que sirve para definir todos los grupos existentes en el sistema y listar qué usuarios pertenecen a cada grupo secundario.

<img width="1153" height="482" alt="2025-11-04_12-56" src="https://github.com/user-attachments/assets/10a29b4a-2d2e-4461-9c60-53aa92d27473" />

Función del Archivo /etc/gshadow: Por último, revisamos /etc/gshadow, que es el equivalente seguro de /etc/group. Este archivo se utiliza para guardar contraseñas cifradas para grupos, en caso de que un grupo sea protegido con contraseña, y gestiona los administradores de cada grupo.

<img width="773" height="517" alt="2025-11-04_12-58" src="https://github.com/user-attachments/assets/2d4cf5a3-d25d-4170-8e8b-8f287809b4a8" />

--- 

## 3. Gestió d'usuaris i grups i permisos

Creación y Gestión del Usuario gina Ahora iremos a crear el usuario gina utilizando el comando adduser, que es la herramienta más sencilla, ya que automatiza muchos pasos.
Creación con adduser y Asignación de Contraseña: Hemos ejecutado adduser gina. El proceso nos ha creado el usuario, el grupo primario y nos ha pedido la contraseña. Comprobamos que el sistema nos avisa si la contraseña es demasiado corta.

<img width="827" height="518" alt="2025-11-04_13-02" src="https://github.com/user-attachments/assets/046a22f7-716d-41a2-8587-a909e5641ddb" />

Verificación del Directorio Personal: Verificamos que el comando adduser creó automáticamente el directorio /home/gina con su estructura interna por defecto.

<img width="922" height="153" alt="2025-11-04_13-05" src="https://github.com/user-attachments/assets/27bb812d-475e-4d93-bcc9-6aa93385f354" />

Creación y Configuración Avanzada del Usuario gina2: Para demostrar un método más manual, creamos el usuario gina2 con useradd y tuvimos que configurar su entorno después.
Acciones que llevamos a cabo:

Crear el usuario (useradd), establecer la contraseña (passwd), modificar la shell de inicio de sesión en /bin/bash (usermod -s), crear el directorio personal manualmente (mkdir), cambiar el propietario del directorio de root en gina2 (chown).

<img width="816" height="667" alt="2025-11-04_13-12" src="https://github.com/user-attachments/assets/f30dffe0-0574-4d8d-84a2-a59b83e98a2b" />

Bloqueo y Desbloqueo de Usuarios (Gestión Fina de gina): Una vez que el usuario gina estaba operativo, demostramos cómo podemos bloquear una cuenta temporalmente, evitando que nadie pueda iniciar sesión sin necesidad de eliminar al usuario.

3Bloqueo (usermod -L) y Desbloqueo (usermod -U) ¿Qué hace el bloqueo?: Utilizamos usermod con la opción -L(Lock). Comprobamos con grep que el sistema añade un signo de admiración (!) al principio del hash de la contraseña en el archivo /etc/shadow, invalidándola.

¿Qué hace el desbloqueo?: Luego utilizamos la opción -U (Unlock) de usermod, que elimina el signo de admiración y restaura la funcionalidad de la contraseña.

<img width="789" height="108" alt="2025-11-04_13-29" src="https://github.com/user-attachments/assets/a9883ff8-f769-4f47-bc20-bd6ee65d90b9" />

<img width="809" height="197" alt="2025-11-04_13-30" src="https://github.com/user-attachments/assets/e60bb793-b9b4-473b-8426-8fb3ee44f25c" />

Eliminación de Usuarios: Finalizadas las pruebas, procedimos a la eliminación de los usuarios gina y gina2 utilizando los métodos habituales.

Eliminación del Usuario gina con deluser: Eliminamos gina con deluser, que es el pedido recomendado para sistemas Debian/Ubuntu. Este pedido se encarga de limpiar las referencias al grupo primario del usuario si no tiene más miembros.

Eliminación del Usuario gina2 con userdel -r: Eliminamos gina2 con userdel utilizando la opción -r (remove home directory) para borrar también su directorio personal. Utilizamos este comando ya que gina2 fue creado con el método useradd (más manual).

<img width="615" height="325" alt="2025-11-04_13-24" src="https://github.com/user-attachments/assets/292c2b3f-5983-4b73-a25a-c1d209b6eeef" />

Cambio de Nombre y Eliminación del Grupo asixb: Para practicar la modificación de grupos, cambiamos el nombre de asixb a asix con el comando groupmod -n. Luego, eliminamos el grupo utilizando groupdel.

¿Qué hace groupmod -n?: Modifica el nombre de un grupo sin afectar al GID ni a los usuarios miembros.

<img width="807" height="201" alt="2025-11-04_13-35" src="https://github.com/user-attachments/assets/cfdd0780-f6c5-4cdd-8f26-fea8b31cc218" />

Cambio de Nombre de Grupo Hicimos otro ejemplo de cambio de nombre para consolidar el conocimiento, cambiando el grupo parchis a damas.

<img width="804" height="112" alt="2025-11-17_11-54" src="https://github.com/user-attachments/assets/ba165423-8607-4d0d-b247-00bd5463e19a" />

Verificación de Nuevos Usuarios (Usuarios de Colores): Comprobamos que los usuarios con nombres de colores (azul, rojo, amarillo y verde) se habían creado correctamente, observando las últimas líneas del archivo /etc/passwd. Esto nos permite ver sus UID y GID asignados.

<img width="799" height="132" alt="2025-11-17_11-53" src="https://github.com/user-attachments/assets/dc456a4d-87b8-4d4b-a306-d482a1dd9a86" />

Gestión Avanzada de Miembros de Grupos: Demostramos diferentes formas de añadir y sacar usuarios de un grupo existente, utilizando herramientas especializadas para la gestión de miembros.
Métodos para Añadir Usuarios a Grupos Secundarios: Para un grupo de prueba (asix1r), añadimos tres usuarios (ivan, paz, iker) utilizando tres pedidos diferentes, ya que cada uno tiene un uso ligeramente distinto.

<img width="802" height="219" alt="2025-11-04_13-38" src="https://github.com/user-attachments/assets/a04049dd-016d-495f-af3d-815a743e68b5" />

Administración y Gestión de Miembros con gpasswd: Utilizamos gpasswd para demostrar cómo asignar administradores de grupo y cómo intentaríamos eliminar a sus miembros.

¿Qué hace gpasswd -A?: Añade un usuario como administrador del grupo.

Añadimos aaron como administrador de asix1r y comprobamos la modificación en el archivo /etc/gshadow, que es donde se guardan estos permisos.

<img width="711" height="192" alt="2025-12-01_21-14" src="https://github.com/user-attachments/assets/10d2d0d0-b54f-4f6a-b82b-9dab9a23ccef" />

Métodos para Eliminar Usuarios de Grupos: Utilizamos el grupo parchis (con miembros rojo, verde y amarillo) para demostrar los dos pedidos principales para sacar a miembros de un grupo:

<img width="806" height="363" alt="2025-11-17_11-58" src="https://github.com/user-attachments/assets/156911b9-64dc-49e6-8c3c-1481f7663a30" />

<img width="817" height="238" alt="2025-11-17_12-02" src="https://github.com/user-attachments/assets/d9dd9168-724e-4d62-b3b0-ab7cf1e5aca5" />

Preparo la Plantilla de Usuario (/etc/skel) Ante todo, entro en el directorio esquelético (/etc/skel), que es la plantilla para los nuevos usuarios. Yo quiero que, por defecto, tengan algo más que los archivos básicos.
He creado una nueva carpeta que he llamado prueba (mkdir prueba), un archivo vacío llamado hola (touch hola) y de esta forma, cualquier usuario nuevo que cree a partir de ahora tendrá estos dos elementos en su directorio personal.

<img width="692" height="457" alt="2025-11-17_12-07" src="https://github.com/user-attachments/assets/9a8b2521-124b-4a20-b193-3396bb438664" />

Definimos los Parámetros Generales (/etc/adduser.conf) Luego, voy a configurar cómo deben crearse los usuarios con la herramienta adduser. He editado el archivo /etc/adduser.conf y he realizado tres cambios clave:
Cambio la ubicación de los Home Directorias: He cambiado DHOME del estándar /home a /var. Esto significa que los directorios personales irán a /var/nombre_usuario.

Cambio los UIDs/GIDs: Quiero que los nuevos usuarios y sus grupos empiecen a partir de 3000; por eso he definido FIRST_UID=3000 y FIRST_GID=3000.

<img width="727" height="91" alt="2025-11-17_12-10" src="https://github.com/user-attachments/assets/90b1d0de-dc6f-4a16-9bd8-a99b5e936913" />

<img width="440" height="167" alt="2025-11-17_12-12" src="https://github.com/user-attachments/assets/b33a60af-cf51-4b92-9752-4f5d1c9d09e0" />

Definimos las Reglas de Seguridad (/etc/login.defs) Por motivos de seguridad, he definido una política de contraseñas global. En /etc/login.defs, he establecido estas reglas:
Validez Máxima: He puesto PASS_MAX_DAYS 20. Las contraseñas caducarán a los 20 días.

Intervalo Mínimo: He puesto PASS_MIN_DAYS 15. Habrá que esperar 15 días entre cambio y cambio de contraseña.

Avisos: He definido PASS_WARN_AGE 3. El usuario recibirá un aviso 3 días antes de que la contraseña caduque.

<img width="260" height="81" alt="2025-11-17_12-13" src="https://github.com/user-attachments/assets/9bda57f6-94ff-419b-88fd-6728a36b0bcc" />

Me aseguro que Shell sea Bash (/etc/default/useradd) Como la herramienta useradd es de bajo nivel ya veces utiliza una shell más simple (/bin/sh), he editado /etc/default/useradd y he cambiado SHELL a /bin/bash. Así me aseguro que cualquier usuario, independientemente de cómo se cree, utilice Bash.

<img width="685" height="207" alt="2025-11-17_12-19" src="https://github.com/user-attachments/assets/e17b1b49-2e7c-409b-9845-317ee333c613" />

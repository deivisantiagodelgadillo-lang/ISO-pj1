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

## Gestió de processos

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

## Gestió d'usuaris i grups i permisos

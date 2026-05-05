# **Sprint 2 - Windows: Discs, Quotes, Scripts, Processos i ACLs**

## **Fase 1 – Preparació del sistema**

**Pas 1. Afegir un nou disc virtual a la màquina virtual**

Creamos el disco y lo insertamos en la máquina virtual.

<img width="530" height="317" alt="2026-05-05_10-13" src="https://github.com/user-attachments/assets/864f2e87-72ba-46a0-a456-1f19bd81970e" />

**Pas 2. Iniciar Windows i obrir Gestió de discs**
Podemos ver y administrar el disco desde Gestión de discos, de Windows. Confirmamos que el sistema reconoce el disco, y lo marca como espacio sin asignarlo.

<img width="839" height="553" alt="2026-05-05_10-15" src="https://github.com/user-attachments/assets/d87cd68c-b8d1-4021-bb02-72e5713c4f96" />

**Pas 3. Inicialitzar el disc, crear dues particions: una anomenada Dades i una en FAT32 anomenada Portable**

Creación de la partición NTFS Creamos un nuevo volumen simple en el disco.

<img width="651" height="257" alt="2026-05-05_10-17" src="https://github.com/user-attachments/assets/700dad94-f3f7-4155-99ae-922f866e7207" />

Especificamos el tamaño y asignamos una letra a la unidad.

<img width="358" height="322" alt="2026-05-05_10-17_1" src="https://github.com/user-attachments/assets/5e039eaa-933e-41cf-a1c0-4cbe55377466" />

<img width="343" height="314" alt="2026-05-05_10-18" src="https://github.com/user-attachments/assets/4e94b6f2-59ae-484c-9cfc-3eb72463f518" />

Nombramos a la partición y por último, podemos ver el resumen de la operación.

<img width="428" height="322" alt="2026-05-05_10-20" src="https://github.com/user-attachments/assets/da2f3319-1bd9-4de8-8964-52320e5a303d" />

<img width="442" height="348" alt="2026-05-05_10-20_1" src="https://github.com/user-attachments/assets/c1fb9af7-98d8-49d2-898b-bec688b08e11" />

Creación de la partición FAT32 Creamos el segundo volumen simple en el disco, especificamos la medida y le asignamos una letra a la unidad.

<img width="345" height="340" alt="2026-05-05_10-23" src="https://github.com/user-attachments/assets/a59f6c52-2496-4d19-93b9-267932d8dd86" />

<img width="356" height="318" alt="2026-05-05_10-23_1" src="https://github.com/user-attachments/assets/0187a7eb-5d69-4a84-a5f8-051a5d820554" />

Nombramos la partición y Finalmente, podemos ver el resumen de la operación.

<img width="442" height="331" alt="2026-05-05_10-25" src="https://github.com/user-attachments/assets/060ee792-d68e-4680-aa1f-9af90d012d1c" />

<img width="442" height="341" alt="2026-05-05_10-25_1" src="https://github.com/user-attachments/assets/4b2009a0-5a66-46cd-a2b1-dee95b417152" />

**Pas 4. Assignar lletres i comprovar amb diskpart la configuració**

Verificaremos la configuración con una consola CMD con privilegios de administrador y el comando diskpart.

El pedido nos muestra:

El disco original (40GB) y la letra C:
El disco sobre el que estamos trabajando, con la partición Datos (3MB, formato NTFS) y la partición Portable (2102 MB, formato FAT32)

<img width="526" height="495" alt="2026-05-05_10-28" src="https://github.com/user-attachments/assets/8663fa90-ae3e-4561-83b2-52153dd11d76" />

## **Fase 2 – Quotes i usuaris**

**Pas 5 – Activar quotes de disc a la partició Dades (NTFS)**

Las cuotas de disco en Windows permiten limitar el espacio que cada usuario puede utilizar dentro de una partición NTFS. Para activarlas, abrimos el Explorador de Windows, clic derecho sobre la unidad Datos (E:) y seleccionamos Propiedades.

<img width="1216" height="872" alt="Gemini_Generated_Image_rr4q2grr4q2grr4q" src="https://github.com/user-attachments/assets/ffc16a16-43f3-495e-b4e4-49c24049e474" />

En la ventana de propiedades nos dirigimos a la pestaña Cuota y hacemos clic en Mostrar configuración de cuota.

<img width="1344" height="799" alt="Gemini_Generated_Image_tphm74tphm74tphm" src="https://github.com/user-attachments/assets/2b9eb122-c37a-4d85-916b-d2863df40e39" />

**Pas 6 – Establir límit de 300 MB per usuari, amb notificació d'advertència**

Dentro del panel de configuración de cuotas, activamos las opciones:

Habilita la administración de cuota: activa el sistema de cuotas.
Denegar espacio en disco a usuarios que superen el límite: bloquea la escritura cuando se supera el límite.
Limitar espacio en disco a: 300 MB
Establecer el nivel de advertencia en: 150 KB (el usuario recibirá un aviso cuando casi llene el límite)
Registrar un evento cuando algún usuario supere su límite de cuota
Registrar un evento cuando algún usuario supere su nivel de advertencia

<img width="313" height="398" alt="2026-05-05_10-37" src="https://github.com/user-attachments/assets/4e7c8742-9f63-4d54-86db-eb471fae1e14" />

**Pas 7 – Crear dos usuaris locals: alumne1 i alumne2**

Para crear usuarios locales en Windows, ejecute lusrmgr.msc (Gestión de usuarios y grupos locales) desde la ventana Ejecutar (Win + R).

<img width="353" height="177" alt="2026-05-05_10-38" src="https://github.com/user-attachments/assets/7ed07b7b-bcb0-4c00-87e4-8d7338f17e19" />

Dentro de la consola, hacemos clic derecho sobre Usuarios - Usuario nuevo

<img width="1269" height="832" alt="Gemini_Generated_Image_496cnm496cnm496c" src="https://github.com/user-attachments/assets/e239574e-d7c3-47ec-a263-d8c9a9106771" />

Creamos el usuario alumno1 con la contraseña correspondiente. Activamos la opción La contraseña nunca expira para evitar problemas en las pruebas.

<img width="360" height="335" alt="2026-05-05_10-41" src="https://github.com/user-attachments/assets/0152a79b-567f-44ed-839f-23fb608c2677" />

Del mismo modo, creamos al usuario alumno2 con la misma configuración.

<img width="363" height="340" alt="2026-05-05_10-42" src="https://github.com/user-attachments/assets/64e29183-2879-4811-a24b-d0271db617c7" />

**Pas 8 – Afegir-los a un grup nou anomenat Limitats**

Dentro de lusrmgr.msc, hacemos clic sobre la carpeta Grupos para ver todos los grupos existentes. Clic derecho en un espacio vacío de la lista - Grupo nuevo

<img width="468" height="375" alt="2026-05-05_10-44" src="https://github.com/user-attachments/assets/4f412bc8-a5cd-4d07-bfb6-ca83ccd129a0" />

Introducimos el nombre del grupo Limitados y añadimos los dos usuarios creados (alumno1 y alumno2) como miembros. Hagamos clic en Crear para finalizar.

<img width="359" height="335" alt="2026-05-05_10-44_1" src="https://github.com/user-attachments/assets/d011866c-2c3f-4b50-9ccf-0e1f2b496f14" />

**Pas 9 – Provar la còpia de fitxers a Dades per veure com actuen les quotes**

Finalmente, accederemos al usuario alumno1, e intentaremos crear archivos mayores que el límite que le hemos establecido.

<img width="474" height="318" alt="2026-05-05_10-48" src="https://github.com/user-attachments/assets/bc359f31-97b3-43e4-85f9-51276c590705" />

## **Fase 3 – Script de còpia i automatització**

**Pas 10 – Afegir tercer disc virtual, formatar-lo en NTFS com a Backups**

Añadiremos un 3r disco, y lo cambiaremos a formato NTFS para backups.

<img width="524" height="298" alt="2026-05-05_10-50" src="https://github.com/user-attachments/assets/1c5c08e7-8452-47ae-9e52-33f13b059cd2" />

Crean un nuevo volumen simple dentro del 3er disco.

<img width="318" height="110" alt="2026-05-05_10-50_1" src="https://github.com/user-attachments/assets/e6ec178f-e406-4c93-a26e-5db12cc1e592" />

Formato NTFS, con el nombre Backups.

<img width="442" height="341" alt="2026-05-05_10-52" src="https://github.com/user-attachments/assets/e56497c2-32ab-4153-8adb-30f4e5660c44" />

**Pas 11 – Crear carpeta CòpiesUsuaris dins Backups**

Creamos la carpeta dentro de Backups.

<img width="265" height="268" alt="2026-05-05_10-53" src="https://github.com/user-attachments/assets/6de4ede6-b253-4a9d-8e57-50afb8a2aff3" />

**Pas 12 – Crear un script .bat que copiï C:\Users%USERNAME% a B:\CòpiesUsuaris%USERNAME%**

Explicación del script. @echo off: Silencia la salida de los pedidos en la consola xcopy: Copia archivos y directorios (incluye subdirectorios) %USERNAME%: Variable de entorno que se expande automáticamente con el nombre del usuario activo /E: Copia todos los subdirectorios, incluso los archivos vacíos /I: Si el destino no existe, la creación

<img width="383" height="72" alt="2026-05-05_10-53_1" src="https://github.com/user-attachments/assets/0c5af36c-4c0e-4fae-9cf1-02cdcda697aa" />

**Pas 13 – Obrir gpedit.msc - Configuració d'usuari - Scripts - Inici de sessió**

Ahora, haremos que el sistema ejecute el script automáticamente cuando se inicia sesión.

<img width="351" height="179" alt="2026-05-05_11-59" src="https://github.com/user-attachments/assets/e5192ba8-da1c-4da6-ab4a-169f587ab395" />

<img width="512" height="278" alt="2026-05-05_12-00" src="https://github.com/user-attachments/assets/010b7630-4ad7-4452-ae9e-fcad99a9901d" />

**Pas 14 – Assignar l'script perquè s'executi automàticament en iniciar sessió**

Añadimos la ruta del script a la pestaña Iniciar Sesión.

<img width="550" height="284" alt="2026-05-05_12-01" src="https://github.com/user-attachments/assets/a68c211d-e338-4041-b896-4c25728db976" />

## **Fase 4 – Verificació i documentació**

**Pas 15 – Comprovació: l'script fa la còpia a Backups**

Iniciamos sesión con alumno1 para que se ejecute el script, y comprobamos que las carpetas se han copiado correctamente en Backups.

<img width="703" height="363" alt="2026-05-05_12-05" src="https://github.com/user-attachments/assets/482fcb67-0b91-457b-b080-9f660f7d0a77" />

## **Fase 5 – Gestió de processos i serveis**

**Pas 19 – Llistar processos actius**

Iniciamos sesión como alumno1, abrimos la consola (CMD) y ejecutamos tasklist para obtener la lista de todos los procesos activos, con su PID, sesión y uso de memoria.

<img width="532" height="432" alt="2026-05-05_12-14" src="https://github.com/user-attachments/assets/d40f5789-72b5-402b-9736-6ce83672f61d" />

Redirigimos la salida a un archivo de texto para poder analizarla:

se ha ejecutado correctamente y que el archivo procesos_inici.txt (12.950 bytes) se ha creado en el directorio del usuario alumno1. Hagamos decir para confirmarlo.

<img width="479" height="387" alt="2026-05-05_12-15" src="https://github.com/user-attachments/assets/6ebdd0c8-d7e6-435d-9519-8fe6d00f3520" />

Comprobamos algunos procesos clave usando findstr para filtrar del archivo guardado:

<img width="533" height="163" alt="2026-05-05_12-18" src="https://github.com/user-attachments/assets/eae810a1-87b3-4c8f-83ca-4c83eb029005" />

**Pas 20 – Identificar processos prescindibles**

Filtramos el tasklist para encontrar procesos no esenciales para el usuario en un entorno educativo:

OneDrive.exe se ejecuta en dos instancias (PID 4272 y 1480), consumiendo unos 133 a 135 MB de RAM en total.

<img width="535" height="126" alt="2026-05-05_12-23" src="https://github.com/user-attachments/assets/e0f12047-81c8-4d7f-a387-21bdec18ad5c" />

**Pas 22 – Automatitzar-ho a l'inici de sessió**

Modificamos el script script.bat para incluir los pedidos taskkill que eliminarán automáticamente OneDrive y Teams cada vez que un usuario inicie sesión:

<img width="475" height="127" alt="2026-05-05_12-24" src="https://github.com/user-attachments/assets/ae7a3158-8e2f-46aa-8d9a-8709b3fb3db8" />

Para verificar que funciona, iniciamos sesión como alumno2 y comprobamos que OneDrive no se ejecuta:

<img width="352" height="46" alt="2026-05-05_12-26" src="https://github.com/user-attachments/assets/27ced33b-a29c-4a8d-bec6-ace2b27684a0" />

La consola no devuelve ningún resultado, lo que confirma que OneDrive.exe no se está ejecutando para alumno2 gracias al script de inicio de sesión.

### Paso 23 – Documentación: tasklist, análisis de procesos críticos y rendimiento

#### Archivo de procesos y análisis

El archivo `processos_inici.txt` generado por `tasklist` contiene la lista completa de procesos en el momento de inicio de sesión. Se ha adjuntado a la documentación como evidencia.

#### ¿Qué pasa si matas un proceso crítico como explorer.exe?

`explorer.exe` es el gestor del escritorio y del Explorador de archivos de Windows. Si lo eliminamos:

1. El escritorio desaparece por completo (barra de tareas, iconos, fondo).
2. No podemos abrir ninguna ventana ni acceder a ningún archivo vía GUI.
3. El sistema NO se cuelga: el kernel y los servicios siguen funcionando.
4. Para recuperarlo: `Ctrl + Alt + Supr → Administrador de tareas → Archivo → Ejecutar nueva tarea → explorer.exe`


#### ¿Cómo mejora el rendimiento en VMs?

| Acción | Recursos liberados |
|-------|---------------------|
| Matar OneDrive.exe | ~135 MB RAM, CPU esporádica |
| Matar Teams.exe | ~150-400 MB RAM, CPU y red |
| Deshabilitar SearchIndexer | ~40 MB RAM, I/O disco reducido |
| Total estimado | +300-600 MB RAM disponible |

En máquinas virtuales con 4 GB de RAM, liberar 300+ MB puede significar la diferencia entre un sistema fluido y uno lento.

---

## Fase 6 – Gestión de permisos (ACLs)

### Qué son las ACLs y cómo funcionan en Windows

En Windows, cada archivo y carpeta tiene una **lista de control de acceso (ACL, Access Control List)**. Esta lista define quién puede hacer qué con ese recurso.

Cada entrada de una ACL se llama **ACE (Access Control Entry)** e indica:
- Qué **identidad** (usuario o grupo) está afectada
- Qué **permisos** tiene (lectura, escritura, ejecución, control total, etc.)
- Si el permiso es **Permitir** o **Denegar**

**Permisos disponibles en Windows:**

| Permiso | Descripción |
|--------|------------|
| Control total (F) | Acceso completo: leer, escribir, modificar, eliminar y cambiar permisos |
| Modificar (M) | Leer, escribir y eliminar archivos, pero no cambiar permisos |
| Lectura y ejecución (RX) | Abrir archivos y ejecutar programas |
| Mostrar contenido | Listar el contenido de una carpeta |
| Lectura (R) | Abrir archivos en modo solo lectura |
| Escritura (W) | Crear archivos y subcarpetas |

**Herencia:** Los permisos de una carpeta padre se propagan automáticamente a las subcarpetas y archivos. Cuando se desactiva la herencia, hay que decidir si se conservan o se descartan las entradas heredadas.

---

### Paso 24 – Crear la carpeta Projectes

Iniciamos sesión como **administrador** y creamos la carpeta `Projectes` dentro de la partición Dades (E:). La carpeta se ha creado correctamente en `E:\Projectes`.

<img width="590" height="83" alt="41" src="https://github.com/user-attachments/assets/a91f7c94-4cac-40f8-b026-21b6a6025a56" />


---

### Paso 25 – Asignar permisos normales al grupo Limitats

Hacemos clic derecho sobre `E:\Projectes → Propiedades → Seguridad`. Vemos los permisos actuales (heredados de `E:\`): Usuarios autenticados, SYSTEM, Administradores y Usuarios.

Hacemos clic en **Opciones avanzadas** para acceder a la configuración avanzada de permisos.

<img width="356" height="473" alt="42" src="https://github.com/user-attachments/assets/9eb1233f-199f-44b1-bb32-f09f3450a4c7" />


En la ventana de opciones avanzadas vemos que los permisos están **heredados** desde `E:\` (columna "Heredada de"). Hacemos clic en **Deshabilitar herencia** para romper la herencia y poder gestionar los permisos de forma independiente.

<img width="360" height="479" alt="43" src="https://github.com/user-attachments/assets/1c112d86-72e5-4185-8a0f-b513927e5cbc" />


Eliminamos la entrada de **Usuarios (DESKTOP-6104CQ0\Usuarios)** para limpiar los permisos por defecto que no necesitamos. Seleccionamos la entrada y hacemos clic en **Quitar**.

<img width="729" height="420" alt="44" src="https://github.com/user-attachments/assets/8cd1bd74-100c-487d-b0a4-fe877d4c7a52" />


Ahora añadimos el grupo **Limitats** con **Control total**. Hacemos clic en **Agregar**, introducimos `Limitats`, y marcamos todos los permisos básicos (Control total, Modificar, Lectura y ejecución, Mostrar el contenido de la carpeta, Lectura, Escritura).

El tipo es **Permitir** y se aplica a **Esta carpeta, subcarpetas y archivos** para garantizar la herencia hacia abajo.

<img width="633" height="416" alt="46" src="https://github.com/user-attachments/assets/1245b96c-be6b-43ca-baaf-345d566e61ca" />


La captura de la configuración avanzada final muestra el resultado: la columna **"Heredada de"** ahora dice **"Ninguno"** para todas las entradas, confirmando que la herencia se ha desactivado. El grupo **Limitats (aaron\Limitats)** aparece con **Control total**.

<img width="734" height="359" alt="47" src="https://github.com/user-attachments/assets/83b601df-64aa-475a-a589-33906d4e779c" />


---

### Paso 26 – Comprobar acceso con alumne1

Iniciamos sesión como **alumne1** (miembro del grupo Limitats). Creamos un archivo de texto `hey.txt` en `E:\Projectes` con el contenido "hola".

La captura confirma que alumne1 ha podido crear y escribir el archivo sin ningún problema, tal como se esperaba (tiene **Control total** heredado del grupo Limitats).

<img width="624" height="154" alt="48" src="https://github.com/user-attachments/assets/e667bf1c-cd67-43dd-b530-58b467174697" />

El archivo `hey.txt` se ha creado correctamente en `E:\Projectes` y contiene el texto "hola".

<img width="246" height="109" alt="49" src="https://github.com/user-attachments/assets/9c7c329d-bfad-4df1-ba56-a4f2d126268d" />


---

### Paso 27 – Aplicar excepción para alumne2 (solo lectura)

Volvemos a iniciar sesión como **administrador** y ejecutamos el comando `icacls` para aplicar una excepción específica para `alumne2`:

**Explicación:**
- `/grant:r` → Sustituye (restablece) cualquier permiso existente para ese usuario.
- `alumne2:(R)` → Asigna **solo lectura (R)** al usuario alumne2.

La salida confirma: *"Se procesaron correctamente 1 archivos"*. Ahora `alumne2` tiene **solo lectura**, a pesar de ser miembro del grupo Limitats que tiene Control total (la entrada explícita del usuario tiene **prioridad** sobre la del grupo).

<img width="2488" height="416" alt="51" src="https://github.com/user-attachments/assets/6b494b6d-adf3-4259-bb4e-a83ad360755f" />

---

### Paso 28 – Comprobar la excepción con alumne2

Iniciamos sesión como **alumne2** y accedemos a `E:\Projectes`. La captura muestra que la carpeta aparece **vacía** para alumne2 (no ve el archivo creado por alumne1, o la carpeta ha sido modificada entre capturas).

Cuando alumne2 intenta crear un archivo nuevo o modificar alguno existente, recibe un mensaje de **denegación de acceso**.

<img width="665" height="178" alt="50" src="https://github.com/user-attachments/assets/9f7f04cc-fc57-4b57-a7df-445f858fd88e" />


Volvemos a iniciar sesión como alumne1 y comprobamos que puede leer y ver el archivo `hola.txt` creado en la sesión anterior.

<img width="694" height="150" alt="52" src="https://github.com/user-attachments/assets/1ee87629-4e31-420e-a9ee-d045ccfb6a97" />

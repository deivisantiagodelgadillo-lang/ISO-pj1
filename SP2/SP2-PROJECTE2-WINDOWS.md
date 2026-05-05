**Sprint 2 - Windows: Discs, Quotes, Scripts, Processos i ACLs**

**Fase 1 – Preparació del sistema**

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

**Fase 2 – Quotes i usuaris**

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

**Fase 3 – Script de còpia i automatització**

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

# Instal·lació, Configuració Inicial i Programari de Base

## Fase 1 – Instal·lació del sistema operatiu
- **Pas 1:** Crear màquina virtual amb VirtualBox

<img width="856" height="457" alt="2026-04-14_08-54" src="https://github.com/user-attachments/assets/ffaba0a6-ea16-4a27-8512-bdf53944737a" />

- **Pas 2:** Assignar recursos (RAM mínim 4 GB, disc mínim 40 GB)

<img width="843" height="466" alt="2026-04-14_08-56" src="https://github.com/user-attachments/assets/f718d9d7-0472-4c7c-969e-29b9d511b2e3" />

<img width="724" height="465" alt="2026-04-14_08-57" src="https://github.com/user-attachments/assets/f27ff410-ab02-4a17-9414-10b4f7cb91bf" />


- **Pas 3:** Carregar ISO de Windows 10 o Windows 11

<img width="863" height="325" alt="2026-04-15_01-36" src="https://github.com/user-attachments/assets/c4d1b27b-5171-4bd9-bc53-3fa457c74d1c" />
  
- **Pas 4:** Instal·lar el sistema (idioma, usuari, contrasenya)

<img width="661" height="497" alt="2026-04-14_09-00" src="https://github.com/user-attachments/assets/f9b29f24-29d5-488a-add0-c1375538109b" />

<img width="634" height="424" alt="2026-04-14_09-12" src="https://github.com/user-attachments/assets/d479ec67-64af-4f6c-bd98-f910fbbb90c3" />

<img width="777" height="433" alt="2026-04-14_09-12_1" src="https://github.com/user-attachments/assets/ac272910-d52b-45e6-bc9c-c975f49df09d" />
  
- **Pas 5:** Comprovar que arrenca correctament

<img width="427" height="413" alt="2026-04-15_01-38" src="https://github.com/user-attachments/assets/9b2d90ed-4e01-4a2a-9fe5-ef407fa36513" />

## Fase 2 – Punts de restauració
- **Pas 6:** Cercar "Crear un punt de restauració"

<img width="736" height="251" alt="2026-04-14_23-52" src="https://github.com/user-attachments/assets/eeaf7dd4-b556-402f-acec-b2407dd2e2ea" />

- **Pas 7:** Activar protecció del sistema al disc C:

<img width="437" height="501" alt="2026-04-14_23-53" src="https://github.com/user-attachments/assets/ff92de93-eed6-4810-91fc-47ee389267b1" />

<img width="425" height="468" alt="2026-04-14_23-53_1" src="https://github.com/user-attachments/assets/a1d5ef6d-b95c-4b21-b3a3-f746dcf5a064" />

- **Pas 8:** Crear un punt manual

<img width="407" height="483" alt="2026-04-14_23-54" src="https://github.com/user-attachments/assets/03e3b282-327a-486e-aa2c-18618ee63523" />

<img width="416" height="486" alt="2026-04-14_23-55" src="https://github.com/user-attachments/assets/1ea26893-abcc-46c9-af71-4f617f78664c" />

<img width="373" height="169" alt="2026-04-14_23-56" src="https://github.com/user-attachments/assets/6e347e78-adfb-49d6-9182-85a8ebcdd92c" />

- **Pas 9:** Fer un canvi (instal·lar app o configuració)

<img width="423" height="153" alt="2026-04-14_23-59" src="https://github.com/user-attachments/assets/1fb40cf1-c705-415d-8dad-8c6001e3e6f8" />

<img width="294" height="332" alt="2026-04-14_23-59_1" src="https://github.com/user-attachments/assets/b052d5cb-0313-41c3-a376-f4717897bf80" />

- **Pas 10:** Restaurar i comprovar

<img width="399" height="478" alt="2026-04-15_00-01" src="https://github.com/user-attachments/assets/81d42545-dc48-4bae-8ff6-f218c60d609b" />

<img width="620" height="494" alt="2026-04-15_00-01_1" src="https://github.com/user-attachments/assets/fe0f552b-3ac3-4418-9b66-c82d302f0daa" />

<img width="560" height="456" alt="2026-04-15_00-01_2" src="https://github.com/user-attachments/assets/1d72e449-a07b-4db7-b8fa-66af12e2a743" />

<img width="567" height="271" alt="2026-04-15_00-02" src="https://github.com/user-attachments/assets/634645e6-7f79-4ff0-aa28-d14da1e72f65" />

<img width="720" height="464" alt="2026-04-15_00-05" src="https://github.com/user-attachments/assets/8bc37c0d-8ac2-4c36-9805-f21c61cb89cd" />

## Fase 3 – Llicències de Windows
- **Pas 11:** Obrir Configuració → Sistema → Activació

<img width="305" height="706" alt="2026-04-15_00-08" src="https://github.com/user-attachments/assets/f20b67a3-bb36-451c-846a-6bb5c986c0e7" />

- **Pas 12:** Veure si Windows està activat

<img width="784" height="699" alt="2026-04-15_00-08_1" src="https://github.com/user-attachments/assets/433b69ce-7124-4323-90c9-cc495f321929" />

- **Pas 13:** Executar al cmd: `slmgr /xpr`

<img width="683" height="361" alt="2026-04-15_00-09" src="https://github.com/user-attachments/assets/9dc3f170-8598-4d12-be97-05bb363e7880" />

- **Pas 14:** Esbrinar llicenciament Windows i explicar breument

Aquí tienes la traducción al castellano, manteniendo el formato para que sea fácil de consultar:

### Tipos de Licencias de Software

* **Retail (FPP):** Licencia comercial que se compra por separado. Pertenece al **usuario** y no al ordenador.
* **OEM:** Instalada por defecto en equipos nuevos. Se vincula de manera **permanente** a la placa base de ese PC.
* **Volumen:** Diseñada para empresas e instituciones. Permite activar **múltiples dispositivos** a la vez.
* **Digital:** Licencia vinculada al hardware y a la cuenta de Microsoft; es el sustituto de la clave de producto tradicional.
* **Suscripción:** Pago indefinido (mensual o anual, como Windows 365), utilizada principalmente en la **nube**.

- **Pas 15:** Consultar preu aproximat d'una llicència Windows (web oficial o botigues)

> **Precios oficiales de Microsoft (abril 2026):**
>
> | Edición | Precio aprox. (web oficial) |
> |---|---|
> | Windows 11 Home | ~145 € |
> | Windows 11 Pro | ~259 € |
> | Windows 11 Pro for Workstations | ~439 € |
>****

## Fase 4 – Gestor d'arrencada
- **Pas 16:** Obrir Command Prompt com administrador

<img width="738" height="371" alt="2026-04-15_00-10" src="https://github.com/user-attachments/assets/be079ce0-b218-46ec-8dee-fd71c9c84cdb" />

- **Pas 17:** Executar `bcdedit`

<img width="538" height="554" alt="2026-04-15_00-11" src="https://github.com/user-attachments/assets/7b9c8974-b902-4487-a9e5-752b89ee04cf" />

- **Pas 18:** Identificar els blocs:
  - Administrador de arranque de Windows (Boot Manager)
 
<img width="513" height="202" alt="2026-04-15_00-12" src="https://github.com/user-attachments/assets/4a870afa-d39d-468d-abf0-340818397352" />


  - Cargador de arranque de Windows (Boot Loader)

<img width="524" height="281" alt="2026-04-15_00-13" src="https://github.com/user-attachments/assets/479b89f9-593b-48aa-a5d6-fb6346783db8" />


- **Pas 19:** Interpretar dades concretes
* **Boot Manager**
    * **default: {current}** -> El sistema que se elige por defecto para arrancar.
    * **timeout: 30** -> Los segundos que tarda antes de arrancar automáticamente.

* **Boot Loader**
    * **device: partition=C:** -> Partición del disco donde está instalado el sistema operativo (Windows).
    * **path: \WINDOWS\system32\winload.efi** -> Archivo que carga el sistema.
    * **description: Windows 11** -> Nombre del sistema operativo.

- **Pas 20:** Respondre preguntes curtes:
  * **¿Qué sistema se está arrancando?** Se arranca Windows 10 (se ve en el parámetro `description` del Cargador de arranque).
* **¿En qué disco o partición está instalado?** Se encuentra en la partición C: (se ve en el parámetro `device` del Cargador de arranque).
* **¿Cuánto tiempo espera antes de arrancar?** Espera 30 segundos (se ve en el parámetro `timeout` del Administrador de arranque).
* **¿Qué archivo inicia Windows?** Lo inicia el archivo `\WINDOWS\system32\winload.efi` (se ve en el parámetro `path` del Cargador de arranque).

- **Pas 21:** Interpretació final. 
* **Quién decide el arranque (Boot Manager):** El Windows Boot Manager (`bootmgr`) es el responsable de mostrar el menú de arranque y decidir qué sistema operativo se iniciará, en función de la configuración del BCD.

* **Quién carga el sistema (Boot Loader):** El Windows Boot Loader (`winload.efi`) es el archivo que realmente carga el núcleo de Windows en la memoria e inicia el sistema operativo una vez que el Boot Manager ha tomado la decisión.

## Fase 5 – Xarxa bàsica
- **Pas 22:** Obrir configuració de xarxa

<img width="752" height="623" alt="2026-04-15_00-19" src="https://github.com/user-attachments/assets/ead5e26a-f4b1-40fb-b0ab-0bee50393553" />

- **Pas 23:** Consultar IP amb: `ipconfig`

<img width="551" height="236" alt="2026-04-15_00-20" src="https://github.com/user-attachments/assets/42d1e0e9-c600-4543-b609-b7b2576da1b9" />

- **Pas 24:** Configurar IP dinàmica (DHCP automàtic)

<img width="605" height="496" alt="2026-04-15_00-21" src="https://github.com/user-attachments/assets/fcfa90b6-2a00-4ffc-b0eb-7e8f546fe39c" />

- **Pas 25:** Configurar IP fixa (manual: IP, màscara, gateway, DNS)

<img width="363" height="713" alt="2026-04-15_00-25" src="https://github.com/user-attachments/assets/b05a8eda-7823-4158-b63e-cdab64df87a2" />

<img width="321" height="216" alt="2026-04-15_00-26" src="https://github.com/user-attachments/assets/121cc21c-59b8-47c8-b8e6-d356855bc941" />

- **Pas 26:** Comprovar connexió amb: `ping google.com`

<img width="541" height="228" alt="2026-04-15_00-28" src="https://github.com/user-attachments/assets/25173454-f8f9-4656-a505-e8dcd6f58df7" />

## Fase 6 – Comandes generals
- **Pas 27:** Obrir PowerShell

<img width="355" height="219" alt="2026-04-15_00-30" src="https://github.com/user-attachments/assets/dea42be5-bca6-49b0-82cb-8f172037fee9" />

- **Pas 28:** Diferenciar cmd i PowerShell:
### Detalles del arranque

* **BCD (Boot Configuration Data):** Es el archivo de donde el **Boot Manager** lee la configuración de arranque.
* **Kernel:** El **Boot Loader** (`winload.efi`) es quien toma el núcleo de Windows (`ntoskrnl.exe`) y los controladores básicos y los carga en la memoria RAM.

---

### Diferencias clave: cmd vs. PowerShell

| Característica | cmd (Símbolo del sistema) | Windows PowerShell |
| :--- | :--- | :--- |
| **Datos** | Trabaja con texto plano. | Trabaja con **objetos** (.NET). |
| **Comandos** | Básicos y heredados de DOS (`dir`, `ping`). | Utiliza **Cmdlets** con formato `Verbo-Nombre` (`Get-Process`). |
| **Uso principal** | Comprobaciones rápidas de red o sistema. | Automatización de tareas y scripts para administradores. |

- **Pas 29:** Comandes bàsiques (provar-les):
  - `dir`: veure fitxers
 
<img width="634" height="452" alt="2026-04-15_00-34" src="https://github.com/user-attachments/assets/e424c182-738f-4a92-bbf9-66e8c6886b72" />

  - `cd`: moure's per carpetes

<img width="450" height="99" alt="2026-04-15_00-38" src="https://github.com/user-attachments/assets/f10b3800-8d33-4cfc-971f-99d4d97c7172" />

  - `mkdir prova`: crear carpeta

<img width="327" height="56" alt="2026-04-15_00-39" src="https://github.com/user-attachments/assets/f169cf6b-2fa8-4a30-bd2c-dbebe8de9204" />

  - `echo hola > fitxer.txt`: crear fitxer

<img width="412" height="59" alt="2026-04-15_00-40" src="https://github.com/user-attachments/assets/2d3da937-5e61-4e2b-9fa2-fa47e5be614b" />

  - `del fitxer.txt`: eliminar fitxer

<img width="363" height="59" alt="2026-04-15_00-41" src="https://github.com/user-attachments/assets/57395635-4b83-4af2-b070-e486f4c70b09" />

- **Pas 30:** Comandes útils del sistema:
  - `tasklist`: veure processos actius
 
<img width="615" height="457" alt="2026-04-15_00-42" src="https://github.com/user-attachments/assets/928232dd-891a-4512-ab75-305d8255979b" />

  - `taskkill /IM notepad.exe /F`: tancar un procés

<img width="490" height="119" alt="2026-04-15_00-43" src="https://github.com/user-attachments/assets/73be46bc-e99c-4eed-a619-c1949f3b38c0" />

  - `systeminfo`: informació completa del sistema

<img width="867" height="662" alt="2026-04-15_00-44" src="https://github.com/user-attachments/assets/36d22ed1-4106-4d4e-bbd2-febc85b90efa" />

  - `hostname`: nom de l'equip

<img width="283" height="118" alt="2026-04-15_00-44_1" src="https://github.com/user-attachments/assets/2ca52e46-9c8f-4cd2-ac76-128c47297be7" />

  - `whoami`: usuari actual

<img width="270" height="76" alt="2026-04-15_00-44_2" src="https://github.com/user-attachments/assets/0f2ad154-7137-4913-8d43-5de029d3b879" />

- **Pas 31:** Comandes de xarxa:
  - `ipconfig`: veure configuració IP

 <img width="545" height="236" alt="2026-04-15_00-45" src="https://github.com/user-attachments/assets/564c1fe9-efc0-4cb6-8a44-64c2d9b98375" />

  - `ping google.com`: comprovar connexió

<img width="533" height="248" alt="2026-04-15_00-46" src="https://github.com/user-attachments/assets/89eb0bf6-a575-4ee7-84cb-9b914b62b733" />

  - `netstat -an`: connexions obertes

<img width="475" height="624" alt="2026-04-15_00-51" src="https://github.com/user-attachments/assets/253d32c8-ec60-4870-9969-dd8dddaf9a06" />

- **Pas 32:** Comandes interessants (una mica més avançades):
  - `tree`: veure estructura de carpetes
 
<img width="309" height="111" alt="2026-04-15_00-51_1" src="https://github.com/user-attachments/assets/7dfb9cf6-ec9d-4947-94c4-bfdd7e656b8e" />

  - `cls`: netejar pantalla

<img width="320" height="134" alt="2026-04-15_00-52" src="https://github.com/user-attachments/assets/d5004b00-7160-464a-a274-a37eb810e17d" />

<img width="222" height="67" alt="2026-04-15_00-52_1" src="https://github.com/user-attachments/assets/c760c380-ffa3-4b19-9f9d-fc2f941578f7" />

  - `help`: veure ajuda

<img width="647" height="621" alt="2026-04-15_00-53" src="https://github.com/user-attachments/assets/e4c77253-e487-4e42-9939-23416c987453" />

  - `shutdown /s /t 0`: apagar l'equip

<img width="834" height="447" alt="2026-04-15_00-54" src="https://github.com/user-attachments/assets/bbf2f28b-ae32-4a40-aea4-2c211d95b2ef" />

- **Pas 33:** Mini interpretació:

* **tasklist**
    * **tasklist:** Muestra una lista de todos los procesos y programas que se están ejecutando actualmente en el sistema.

* **ipconfig**
    * **ipconfig:** Muestra la configuración básica de red del equipo (dirección IP, máscara de subred, puerta de enlace, etc.).

* **systeminfo**
    * **systeminfo:** Muestra información detallada del hardware y del sistema operativo (versión de Windows, memoria RAM, procesador, tiempo de actividad, etc.).

## Fase 7 – Instal·lació d'aplicacions
- **Pas 34:** Descarregar un programa des del navegador (ex: Chrome o VS Code)

<img width="737" height="160" alt="2026-04-15_01-12" src="https://github.com/user-attachments/assets/6cbb619d-b585-4261-8e27-6b522dedb29b" />


- **Pas 35:** Instal·lar-lo seguint l'assistent

<img width="621" height="233" alt="2026-04-15_01-12_1" src="https://github.com/user-attachments/assets/3cb569eb-3579-43f8-afe9-f6ad6ce3a434" />

- **Pas 36:** Obrir-lo i comprovar que funciona

<img width="694" height="456" alt="2026-04-15_01-12_2" src="https://github.com/user-attachments/assets/82275e5d-3fc8-4418-b12a-deb9ffeb8a3a" />

- **Pas 37:** Instal·lar una aplicació des de Microsoft Store

<img width="511" height="386" alt="2026-04-15_01-14" src="https://github.com/user-attachments/assets/39834a0f-3615-45ae-9b34-f35c14ab29c7" />

- **Pas 38:** Obrir-la i comprovar funcionament

<img width="503" height="403" alt="2026-04-15_01-16" src="https://github.com/user-attachments/assets/38e28e04-8619-46fc-8ae7-754527d8fdaa" />

<img width="797" height="456" alt="2026-04-15_01-16_1" src="https://github.com/user-attachments/assets/407e3c3f-8f38-4429-86a9-bdfefffd163c" />

- **Pas 39:** Desinstal·lar una aplicació: `Configuració → Aplicacions → Desinstal·lar`

<img width="797" height="326" alt="2026-04-15_01-18_1" src="https://github.com/user-attachments/assets/22dd724b-756a-429f-baec-6df71743bc54" />

- **Pas 40:** Verificació: Comprovar que el programa ja no apareix al sistema

<img width="771" height="588" alt="2026-04-15_01-19" src="https://github.com/user-attachments/assets/9a1fa2ed-ca27-491c-9e09-43a2d1430f23" />

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
- **Pas 17:** Executar `bcdedit`
- **Pas 18:** Identificar els blocs:
  - Administrador de arranque de Windows (Boot Manager)
  - Cargador de arranque de Windows (Boot Loader)
- **Pas 19:** Interpretar dades concretes
- **Pas 20:** Respondre preguntes curtes:
  - Quin sistema s'està arrencant?
  - A quin disc o partició està instal·lat?
  - Quant temps espera abans d'arrencar?
  - Quin fitxer inicia Windows?
- **Pas 21:** Interpretació final. *Explicar amb una frase:*
  - Qui decideix l'arrencada (Boot Manager)
  - Qui carrega el sistema (Boot Loader)

## Fase 5 – Xarxa bàsica
- **Pas 22:** Obrir configuració de xarxa
- **Pas 23:** Consultar IP amb: `ipconfig`
- **Pas 24:** Configurar IP dinàmica (DHCP automàtic)
- **Pas 25:** Configurar IP fixa (manual: IP, màscara, gateway, DNS)
- **Pas 26:** Comprovar connexió amb: `ping google.com`

## Fase 6 – Comandes generals
- **Pas 27:** Obrir PowerShell
- **Pas 28:** Diferenciar cmd i PowerShell:
  - `cmd`: comandes bàsiques i clàssiques
  - `PowerShell`: més potent, permet treballar amb objectes i automatitzar tasques
- **Pas 29:** Comandes bàsiques (provar-les):
  - `dir`: veure fitxers
  - `cd`: moure's per carpetes
  - `mkdir prova`: crear carpeta
  - `echo hola > fitxer.txt`: crear fitxer
  - `del fitxer.txt`: eliminar fitxer
- **Pas 30:** Comandes útils del sistema:
  - `tasklist`: veure processos actius
  - `taskkill /IM notepad.exe /F`: tancar un procés
  - `systeminfo`: informació completa del sistema
  - `hostname`: nom de l'equip
  - `whoami`: usuari actual
- **Pas 31:** Comandes de xarxa:
  - `ipconfig`: veure configuració IP
  - `ping google.com`: comprovar connexió
  - `netstat -an`: connexions obertes
- **Pas 32:** Comandes interessants (una mica més avançades):
  - `tree`: veure estructura de carpetes
  - `cls`: netejar pantalla
  - `help`: veure ajuda
  - `shutdown /s /t 0`: apagar l'equip
- **Pas 33:** Mini interpretació:
  - Indicar què mostra `tasklist`
  - Indicar què mostra `ipconfig`
  - Indicar què mostra `systeminfo`

## Fase 7 – Instal·lació d'aplicacions
- **Pas 34:** Descarregar un programa des del navegador (ex: Chrome o VS Code)
- **Pas 35:** Instal·lar-lo seguint l'assistent
- **Pas 36:** Obrir-lo i comprovar que funciona
- **Pas 37:** Instal·lar una aplicació des de Microsoft Store
- **Pas 38:** Obrir-la i comprovar funcionament
- **Pas 39:** Desinstal·lar una aplicació: `Configuració → Aplicacions → Desinstal·lar`
- **Pas 40:** Verificació: Comprovar que el programa ja no apareix al sistema

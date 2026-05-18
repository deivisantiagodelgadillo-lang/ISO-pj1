# Sprint 4: Configuració del Programari de Base i Sistemes d’Emmagatzematge en Windows

---

## 1. Introducció
Els RAIDs (Redundant Array of Independent Disks) són sistemes que permeten combinar diversos discos discos físics en una sola unitat lògica per aconseguir millores en rendiment, capacitat o seguretat. Aquests sistemes poden ser gestionats tant per maquinari (controladores RAID) com per programari, sent aquest últim el cas dels sistemes operatius moderns com Windows Server. Cada nivell de RAID ofereix característiques diferents segons si l'objectiu és millorar la velocitat, oferir redundància o combinar ambdues coses.

El RAID 5 és un dels nivells més utilitzats en entorns professionals perquè aconsegueix un equilibri òptim entre rendiment, capacitat i tolerància a fallades. Aquest sistema distribueix tant les dades com la informació de paritat entre tots els discos de la matriu. La paritat té la funció de reconstruir la informació en cas que un dels discos falli, permetent que el sistema segueixi funcionant i garantint la disponibilitat en entorns crítics com els servidors. Per a la seva configuració es requereix un mínim de tres discos durs, i la capacitat útil total és la suma de tots els discos menys un, ja que l'espai equivalent a una unitat es dedica a la paritat.

---

## 2. Desenvolupament de la Pràctica Pas a Pas

### Pas 1: Preparació de la màquina virtual
Abans d'iniciar el sistema operatiu, cal configurar el maquinari virtual necessari per implementar la matriu de discos:
* A la màquina virtual com Windows Server 2022, s'afegeixen un mínim de 3 discos addicionals de la mateixa mida (per exemple, 10 GB cadascun).
* Una vegada connectats els suports d'emmagatzematge, s'inicia la màquina virtual.

<img width="883" height="534" alt="image" src="https://github.com/user-attachments/assets/9a6f4a93-cb97-4821-96fc-bc89c4b8bcb4" />

### Pas 2: Inicialització i configuració dels discs
Un cop arrencat el sistema, s'obre l'eina de **Gestió de discs** mitjançant l'execució de la comanda `diskmgmt.msc`.

<img width="406" height="220" alt="image" src="https://github.com/user-attachments/assets/d3963112-f13f-4245-829a-11fa119e0572" />

Quan es mostri l'assistent automàtic, s'inicialitzen els nous discos triant l'estil de partició MBR o GPT (es recomana GPT si la mida és superior a 2TB, tot i que en aquest cas no afecta).
   
<img width="450" height="322" alt="image" src="https://github.com/user-attachments/assets/ed1d5ba7-d606-4e69-9b12-8b6de6ae1e3a" />

Es mantenen els discos en l'estat inicial, sans formatar-los ni crear-hi cap tipus de partició.

<img width="1207" height="358" alt="image" src="https://github.com/user-attachments/assets/5d30d5ba-215f-4b4b-b787-88642399d258" />


### Pas 3: Creació del volum RAID 5 des del Gestor de discs
Es fa clic amb el botó dret del ratolí sobre un dels nous discos buits i es selecciona l'opció **"New RAID-5 Volume"**.
   
<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/1a1cd729-2ea0-4a2f-a72a-cc52646b845d" />

Dips de l'assistent, s'afegeixen els altres 2 discos restants a la configuració per formar la matriu.
   
<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/b5fd1d0b-ef73-4f31-9e82-56572ca31f34" />

S'assigna una lletra d'unitat al volum.

<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/454ceb04-4ffe-4f97-ad48-d9b19b38e21f" />

Es formata el volum utilitzant el sistema de fitxers **NTFS** i s'estableix l'etiqueta de volum: **RAID5-Test**.
   
<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/89e07d9e-e83e-4519-b3cf-be78cf8c1b30" />

S'espera que finalitzi el procés de format i es verifica que es mostra com a un volum únic al sistema (amb una capacitat útil de 20 GB, corresponent a la suma dels discos menys l'espai de paritat).

<img width="1277" height="369" alt="image" src="https://github.com/user-attachments/assets/ac50d18c-6ecb-4074-afc5-783f2f7e0399" />


### Pas 4: Proves de funcionalitat i accés
S'obre l'Explorador de fitxers de Windows i es desplaça fins al volum `E:\`.
  <img width="795" height="595" alt="image" src="https://github.com/user-attachments/assets/faae2fbf-6485-4472-8955-7943027a57bd" />

Es copien arxius de prova a l'arrel de la unitat.
<img width="795" height="595" alt="image" src="https://github.com/user-attachments/assets/b70ab182-f29a-4ac6-885a-2a6c8f3551e7" />

S'obren i es comprova que els fitxers són completament accessibles i es llegeixen sense problemes.
<img width="795" height="595" alt="image" src="https://github.com/user-attachments/assets/3a515157-47d2-47c8-b6d0-5f356caff1c1" />


### Pas 5: Simulació de primera fallada (Un disc Offline)
Es torna a accedir a l'eina **Disk Management**, Es fa clic dret sobre un dels tres discos que configuren el RAID i es selecciona l'opció **Offline** per simular una fallada crítica de la unitat.

<img width="795" height="236" alt="image" src="https://github.com/user-attachments/assets/f95935b1-3386-4322-b24a-0688d81c6d5f" />

<img width="1006" height="322" alt="image" src="https://github.com/user-attachments/assets/f6362fcb-9677-4f03-ba22-16b8c2c9c3d5" />

  
S'oberva el cosmportament del sistema: Windows Server mostrarà un advertiment indicant que el volum es troba en estat degradat, però que segueix estant accessiblem es torna a comprovar que es poden obrir els fitxers de forma normal gràcies a la reconstrucció en temps real per paritat.

<img width="831" height="524" alt="image" src="https://github.com/user-attachments/assets/1a152e65-87fc-4be8-8481-30ffdaa04b4e" />

### Pas 6: Simulació de segona fallada (Dos discs Offline)
Es procedeix a forçar una segona fallada col·locant un **segon disc en estat Offline**.
   
<img width="1083" height="144" alt="image" src="https://github.com/user-attachments/assets/285513c5-c75c-488c-a35c-4cfda1ea0434" />

<img width="1298" height="324" alt="image" src="https://github.com/user-attachments/assets/c9fb5c2b-32e8-4d98-89db-60e81fda79d0" />

Atès que el RAID 5 només té tolerància per suportar la fallada d'un sol disc de forma simultània, el volum sencer deixarà de funcionar immediatament. S'intenta accedir de nou a la unitat `E:\` i es comprova que l'accés als arxius queda totalment bloquejat.

<img width="175" height="47" alt="image" src="https://github.com/user-attachments/assets/cbc1c568-6ba3-4a4f-9cc2-d4da0aa8a3af" />



### Pas 7: Recuperació del sistema
Es fa clic dret sobre un dels discos desconnectats prèviament i es torna a posar en estat **Online**.

<img width="294" height="175" alt="image" src="https://github.com/user-attachments/assets/0b167ac8-48c3-47a8-9169-3b704a979bbe" />



El volum inicia de forma automàtica la seva recuperació o entra en un procés actiu de reconstrucció de les dades, es torna a intentar l'accés als arxius de la unitat i es comprova que la integritat de les dades s'ha mantingut.

<img width="696" height="181" alt="image" src="https://github.com/user-attachments/assets/e17336f3-b64e-4d0c-b02a-5bee0c4f2e48" />


---

## 3. Conclusions i Observacions
* **Distribució de paritat:** S'ha comprovat com el RAID 5 distribueix de manera eficient la paritat i les dades entre tots els components de la matriu.
* **Tolerància limitada:** El sistema ofereix redundància i tolera correctament la fallada d'un sol disc dur, mantenint els serveis operatius en entorns de producció.
* **Penalització d'escriptura:** Atès que la paritat es calcula i s'escriu automàticament cada vegada que es graven dades, s'ha de tenir en compte que hi ha una petita penalització en el rendiment d'escriptura, encara que la lectura és molt eficient.
* **No és un backup:** Tot i la seva resistència davant de la pèrdua d'una unitat, **el RAID 5 no substitueix una còpia de seguretat**. Si dues unitats fallen simultàniament o es produeix corrupció de dades, es perdran tots els fitxers de forma irreversible. A més, el procés de reconstrucció pot ser llarg i estressant per a la resta de discos de la matriu.
* **Recomanació:** No és adequat per a entorns on la màxima disponibilitat o protecció total sigui crítica; en aquests casos és obligatori combinar-lo amb sistemes de backup externs o avaluar alternatives com RAID 6 o RAID 10.

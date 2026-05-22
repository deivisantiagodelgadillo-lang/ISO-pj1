# Sprint 3: Administració de Dominis i Seguretat 

## Configuració del servidor

Primer, obrim un terminal dintre de la màquina servidor, executem la comanda **ip a**, ens apuntem l'adreça IP que rebem per dhcp, i la posarem de manera estàtica amb interficie gràfica. Quan configurem un servidor **sempre hem de posar l'adreça IP estatica**, ja que una adreça dinàmica complicaría l'accés als serveis que ofereix, degut a que cada dia en tindria una de diferent.

<img width="746" height="459" alt="Captura de pantalla de 2026-01-08 13-24-13" src="https://github.com/user-attachments/assets/9a3ec543-8a7e-4345-83bc-fcec314ada22" />

<img width="786" height="302" alt="2026-05-22_00-06" src="https://github.com/user-attachments/assets/13b72184-44a5-4d15-85a7-3718c254e04d" />

Tot seguit, accedim a **/etc/hostname** amb la comanda **nano**, on **modificarem el nom del dispositiu**.

<img width="504" height="48" alt="2026-05-22_00-06_1" src="https://github.com/user-attachments/assets/da0225d1-026a-4372-b06b-7cbba1cb6fb2" />

El mateix al **/etc/hosts** i posarem el nou hostname a l'adreça de loopback del dispositiu. També posarem el domini que crearem pròximament lligat a l'adreça IP que ens hem configurat estàticament.

<img width="492" height="89" alt="2026-05-22_00-07" src="https://github.com/user-attachments/assets/b3d5d3c2-f494-4d84-8993-b05b50de3d4f" />

A continuació, instal·lem els serveis per a instal·lar i gestionar ldap.

<img width="780" height="153" alt="image" src="https://github.com/user-attachments/assets/0a30a644-0d52-45bd-9e02-394bf293a2af" />

Durant l'instal·lació, ens demanara una contrasenya per a l'usuari d'administrador de ldap, mes avant haurem de recordar.

<img width="652" height="300" alt="image" src="https://github.com/user-attachments/assets/d6da4609-d432-471d-976f-dba29410869d" />

En la comanda **slapcat** per a veure tots els elements del domini.

<img width="761" height="483" alt="image" src="https://github.com/user-attachments/assets/52c97ac2-bc84-4031-98ef-72cc74827359" />

Ara anem a **Descargas**, i descomprimim el zip que ens descarregat del moodle.

<img width="773" height="305" alt="image" src="https://github.com/user-attachments/assets/c32eaa7f-ce22-4652-abd4-bfb65a94d6de" />

Amb **dpkg-reconfigure slapd**, podem configurar i afegir elements al domini més facilment. Alternativament, podem fer servir els fitxers de configuració **.ldif** que hem descomprimit, però aquests no són tan practics.

<img width="561" height="18" alt="image" src="https://github.com/user-attachments/assets/66131f3e-973c-4abc-b772-652b85e35fbf" />

Posem al domini que hem indicat previament al **/etch/hosts**.

<img width="768" height="359" alt="image" src="https://github.com/user-attachments/assets/dc385436-be5b-44cc-bc78-febcfc178e27" />

El nom de l'organitazció.

<img width="751" height="369" alt="image" src="https://github.com/user-attachments/assets/4596e391-d4b5-432e-80f1-e7a0af226daa" />

Una contrasenya, podem ficar la mateia que abans.

<img width="556" height="233" alt="image" src="https://github.com/user-attachments/assets/98401836-90b1-4ee4-bfbd-2e046ebc89a3" />

Eliminarem la base de dades en purgar.

<img width="555" height="230" alt="image" src="https://github.com/user-attachments/assets/1a6004dd-9342-42a4-a2b4-91a72385e54d" />

Finalment, movem la base de ades antiga, i executem la comanda **slapcat** per a comprovar que tots els canvis que acabem de configurar s'han aplicat correctament.

<img width="556" height="242" alt="image" src="https://github.com/user-attachments/assets/a3bb3730-8c0e-4997-9f84-df402069fb57" />


De moment no tenim elements (usuaris, grups, unitats organitzatives) però el domini ja apareix configurat correctament.

<img width="763" height="462" alt="image" src="https://github.com/user-attachments/assets/d983ffbd-7436-4457-988c-d3cf294bbb2a" />

Ara crearem una unitat organitzativa mitjançant un fitxer, **uo.ldif** que ens hem descarregat, l'editarem per a que s'adapte als nostres parametres, que seria canviar **dc=nick,dc=cat**, que vindria a ser el nostre domini.

<img width="753" height="210" alt="image" src="https://github.com/user-attachments/assets/5c509ca5-47f8-44af-9be0-afd34aa8535c" />

Per executar-lo utilitzarem aquesta comanda, que serveix per afegir contingut al servidor LDAP llegint-lo des d'un fitxer.

**ldapadd:** És l'ordre principal per afegir entrades a la base de dades LDAP.

**-c (continue):** Si troba un error (per exemple, si una entrada ja existeix), no s'atura; continua afegint la resta de coses del fitxer.

**-x:** Utilitza autenticació simple (amb contrasenya normal), en lloc de xifrats complexos.

**-D "cn=admin...":** És l'usuari amb qui t'identifiques per fer els canvis (el login). Aquí estàs entrant com a admin del domini nick.cat.

**-W:** Et demana la contrasenya després de prémer Intro (per seguretat, perquè no quedi guardada a l'historial de comandes).

**-f uo.ldif:** Indica el fitxer d'on ha de llegir les dades que vols afegir (en aquest cas, el fitxer uo.ldif).

<img width="791" height="84" alt="image" src="https://github.com/user-attachments/assets/26a7f477-70b4-4d4e-9e5f-c4c2a0dfe603" />

Ara tocaria per a crear un usuari amb el fitxer **usu.ldif**, igual canviarem els parametres adaptant-ho als nostres. 

<img width="758" height="627" alt="image" src="https://github.com/user-attachments/assets/5b40df47-b756-4f20-957f-77f107f9b5a5" />

Seguidament executariem la mateixa comanda per afegir-ho, nomes canviant el nom del fitxer.

<img width="792" height="86" alt="image" src="https://github.com/user-attachments/assets/bbad47fe-e51e-4f19-91fe-34e182fdd7af" />

Tocaria per a l'ultim que es el fitxer de **grup.ldif** que canviariem el mateix que als altres dos fitxers.

<img width="742" height="267" alt="image" src="https://github.com/user-attachments/assets/3feae02a-b3a1-40dc-ab23-5cb826988e64" />

I mateixa comanda canviant el nom del fitxer.

<img width="620" height="69" alt="image" src="https://github.com/user-attachments/assets/bfe280e5-25bb-4b3f-95ec-e5ec60cd8e3a" />

Mitjançant la comanda de **slapcat**, podriem confirmar que se'ns ha creat.

<img width="610" height="677" alt="image" src="https://github.com/user-attachments/assets/7f81a643-f6e5-4682-b943-5a8dcf975fe0" />

<img width="591" height="765" alt="image" src="https://github.com/user-attachments/assets/30f562c8-9ee4-41bd-b38b-ddc7286177ad" />

<img width="712" height="425" alt="image" src="https://github.com/user-attachments/assets/c564ae41-957d-46fc-bc0a-7eb09797140f" />


## Configuració del client

Ara seria el torn per al client, previament hauriem fet la compravacio que tenen connexio entre els dos. Despres descarregarem els paquets necessaris.

<img width="381" height="17" alt="image" src="https://github.com/user-attachments/assets/c99a90b0-a451-4c43-bc05-e6adcd858913" />

En la instal·lació, apareixera l'assistent que ens demanara l'adreça IP del domini.

<img width="689" height="308" alt="image" src="https://github.com/user-attachments/assets/985a1e76-9238-436c-a9ba-cd8d3a00294c" />

Posarem tambe el nom.

<img width="717" height="319" alt="image" src="https://github.com/user-attachments/assets/ea6372da-ba7e-471a-866f-1f513924010e" />

Elegirem la versió de LDAP 3.

<img width="696" height="327" alt="image" src="https://github.com/user-attachments/assets/d97b2edf-d168-4024-8a9a-17e1397a3087" />

Si a les seguents dos opcions.

<img width="690" height="390" alt="image" src="https://github.com/user-attachments/assets/43838a43-c1ec-45f0-ac20-c61bb25ced4a" />

<img width="698" height="360" alt="image" src="https://github.com/user-attachments/assets/e1a2ceeb-1e97-49a3-8ecb-d72cbf28c769" />

Posarem l'usuari d'adminsitrador.

<img width="708" height="422" alt="image" src="https://github.com/user-attachments/assets/fd0afbf9-945b-479d-a96b-9e64e57d4214" />

La seva contrasenya.

<img width="692" height="339" alt="image" src="https://github.com/user-attachments/assets/403daf51-35ff-4c90-8607-183a33cce760" />

I ja ho tindriem, pero en cas que en algun punt ens haguessim equivocat, podem tornar a configurar-ho amb aquesta comanda.

<img width="343" height="20" alt="image" src="https://github.com/user-attachments/assets/9e1632ce-e516-4e7d-a36c-4c3be3c46557" />

Seguidament editarem el fitxer **/etc/nsswitch.conf** i afegirem **files systemd** al mig de cada linia.

<img width="697" height="231" alt="image" src="https://github.com/user-attachments/assets/6b668762-554f-400c-a17e-23ab29ba254d" />

Despres al fitxer **/etc/pam.d/common-password** haurem de borrar aquesta part d'una linia.

<img width="699" height="284" alt="image" src="https://github.com/user-attachments/assets/01334baa-b0ac-4213-8f12-8a9d32669867" />

Casi acabariem i dins d'aquest fitxer **/etc/pam.d/common-session** afegirem l'ultima linia que es veu, serveix perque quan un usuari canvii la seva contrasenya, s'actualitzi automaticament al servidor LDAP sense que l'hagi de teclejar dues vegades.

<img width="698" height="410" alt="image" src="https://github.com/user-attachments/assets/93849ed2-821e-4710-801c-75473ba49c96" />

Ara modificariem i ficariem el seguent al fitxer **/usr/share/ligthdm/lightdm.conf.d/50-ubuntu.conf** per 

<img width="680" height="94" alt="image" src="https://github.com/user-attachments/assets/c001bfe0-d237-4e93-82e8-262041223899" />

Una vegada fet tot aixo, ja podriem surtir del nostre usuari, i iniciar per l'usuari nou que hem creat que es diu **alu1**.

<img width="563" height="609" alt="image" src="https://github.com/user-attachments/assets/92aa1a5a-0598-41d3-bc1a-599eaea50f17" />

## Gestió del domini mitjançant comandes

### Requisits previs

* Fes un dpkg-reconfigure slapd al servidor per tal de deixar la base de dades buida i només amb el domini l’usuari admin creat. Comprova-ho amb un slapcat.

<img width="2171" height="724" alt="image" src="https://github.com/user-attachments/assets/5912be5b-1f35-4c7b-b0d6-8b99ca5027c9" />

<img width="1617" height="973" alt="image" src="https://github.com/user-attachments/assets/52ce8285-3cee-46ca-879a-6b651fb12cb6" />


* Descarrega l'arxiu dades_pt10.ldif del moodle i amb la comanda ldapadd carrega els usuaris, grups i uos (Compte que el domini és vesper.cat, hauràs de modificar-lo pel teu)

<img width="1708" height="921" alt="image" src="https://github.com/user-attachments/assets/19b851bc-ea67-4594-98e8-162e2b9fc7f8" />

I afegim el **.ldif** amb **ldapadd**.

<img width="1746" height="901" alt="image" src="https://github.com/user-attachments/assets/2044a705-e712-428d-9deb-1794aa2dcac0" />


* Fes un altre slapcat per tal de comprovar que les dades s'han carregat correctament.

<img width="1231" height="1278" alt="image" src="https://github.com/user-attachments/assets/a404209c-6e4a-4dbd-83ac-cab4a342d983" />


### Activitats

* Quantes uos hi ha? **Hi ha 2 UO** Quants usuaris hi ha al domini? **Hi ha 3 usuaris**

<img width="1979" height="795" alt="image" src="https://github.com/user-attachments/assets/06e1e949-63b0-46aa-8d3c-e6a52996db6d" />

* Crea una nova uo anomenada asix

<img width="755" height="164" alt="image" src="https://github.com/user-attachments/assets/4f8103b3-2367-4b6c-b2ef-1607c51404cf" />

* Esborra l’atribut roomnumber i homeDirectory de l’usuari ejohnson

Amb aquest cas no existeix cap usuari **ejohnson** i cap dels usuaris te assignat roomNumber i homeDirectory per tant primer ho afegiré i despres ho esborraré.

Com que l'usuari esta present no permet eliminar el homeDirectory pero si el seu roomNumber.

<img width="738" height="123" alt="image" src="https://github.com/user-attachments/assets/63dc258c-22da-4fab-b6f5-d5d98aa60b8a" />

Aqui ja l'hauriem creat que es podria veure.

<img width="1272" height="1236" alt="image" src="https://github.com/user-attachments/assets/daa850eb-2836-4362-b04f-ad6582ecb859" />

Executariem la seguent comanda.

<img width="788" height="88" alt="image" src="https://github.com/user-attachments/assets/21617e71-c607-4295-a171-fdca05463381" />

I ja s'hauria esborrat.

<img width="1309" height="1202" alt="image" src="https://github.com/user-attachments/assets/b4a2beed-be7e-46b8-8d2d-5f7427dc17e9" />

* L’usuari kvaughan en quants grups el trobem com a uniqueMember i quins són?

Utilitzant l’usuari xavier com a substitut de kvaughan:

Nombre de grups: 1

Grups on apareix com a memberUid: informatica

<img width="808" height="85" alt="image" src="https://github.com/user-attachments/assets/332d6426-454c-4e1c-b81e-03883cd86e12" />

* Trau de la uo People a 3 usuaris i afegeix-los a la uo asix

Aquest seria el fitxer que he creat.

<img width="1421" height="1107" alt="image" src="https://github.com/user-attachments/assets/67d63c60-90c9-4483-b331-54d8a8984c16" />


Amb la seva comanda per executar-lo.

<img width="776" height="182" alt="image" src="https://github.com/user-attachments/assets/177dd476-5325-45b2-8995-f16546a514a1" />

Comprovacio:

<img width="1310" height="1200" alt="image" src="https://github.com/user-attachments/assets/9db5010d-a76d-4842-a109-836c1c6e9e72" />


* Quants grups hi ha dintre de la uo Groups?

Amb aquest cas 0

<img width="811" height="93" alt="image" src="https://github.com/user-attachments/assets/5bca67a4-b0ca-483c-9d11-397c1a73a46b" />

* Esborra la uo People

En aquest cas esborraria la "uo" de "rrhh" ja que la de "People" no existeix.

<img width="801" height="61" alt="image" src="https://github.com/user-attachments/assets/50033580-013c-4ed1-8aa4-3bb85b598cb8" />


* Modifica el uid de l’usuari hmiller a hamiller

Com que el usuari hamiller no exiteix ho faré amb l'usuari xavier, amb aquest fitxer.

<img width="808" height="158" alt="image" src="https://github.com/user-attachments/assets/be75f2d3-fc85-4087-b754-13d95496bc8b" />

I aquesta comanda.

<img width="701" height="89" alt="image" src="https://github.com/user-attachments/assets/33a64693-7a1f-4810-b709-6e2d2abd5b67" />


Comprovació:

<img width="1324" height="1188" alt="image" src="https://github.com/user-attachments/assets/e7e9f482-9aec-4d45-bfb1-a6153971d064" />

* Crea un nou usuari amb dos atributs opcionals per a  la classe posixAccount, ho fare amb aquest fitxer.

<img width="1447" height="1087" alt="image" src="https://github.com/user-attachments/assets/49dbf014-3d46-4d92-a014-bf5df04634da" />

Comanda:

<img width="794" height="87" alt="image" src="https://github.com/user-attachments/assets/e5f94566-7e44-42fb-99b0-1bc1da40b580" />

* Afegeix un parell més d’opcionals a l’usuari anterior

<img width="2153" height="730" alt="image" src="https://github.com/user-attachments/assets/62aee637-9a6e-4f36-b85a-39e54eef6750" />

Comanda:

<img width="806" height="91" alt="image" src="https://github.com/user-attachments/assets/5f031a75-2fa5-4785-9dd2-cd22d030e9ca" />

* Modifica el mail de l’usuari jburrell per jburrell@gmail.com

Com que el usuari jburrell no existeix ho he fet amb ramon.

<img width="800" height="187" alt="image" src="https://github.com/user-attachments/assets/74905ab9-2571-4a8f-acf3-ac9ad4f5ce5f" />

Comanda:

<img width="788" height="87" alt="image" src="https://github.com/user-attachments/assets/daed430c-ccd2-4502-8646-26f4f5016343" />

Comprovació:

<img width="277" height="72" alt="2026-02-20_13-35" src="https://github.com/user-attachments/assets/bf626264-87a0-40f8-816d-455d4a8f7d70" />

* Crea un nou grup dintre de la uo Groups i afegeix 3 usuaris

Com que prèviament he mostrat que no existeix la UO Groups ho faré sobre la de asix.

<img width="2033" height="773" alt="image" src="https://github.com/user-attachments/assets/794fcb46-6378-45ba-8386-09e8bf8a0dbf" />

Comanda:

<img width="810" height="90" alt="image" src="https://github.com/user-attachments/assets/54a87f00-fdfd-410f-8024-7bbb4f6fd409" />

Comprovació:

<img width="1779" height="884" alt="image" src="https://github.com/user-attachments/assets/352b81ce-c36f-40e2-9536-fb9d485b8931" />

* Treu del grup creat anteriorment a un usuari

<img width="798" height="161" alt="image" src="https://github.com/user-attachments/assets/3299d01c-68fd-420b-a434-f0a6d5ec1609" />


Comanda:

<img width="782" height="89" alt="image" src="https://github.com/user-attachments/assets/8571f0f0-5f62-4f51-ad8e-5ce3c386bf63" />

* Mostra tots els usuaris de la uo Asix que el seu uid comenci per la lletra x i formin part també de la uo Recursos Humans

<img width="797" height="107" alt="image" src="https://github.com/user-attachments/assets/029959d3-0d28-4472-97e3-6212b73c21d1" />

* Mostra tots els usuaris del domini on el seu uidNumber estigui entre 1010 i 1030 (inclosos). Quants en son?

<img width="807" height="111" alt="image" src="https://github.com/user-attachments/assets/d7f1bc01-3d69-4420-be5b-0aa7d0f008e9" />

* Usuaris on el seu telèfon acabi en un 2 o el seu cognom en una n. Quants?

Amb aquest cas son 0 usuaris.

<img width="810" height="69" alt="image" src="https://github.com/user-attachments/assets/366e1ab1-838f-4cc2-bf68-3dd5cba2a1b6" />

* D’un sol cop, a l’usuari que tu vulguis, esborra un atribut, afegeix-ne un altre i modifica un tercer.

<img width="1618" height="972" alt="image" src="https://github.com/user-attachments/assets/beb4ee07-6a60-46bd-bd8d-f7369398a766" />

Comprovació:

<img width="2170" height="725" alt="image" src="https://github.com/user-attachments/assets/d8ff7549-d83e-4a7e-80bd-11666eb995f4" />

## Entorn grafic

Per a configurar LDAP en un entorn gràfic tenim moltes opcions com ara:

* phpldapadmin
* apache directory stdio
* jxplorer
* ldap account manager (LAM)

Amb aquest cas he escollit LAM ja que em sembla molt fàcil d'utilitzar i molt intuitiu.

### Requeriments Prèvis

Primerament hem d'instalar tots aquests paquets ja que LAM utilitza php i hem d'instalar tots els seus requeriments per al seu funcionament.


<img width="733" height="196" alt="2026-02-18_17-21" src="https://github.com/user-attachments/assets/2e67a43a-7ae1-421d-9c12-90c343c3a69c" />

I ara descarregaré el binari **.deb**.

<img width="734" height="134" alt="2026-02-18_17-23" src="https://github.com/user-attachments/assets/4f8f4c3b-7e2f-4b3d-ab51-56dd18ea5d0a" />

<img width="735" height="131" alt="2026-02-18_17-24" src="https://github.com/user-attachments/assets/cf3658e4-0da9-4c6f-b9ff-3510e2f024fd" />


## Configuració del entorn gràfic

Un cop ja instal·lat podem accedir via la IP al directori **/lam**. Aqui ficarem una contrasenya per entrar al panel administratiu. I una vegada ficada ja estem aquí dins per poder gestionar el **LDAP**.

<img width="693" height="401" alt="2026-02-18_17-27" src="https://github.com/user-attachments/assets/ecbd687c-afe4-442e-af19-12fdb5106fde" />

Ara quan guardesim ens "expulsará" i ens fará iniciar sessió.

<img width="791" height="527" alt="2026-02-18_17-41" src="https://github.com/user-attachments/assets/105f0a65-aa52-4feb-9230-21765132fabb" />

Ara hem de crear un usuari per a la gestió d'aquest per tant anirem a **"Editar perfiles del servidor"**.

<img width="440" height="338" alt="2026-02-18_17-42" src="https://github.com/user-attachments/assets/c78f32b8-1756-4669-bebc-466c336f6554" />

I aquí farem clic amb aquest opció.

<img width="787" height="455" alt="2026-02-18_17-42_1" src="https://github.com/user-attachments/assets/1cf79ab5-4dca-4981-885a-95744a8505cd" />

<img width="621" height="353" alt="2026-02-18_18-00" src="https://github.com/user-attachments/assets/f7f2eaee-9f3b-472a-adcd-c57aaa0c7a56" />

I ja estem dins com a l'usuari LAM.

<img width="816" height="477" alt="2026-02-18_18-04" src="https://github.com/user-attachments/assets/157aa314-e1d0-45d0-b1b8-b30798c30442" />

Aquí ficarem la nostra configuració LDAP.

<img width="2069" height="760" alt="image" src="https://github.com/user-attachments/assets/bea2c8da-b4f2-42f1-8a7f-4af0e835725d" />

També haurem de anar al **Account Types** i canviar aquesta configuració d'aquí.

<img width="627" height="262" alt="image" src="https://github.com/user-attachments/assets/27d5a79e-118a-4b4f-a912-2369fbc6259a" />

Ara ja podem iniciar sessió amb el usuari admin del nostre domini LDAP.

<img width="389" height="312" alt="2026-02-18_18-18" src="https://github.com/user-attachments/assets/6b005c3f-aff0-49b6-8b59-2929a11b307f" />

Per aqui ja podem veure els usuaris que tenim creats.

<img width="1724" height="912" alt="image" src="https://github.com/user-attachments/assets/3f60c897-d7c0-420a-b916-71467dac5bc3" />


### Creació de una nova OU

Per a la creació d'una nova OU primerament hem d'anar a **"Tools"** i **"OU Editor"**.

<img width="356" height="236" alt="2026-02-18_18-20" src="https://github.com/user-attachments/assets/f71694c9-d757-46cf-a677-24a63484e4ae" />

Aquí fiquem el nom de com volem que es digui aquesta OU.

<img width="1015" height="209" alt="2026-02-18_18-20_1" src="https://github.com/user-attachments/assets/76341059-402a-41f2-ae37-33f436ec313d" />

I fem OK. I ja la tenim creada.

<img width="344" height="152" alt="2026-02-18_18-21" src="https://github.com/user-attachments/assets/5590605c-da92-4c54-925f-4cc3d6ab326c" />

### Creació d'un nou grup

Per a crear un nou grup primerament hem d'anar a **"Accounts"** i **"Groups"**.

<img width="449" height="130" alt="2026-02-18_18-21_1" src="https://github.com/user-attachments/assets/38fe7d4a-8637-4a21-a180-386ae6089c67" />

Una vegada aquí anirem a **"New Group"**.

<img width="549" height="320" alt="2026-02-18_18-22_1" src="https://github.com/user-attachments/assets/af0a0b76-c244-42b9-9b14-3c372b5a19d5" />

I finalment crearem el grup, amb aquest cas li fiquem un nom i un UID.

<img width="905" height="269" alt="2026-02-18_18-30" src="https://github.com/user-attachments/assets/2364fdff-a0e6-46cf-88d0-6174f670778a" />

I s'ha creat correctament el grup.

<img width="715" height="171" alt="2026-02-18_18-31" src="https://github.com/user-attachments/assets/2ba32186-af59-4d43-b134-a955fb8fe001" />

Comprovació:

<img width="889" height="341" alt="2026-02-18_18-31_1" src="https://github.com/user-attachments/assets/9e0e1286-b179-408d-8bd6-ce75bc0b177f" />

### Creació d'un nou usuari

Per a crear un nou usuari primerament hem d'anar a **"Accounts"** i després a **"Users"**.

<img width="298" height="66" alt="2026-02-18_18-32" src="https://github.com/user-attachments/assets/4df0d191-0c57-4d8e-b335-8407ca67ad4f" />

Aquí anirem a **"New User"**.

<img width="848" height="426" alt="2026-02-18_18-32_1" src="https://github.com/user-attachments/assets/dff5a5c2-0367-4f98-99d8-59748dfe6eb1" />

Un cop aquí pasarem a la gestió personal.

<img width="782" height="157" alt="image" src="https://github.com/user-attachments/assets/414bdf7f-99b0-45df-94e7-d0fd96b55f36" />

I ara la gestió UNIX.

<img width="797" height="212" alt="image" src="https://github.com/user-attachments/assets/ae7c08ff-dd26-4d90-85c5-25bcc982c6f5" />

Finalment podem ficarli una contrasenya de la següent manera.

<img width="683" height="423" alt="2026-02-18_18-37" src="https://github.com/user-attachments/assets/3ea00955-bde9-4848-8651-89fa37c525d4" />

I ja tenim el usuari creat correctament.

<img width="676" height="155" alt="2026-02-18_18-38" src="https://github.com/user-attachments/assets/1240daec-b4d5-4e44-bd81-d1d9c69e44b4" />

Verificació:

<img width="856" height="456" alt="2026-02-18_18-38_1" src="https://github.com/user-attachments/assets/790f3576-958d-4aeb-8401-3b505e829020" />

### Accedir desde el client amb aquest nou usuari creat

Per fer-ho he obert el client i he accedit via GUI per comprovar he executat la comanda `id`.

<img width="619" height="81" alt="image" src="https://github.com/user-attachments/assets/ef104953-3f64-4e22-aa37-e8324fefe537" />


## Servidor Samba

Finalment, configurarem Samba per permetre l'accés a recursos compartits amb autenticació LDAP o local.

Primer instal·lem el paquet `samba`.

<img width="622" height="129" alt="image" src="https://github.com/user-attachments/assets/6c21fb8f-d466-4d52-9e53-1d8fb23e8cdf" />

Primerament, procedirem a la creació del directori que volem compartir i n'ajustarem els permisos i la propietat. Definirem l'usuari i el grup corresponents per garantir que només els membres autoritzats tinguin accés al recurs compartit.

<img width="420" height="173" alt="image" src="https://github.com/user-attachments/assets/8ab7f83b-485b-4a4e-98a3-51467352719f" />

Despres fare la creació d'usuaris i grups per realitzar les proves.

<img width="488" height="303" alt="image" src="https://github.com/user-attachments/assets/670f67b6-a377-4988-9efd-24839d04e292" />


I a cada usuari he assignat la seva contrasenya.

<img width="333" height="292" alt="image" src="https://github.com/user-attachments/assets/732d6887-6da7-4272-8e70-b8f8a5960f74" />

Procedire a l'edició del fitxer smb.conf per afegir-hi la declaració del recurs compartit. Això inclou configurar els paràmetres necessaris perquè el directori sigui visible i accessible des de la xarxa per als clients autoritzats.

<img width="494" height="377" alt="image" src="https://github.com/user-attachments/assets/ebdfe297-c9ca-491a-bcc8-95adc2d3c96f" />

Per tal que els canvis realitzats en el fitxer de configuració s'apliquin correctamente, caldrà reiniciar el servei de Samba. Això permetrà que el sistema carregui la nova definició del recurs compartit."

<img width="697" height="393" alt="image" src="https://github.com/user-attachments/assets/b237032d-2590-45d2-bf9f-0655f9bb4984" />

## Configuració client smb

Accedim al client, que es troba a la mateixa xarxa, com he comprovat amb el ping

<img width="1877" height="838" alt="image" src="https://github.com/user-attachments/assets/09237282-2512-4c76-8ab5-a0e350f68321" />

El paquet a instal·lar es **smbclient**.

<img width="598" height="157" alt="image" src="https://github.com/user-attachments/assets/599e7b12-d689-4383-9e90-fc769d0020b4" />

I ja podem connectar-mos mitjançant el navegador de fitxers.

<img width="443" height="44" alt="image" src="https://github.com/user-attachments/assets/b119e755-1af1-4368-80b5-5e2c511e6df2" />

Per comemzat entrarem amb l'usuari anonim.

<img width="622" height="507" alt="image" src="https://github.com/user-attachments/assets/e3484772-52a0-4194-a94b-ed377b95efee" />

Crearem una carpeta "anonim".

<img width="436" height="127" alt="image" src="https://github.com/user-attachments/assets/589511c5-4f21-4a4c-bc69-024c098bc898" />

I veiem que es crea perfectament.

<img width="251" height="142" alt="image" src="https://github.com/user-attachments/assets/4cca0f9a-53ee-43a5-ad3b-f5f88feaa2da" />

Surtirem. 

<img width="213" height="214" alt="image" src="https://github.com/user-attachments/assets/8f96bf84-775c-4799-9dd1-bd055d5482cb" />

I tornarem a entrar amb l'usuari "naim".

<img width="469" height="429" alt="image" src="https://github.com/user-attachments/assets/d43f61a2-0339-4dac-9c7e-8bb924459bd7" />

Creem carpeta.

<img width="433" height="113" alt="image" src="https://github.com/user-attachments/assets/6ee1f356-c671-4e98-86ff-f3dce4145ac3" />

I es crea sense cap problema.

<img width="240" height="140" alt="image" src="https://github.com/user-attachments/assets/4d0112ca-4f97-4c38-a86e-779daf2f0748" />

Ara provarem amb l'usuari "eros".

<img width="466" height="429" alt="image" src="https://github.com/user-attachments/assets/457724ab-ef5e-4057-965a-aa287b3b732d" />

I podem veure que amb aquest usuari, no es pot crear cap carpeta.

<img width="600" height="200" alt="image" src="https://github.com/user-attachments/assets/c087c19b-30f5-4d34-a184-9b1ab245368f" />


## NFS

### 1 exercici nfs sense ldap 

En aquest apartat configurarem un servidor NFS per compartir directoris amb un client, sense utilitzar autenticació LDAP inicialment.

Actualitzarem tots els paquets.

<img width="776" height="233" alt="image" src="https://github.com/user-attachments/assets/68053bfe-5b5c-4193-8ebe-f53d823b4713" />


Primer, al **servidor**, instal·lem el paquet `nfs-kernel-server`.

<img width="775" height="246" alt="image" src="https://github.com/user-attachments/assets/2e988b18-e7fa-4e2e-abf6-eb69aa6b163f" />

Creem el directori que volem compartir i li assignem els permisos necessaris. En aquest cas, creem `/1exercici`.

<img width="778" height="222" alt="image" src="https://github.com/user-attachments/assets/4bca7fa9-e5e6-46fa-bf38-afca5a6033b8" />

Editem el fitxer `/etc/exports` per definir qui pot accedir al recurs i amb quins permisos. Afegim la línia corresponent al nostre directori i xarxa/client.

<img width="629" height="344" alt="image" src="https://github.com/user-attachments/assets/17e968d5-6660-4dfa-994d-cc05501b0376" />

Apliquem la nova configuració i reiniciem el servei `nfs-kernel-server` per assegurar-nos que els canvis s'apliquen.

<img width="806" height="256" alt="image" src="https://github.com/user-attachments/assets/48a92b86-56ed-472b-b285-c37fe4704200" />

Ara crearem un arxiu anomenat `hola` a la carpeta `/1exercici`.

<img width="359" height="58" alt="2026-02-10_13-00" src="https://github.com/user-attachments/assets/3ce9553d-93d1-4404-9ddb-98e26fc5a809" />

Ara passem al **client**. Instal·lem el paquet `nfs-common, rpcbind` i creem el punt de muntatge on vincularem el directori remot.

<img width="777" height="222" alt="image" src="https://github.com/user-attachments/assets/8959dece-2a68-42d7-91c2-9e1c356936ce" />

Muntem manualment el recurs compartit NFS al punt de muntatge creat. Utilitzem la IP del servidor i la ruta del directori exportat.

<img width="772" height="266" alt="image" src="https://github.com/user-attachments/assets/33555c4b-07a7-4c67-a603-7e073bbf22c7" />

Verifiquem que tenim accés d'escriptura (si així ho hem configurat) creant un fitxer de prova dins del directori muntat.

<img width="769" height="256" alt="image" src="https://github.com/user-attachments/assets/d5185b04-5018-4c4c-b9ee-769d27386c1c" />

Per fer que el muntatge sigui permanent i es mantingui després de reiniciar, afegim l'entrada corresponent al fitxer `/etc/fstab`.

<img width="803" height="280" alt="image" src="https://github.com/user-attachments/assets/8331fe14-4987-457c-a6e6-6cc070899a58" />

Finalment, podem reiniciar el client o fer un `mount -a` per comprovar que el recurs es munta automàticament sense errors.

<img width="194" height="49" alt="image" src="https://github.com/user-attachments/assets/3f33c8f9-cf53-4418-91ec-c656a7ae4522" />

<img width="681" height="104" alt="image" src="https://github.com/user-attachments/assets/23971487-44ea-4c30-b351-91378bd8d42b" />

### NFS amb LDAP

Primerament al nostre servidor prepararem el directori.

<img width="413" height="156" alt="2026-02-10_13-51" src="https://github.com/user-attachments/assets/6a237ed6-da20-4b4b-935f-c8ae490b63ce" />

I tal com hem fet anteriorment ficarem aquesta ruta **/homes** al **/etc/exports**.

<img width="508" height="324" alt="2026-02-10_13-53" src="https://github.com/user-attachments/assets/cda2076d-3900-4af4-9a52-47da22df2ed1" />

Ara anirem al nostre client i farem el seguent.

<img width="723" height="219" alt="image" src="https://github.com/user-attachments/assets/343beb44-7ab9-4eea-b823-d88aac9aa024" />

Al fstab ficarem aquesta línia tal i com hem fet anteriorment.

<img width="803" height="306" alt="image" src="https://github.com/user-attachments/assets/0488f3f2-2415-4ecb-a33c-b9970b3a72fb" />

Guardem i tornem a la part del servidor, ara crearem l'usuari Marcel. MOLT IMPORTANT INDICA EL SEU HOME amb aquest cas **/homes**

<img width="704" height="481" alt="image" src="https://github.com/user-attachments/assets/f485ee1c-975c-4bee-bddd-8eb2d4a291b8" />

I amb ldapadd l'afegim.

<img width="741" height="82" alt="image" src="https://github.com/user-attachments/assets/a1d524d9-dbff-4657-9c4d-e4d91926c139" />

Un cop fet aquesta gestió per part del client i el servidor, reiniciarem el client i entrarem com a l'usuari marcel. Si tot ha funcionat correctament dins de **/homes/marcel** hauriem de veure les carpetes basiques com ara **Descargas**, **Documentos** etc...

I si.

<img width="728" height="155" alt="image" src="https://github.com/user-attachments/assets/3f73369f-4084-40f6-b1a8-84296605c1df" />

<img width="524" height="67" alt="2026-02-18_10-32_1" src="https://github.com/user-attachments/assets/18da9858-f630-4765-b20d-4e8d89038a1d" />

---
layout: default
title: "Sprint 1: Instal·lació i Configuració Inicial"
---

## Virtualització i instalacio del SO Ubuntu
Primero abriremos VirtualBox y haremos clic en “Nueva”. A continuación, se abrirá una ventana donde deberemos asignar un nombre a la máquina virtual. En mi caso, le pondré “Ubuntu 22.04”, tal y como se muestra en la imagen. Después, pulsaremos en “Siguiente”.

<img width="850" height="461" alt="2025-10-25_17-19" src="https://github.com/user-attachments/assets/db1cbc9e-37b6-4c6e-9136-8e0aa1a9b40d" />

Ahora es momento de asignar la cantidad de memoria RAM que tendrá la máquina virtual. Para saber cuál es la cantidad recomendada, podemos consultar los requisitos mínimos del sistema operativo en su página oficial: https://ubuntu.com/download/desktop.

Pondremos 4GB, ya que es el mínimo recomendado, y 3 cores para la CPU.

<img width="862" height="469" alt="2025-10-25_17-20" src="https://github.com/user-attachments/assets/777e1eb6-3169-45ad-9e4e-5990f5db2f34" />

Ahora, debemos crear el disco. Éste será de 80GB.

<img width="857" height="462" alt="2025-10-25_17-21" src="https://github.com/user-attachments/assets/67838a2f-b612-4a05-b448-4e73a4b6cca2" />

Por último, comprobamos que todos los datos del resumen de la máquina virtual sean correctos y, si todo está bien, procedemos a crear la máquina.

<img width="857" height="464" alt="2025-10-25_17-21_1" src="https://github.com/user-attachments/assets/707ae346-f753-4c6b-8b2a-d3518c26702a" />

Y en red, ponemos red nat, ya que Las máquinas virtuales dentro de la misma red NAT pueden conectarse entre sí y al igual que con nat, tiene salida a internet

<img width="724" height="235" alt="2025-10-25_17-23" src="https://github.com/user-attachments/assets/3ad9063f-b31d-4148-b40d-a86c6ea56186" />

Podemos crear una nueva red NAT en Herramientas > Red > Red NAT y crear

<img width="855" height="201" alt="2025-10-25_17-24" src="https://github.com/user-attachments/assets/28e5da75-27f0-469e-9ae0-cb1141ac9cc7" />

Abrimos la máquina virtual, y seleccionamos Try or install Ubuntu

<img width="717" height="286" alt="2025-10-25_17-32" src="https://github.com/user-attachments/assets/dab5d4ff-2ceb-4681-8874-40304ea08ed9" />

Ahora, seguimos el proceso de instalación hasta que llegamos a la sección de las particiones.

<img width="823" height="613" alt="2025-10-25_17-34" src="https://github.com/user-attachments/assets/41e5c705-0272-463d-b39e-5faab8543f63" />

Aquí, crearemos las siguientes particiones en el disco:

/home: El tamaño de esta partición será de 16GB

<img width="860" height="338" alt="2025-10-25_17-36" src="https://github.com/user-attachments/assets/e6ea2750-46c4-4fee-ab8b-b80d483909f6" />

/boot: Puesto que, en un futuro, haremos un dualboot, pondremos 1GB de espacio para esta partición.

<img width="806" height="344" alt="2025-10-25_17-43" src="https://github.com/user-attachments/assets/9e157e23-a222-4919-b3bf-dfee5b7dacdc" />

/: Sera de 16GB

<img width="804" height="304" alt="2025-10-25_17-43_1" src="https://github.com/user-attachments/assets/af19987e-fa5d-4634-9034-00dfc51dd22e" />

/swap: Sera de 4GB

<img width="813" height="333" alt="2025-10-25_17-52" src="https://github.com/user-attachments/assets/f1c53da9-9bc4-4192-aae5-889f66085c7d" />

Y ahora continuamos con la instalacion con normalidad.

<img width="825" height="615" alt="2025-10-25_17-53" src="https://github.com/user-attachments/assets/a30759ff-53f3-4a0e-8f5f-2dadc6e719fd" />

## Llicènciament
Ubuntu como tal utiliza la "GNU GPLv2" para su núcleo y en la mayoría de sus aplicaciones, pero Ubuntu es una distribución de GNU/Linux, y no tiene una sola licencia, sino una combinación de licencias de software libre y código abierto como GPL, LGPL, MIT... Esta licencia asegura que el código sea libre y que cualquier modificación también tiene que ser libre.
<img width="597" height="189" alt="2025-10-25_19-34" src="https://github.com/user-attachments/assets/fbe7f593-93df-42de-a1ca-c4da83bcd68b" />

## Gestors d'arrencada per a instalacions DUALS
En la maquina virtual, activamos la siguiente opcion:

<img width="878" height="568" alt="2025-10-25_18-26" src="https://github.com/user-attachments/assets/507edbd3-31ab-4785-b5af-e5ebce3b5235" />

Ponemos la ISo de Windows y arrancamos la maquina.

<img width="485" height="295" alt="2025-10-25_18-32" src="https://github.com/user-attachments/assets/4ae31ada-425a-4311-916f-a28cdd30926a" />

Luego de eso empezamos la instalacion con normalidad hasta llegar a este punto.

<img width="641" height="479" alt="2025-10-25_18-35" src="https://github.com/user-attachments/assets/7e0a1b64-a3cd-4860-b220-ca6c7772190c" />

Ya por ultimo continuamos la instalacion.

<img width="996" height="610" alt="2025-10-25_18-44" src="https://github.com/user-attachments/assets/05a377e3-d924-4230-8b02-139284efaf1f" />

Y ya tendriamos el windows instalado.

<img width="556" height="355" alt="2025-10-25_18-48" src="https://github.com/user-attachments/assets/f7ed5103-de8b-4bf8-8e5d-84da67f582ac" />

Para recuperar el grub ponemos la iso de Super-Grub2:

<img width="483" height="294" alt="2025-10-25_18-56" src="https://github.com/user-attachments/assets/dd3ecfe3-9423-45ee-a4d7-19847c3be7cf" />

Entramos al boot menu de vbox

<img width="418" height="124" alt="2025-10-25_19-45" src="https://github.com/user-attachments/assets/6fe8fa06-a220-49a8-8c82-ab0a15d7fa18" />

Seleccionamos "detect and show boot methods".

<img width="618" height="402" alt="2025-10-25_18-59" src="https://github.com/user-attachments/assets/31d6242e-1007-4b0a-9f89-e1287163a6ce" />

Buscamos grub.cfg de ubuntu.

<img width="630" height="380" alt="2025-10-25_19-04" src="https://github.com/user-attachments/assets/6ec06541-f910-4b43-a3cf-e5ff59ae1b59" />

Una vez entramos en Ubuntu, ejecutamos las siguientes comandas para arreglar el grupo desde el terminal

<img width="643" height="61" alt="2025-10-25_19-05" src="https://github.com/user-attachments/assets/bc9155c7-4c44-4b40-a958-25ea1311024f" />

<img width="600" height="93" alt="2025-10-25_19-07" src="https://github.com/user-attachments/assets/ab451b95-4969-470c-b70f-b6d7f475a9b2" />

Reiniciamos y veremos que ya entramos en el grub para poder seleccionar ubuntu o windows.

<img width="370" height="185" alt="2025-10-25_19-09" src="https://github.com/user-attachments/assets/6681e575-2271-4017-81e1-5511167a792e" />

## Punts de restauracio
Primeramente haremos un apt install timeshift, esta herramienta se utiliza para restaurar el sistema si una actualización la rompe

<img width="1028" height="332" alt="2025-10-25_20-00" src="https://github.com/user-attachments/assets/9bc9099f-1d0c-48cf-9126-f71b54bd1d22" />

Después tomaremos un disco vacío de 20 GB y creamos una única partición que ocupara todo su espacio

<img width="822" height="489" alt="2025-10-25_20-02" src="https://github.com/user-attachments/assets/0026c248-f1a9-49b4-8944-6bfd61edb6ae" />

Podemos ver cómo se ha creado la partición

<img width="659" height="465" alt="2025-10-25_20-03" src="https://github.com/user-attachments/assets/9402ebda-90f6-4dfa-a114-a2e38f0fff2a" />

Seguidamente podremos ver cómo se ha formateado la partición /dev/sdb1 para que pueda ser utilizada por un sistema operativo Linux para almacenar archivos y carpetas

<img width="743" height="242" alt="2025-10-25_20-05" src="https://github.com/user-attachments/assets/97e7b9ec-29ef-436f-a999-ba712c427048" />

A continuación haremos un ls para ver las carpetas que tenemos en nuestra /home, haremos un touch hola, para crear un archivo, también haremos un mkdir hola para crear una carpeta, con los podremos ver cómo se ha creado correctamente

<img width="904" height="178" alt="2025-10-25_20-07" src="https://github.com/user-attachments/assets/6155dd6e-ab07-4be2-9934-acce19c6bf4b" />

Una vez hecho todo lo anterior, nos saldrá la aplicación del timeshift, entraremos y saldrá el asistente de configuración, escogeremos RSYNC

<img width="792" height="254" alt="2025-10-25_20-08" src="https://github.com/user-attachments/assets/174a0026-68cb-4358-928e-2ed18f8fb3df" />

Seguidamente escogeremos el sdb1 que es el disco que hemos creado anteriormente

<img width="767" height="258" alt="2025-10-25_20-09" src="https://github.com/user-attachments/assets/cceeed61-6d4f-4b62-9dde-3d36dccf33f8" />

Indicaremos que sólo cuando arranque

<img width="720" height="587" alt="2025-10-25_20-10" src="https://github.com/user-attachments/assets/8dc1055a-5a78-41c7-8975-ceee615535f8" />

Finalmente pondremos que se excluyan todos los archivos de root, y que se incluyan todos los archivos del usuario

<img width="857" height="219" alt="2025-10-25_20-11" src="https://github.com/user-attachments/assets/23f82998-a0ec-4604-b6f9-c1732a912e46" />

Crearemos otra instantanea, iremos a --> crea, y allí se nos empezará a crear la instantanea

<img width="1920" height="1080" alt="Captura de pantalla de 2025-10-07 13-03-12" src="https://github.com/user-attachments/assets/2ada3fbe-ec47-4dcc-aacc-83bfbe18c824" />

Aquí podemos ver cómo se nos ha creado la ultima instantanea que estábamos haciendo

<img width="678" height="518" alt="2025-10-25_20-15" src="https://github.com/user-attachments/assets/352fa3ac-c983-40e1-84ac-c420ee7cab98" />

Ahora lo que haremos será borrar la carpeta adiós y el archivo hola, esto lo haremos para recuperaremos la instantanea que hemos creado y podremos recuperarlo

<img width="583" height="223" alt="2025-10-25_20-16" src="https://github.com/user-attachments/assets/54b28228-5a3c-4387-85da-ca03d89585f2" />

Seleccionaremos la instantanea y pulsaremos en recuperar, haremos siguiente, siguiente ,siguiente

<img width="672" height="549" alt="2025-10-25_20-18" src="https://github.com/user-attachments/assets/afdbb2f1-9505-4b31-b9ea-0af37d398171" />

<img width="676" height="556" alt="2025-10-25_20-18_1" src="https://github.com/user-attachments/assets/3db75ff0-94af-4d2f-be71-15fb72c1ec2a" />

<img width="649" height="528" alt="2025-10-25_20-18_2" src="https://github.com/user-attachments/assets/4b853db6-7da4-418a-95fe-e581ef088c2b" />

Se reiniciara el sistema y con una pantalla gris nos indicara que se está cargando la instantanea

<img width="1920" height="1080" alt="Captura de pantalla de 2025-10-07 13-55-19" src="https://github.com/user-attachments/assets/dde49c5c-f9e5-44fa-9dff-1840edc7da6e" />

Finalmente haremos un ls y podremos ver que si teníamos bien hecha la instantanea tendremos otra vez la carpeta adiós y el archivo hola

<img width="609" height="37" alt="2025-10-25_20-39" src="https://github.com/user-attachments/assets/b22c67ea-c5c9-4d13-843f-73ce763fbcb5" />

## Configuracio de la xarxa
## Comandes generals i instal·lacions




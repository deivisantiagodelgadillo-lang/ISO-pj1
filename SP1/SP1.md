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
## Punts de restauracio 
## Configuracio de la xarxa
## Comandes generals i instal·lacions




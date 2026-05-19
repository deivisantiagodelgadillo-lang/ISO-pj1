# Sprint 4: Configuración del Software Base y Sistemas de Almacenamiento en Windows

---

## 1. Introducción

Los RAIDs (Redundant Array of Independent Disks) son sistemas que permiten combinar varios discos físicos en una única unidad lógica para conseguir mejoras de rendimiento, capacidad o seguridad. Estos sistemas pueden ser gestionados tanto por hardware (controladoras RAID) como por software, siendo este último el caso de los sistemas operativos modernos como Windows Server. Cada nivel de RAID ofrece características diferentes dependiendo de si el objetivo es mejorar la velocidad, ofrecer redundancia o combinar ambas opciones.

El RAID 5 es uno de los niveles más utilizados en entornos profesionales porque consigue un equilibrio óptimo entre rendimiento, capacidad y tolerancia a fallos. Este sistema distribuye tanto los datos como la información de paridad entre todos los discos de la matriz. La paridad tiene la función de reconstruir la información en caso de que uno de los discos falle, permitiendo que el sistema siga funcionando y garantizando la disponibilidad en entornos críticos como servidores. Para su configuración se requiere un mínimo de tres discos duros y la capacidad útil total es la suma de todos los discos menos uno, ya que el espacio equivalente a una unidad se dedica a la paridad.

---

## 2. Desarrollo de la práctica paso a paso

### Paso 1: Preparación de la máquina virtual

Antes de iniciar el sistema operativo, es necesario configurar el hardware virtual necesario para implementar la matriz de discos:

* En la máquina virtual con Windows Server 2022, se añaden un mínimo de 3 discos adicionales del mismo tamaño (por ejemplo, 10 GB cada uno).
* Una vez conectados los dispositivos de almacenamiento, se inicia la máquina virtual.

<img width="883" height="534" alt="image" src="https://github.com/user-attachments/assets/9a6f4a93-cb97-4821-96fc-bc89c4b8bcb4" />

---

### Paso 2: Inicialización y configuración de los discos

Una vez iniciado el sistema, se abre la herramienta de **Administración de discos** ejecutando el comando:

```text
diskmgmt.msc
```

<img width="406" height="220" alt="image" src="https://github.com/user-attachments/assets/d3963112-f13f-4245-829a-11fa119e0572" />

Cuando aparezca el asistente automático, se inicializan los nuevos discos eligiendo el estilo de partición MBR o GPT (se recomienda GPT si el tamaño es superior a 2 TB, aunque en este caso no afecta).

<img width="450" height="322" alt="image" src="https://github.com/user-attachments/assets/ed1d5ba7-d606-4e69-9b12-8b6de6ae1e3a" />

Los discos se mantienen en su estado inicial, sin formatearlos ni crear ningún tipo de partición.

<img width="1207" height="358" alt="image" src="https://github.com/user-attachments/assets/5d30d5ba-215f-4b4b-b787-88642399d258" />

---

### Paso 3: Creación del volumen RAID 5 desde el Administrador de discos

Se hace clic derecho sobre uno de los discos vacíos y se selecciona la opción:

```text
New RAID-5 Volume
```

<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/1a1cd729-2ea0-4a2f-a72a-cc52646b845d" />

Dentro del asistente, se añaden los otros 2 discos restantes a la configuración para formar la matriz.

<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/b5fd1d0b-ef73-4f31-9e82-56572ca31f34" />

Se asigna una letra de unidad al volumen.

<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/454ceb04-4ffe-4f97-ad48-d9b19b38e21f" />

El volumen se formatea utilizando el sistema de archivos **NTFS** y se establece la etiqueta:

```text
RAID5-Test
```

<img width="498" height="410" alt="image" src="https://github.com/user-attachments/assets/89e07d9e-e83e-4519-b3cf-be78cf8c1b30" />

Se espera a que finalice el proceso de formateo y se verifica que aparece como un único volumen en el sistema (con una capacidad útil de 20 GB, correspondiente a la suma de los discos menos el espacio destinado a la paridad).

<img width="1277" height="369" alt="image" src="https://github.com/user-attachments/assets/ac50d18c-6ecb-4074-afc5-783f2f7e0399" />

---

### Paso 4: Pruebas de funcionalidad y acceso

Se abre el Explorador de archivos de Windows y se accede al volumen:

```text
E:\
```

<img width="795" height="595" alt="image" src="https://github.com/user-attachments/assets/faae2fbf-6485-4472-8955-7943027a57bd" />

Se copian archivos de prueba en la raíz de la unidad.

<img width="795" height="595" alt="image" src="https://github.com/user-attachments/assets/b70ab182-f29a-4ac6-885a-2a6c8f3551e7" />

Se abren y se comprueba que los archivos son completamente accesibles y se leen sin problemas.

<img width="703" height="312" alt="2026-05-19_09-49" src="https://github.com/user-attachments/assets/e9c91a48-403c-4ee2-af0c-5bb6aaff2d61" />


---

### Paso 5: Simulación del primer fallo (un disco Offline)

Se vuelve a acceder a la herramienta **Disk Management**. Después, se hace clic derecho sobre uno de los discos que forman el RAID y se selecciona la opción:

```text
Offline
```

para simular un fallo crítico de la unidad.

<img width="795" height="236" alt="image" src="https://github.com/user-attachments/assets/f95935b1-3386-4322-b24a-0688d81c6d5f" />

<img width="1006" height="322" alt="image" src="https://github.com/user-attachments/assets/f6362fcb-9677-4f03-ba22-16b8c2c9c3d5" />

Se observa el comportamiento del sistema: Windows Server mostrará una advertencia indicando que el volumen se encuentra en estado degradado, pero sigue siendo accesible. Se vuelve a comprobar que los archivos pueden abrirse normalmente gracias a la reconstrucción en tiempo real mediante la paridad.

<img width="471" height="199" alt="2026-05-19_09-51" src="https://github.com/user-attachments/assets/bba35c7a-95c1-4977-a134-faa0d5a464e8" />

---

### Paso 6: Simulación del segundo fallo (dos discos Offline)

Se procede a forzar un segundo fallo colocando un **segundo disco en estado Offline**.

<img width="1083" height="144" alt="image" src="https://github.com/user-attachments/assets/285513c5-c75c-488c-a35c-4cfda1ea0434" />

<img width="1298" height="324" alt="image" src="https://github.com/user-attachments/assets/c9fb5c2b-32e8-4d98-89db-60e81fda79d0" />

Debido a que el RAID 5 únicamente tiene tolerancia para soportar el fallo de un solo disco simultáneamente, el volumen completo dejará de funcionar inmediatamente. Se intenta acceder nuevamente a la unidad:


---

### Paso 7: Recuperación del sistema

Se hace clic derecho sobre uno de los discos desconectados previamente y se vuelve a colocar en estado:

```text
Online
```

<img width="294" height="175" alt="image" src="https://github.com/user-attachments/assets/0b167ac8-48c3-47a8-9169-3b704a979bbe" />

El volumen inicia automáticamente el proceso de recuperación o reconstrucción de datos. Posteriormente, se vuelve a intentar el acceso a los archivos de la unidad y se comprueba que la integridad de los datos se ha mantenido correctamente.

<img width="262" height="250" alt="2026-05-19_09-51_1" src="https://github.com/user-attachments/assets/eee4bac3-8643-4905-8281-32d2472291b4" />


---

## 3. Conclusiones y observaciones

* **Distribución de paridad:** Se ha comprobado cómo el RAID 5 distribuye de manera eficiente la paridad y los datos entre todos los componentes de la matriz.
* **Tolerancia limitada:** El sistema ofrece redundancia y tolera correctamente el fallo de un único disco duro, manteniendo los servicios operativos en entornos de producción.
* **Penalización de escritura:** Debido a que la paridad se calcula y escribe automáticamente cada vez que se almacenan datos, existe una pequeña penalización en el rendimiento de escritura, aunque la lectura es muy eficiente.
* **No es un backup:** A pesar de su resistencia frente a la pérdida de una unidad, **RAID 5 no sustituye una copia de seguridad**. Si dos unidades fallan simultáneamente o se produce corrupción de datos, todos los archivos se perderán de forma irreversible. Además, el proceso de reconstrucción puede ser largo y generar estrés adicional en el resto de discos de la matriz.
* **Recomendación:** No es adecuado para entornos donde la máxima disponibilidad o protección total sean críticas. En estos casos es obligatorio combinarlo con sistemas de backup externos o valorar alternativas como RAID 6 o RAID 10.

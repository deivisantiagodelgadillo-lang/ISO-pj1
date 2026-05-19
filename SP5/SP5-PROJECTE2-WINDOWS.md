# Sprint 5: Monitoratge, Auditories i Programari Client/Servidor
# Autorización y auditorías en Windows Server

## Introducción

En esta práctica se trabaja la configuración de auditorías y autorizaciones en Windows Server. El objetivo es comprender cómo controlar los accesos al sistema, registrar la actividad de los usuarios y analizar los eventos generados mediante el Visor de eventos.

Las auditorías permiten registrar acciones importantes como:

* Inicios de sesión correctos o fallidos
* Acceso a carpetas y archivos
* Creación y eliminación de usuarios
* Ejecución de procesos

Este sistema es fundamental para mejorar la seguridad y el control de un servidor Windows.

---

# Autorización en Windows

La autorización sirve para controlar qué acciones pueden realizar los usuarios dentro del sistema.

Mediante permisos es posible decidir:

* Quién puede leer archivos
* Quién puede modificar carpetas
* Quién puede eliminar archivos
* Quién solo tiene acceso de lectura

Estos permisos se configuran desde:

```text
Propiedades → Seguridad
```

También se pueden aplicar directivas de seguridad locales para controlar el comportamiento de los usuarios y del sistema.

---

# ¿Qué son las auditorías?

Las auditorías registran actividades importantes del sistema para poder supervisar y detectar posibles accesos no autorizados.

Ejemplos:

* Quién inicia sesión
* Quién accede a una carpeta
* Quién modifica un archivo
* Quién crea o elimina usuarios

Los resultados pueden consultarse desde:

```text
eventvwr.msc
```

Algunos Event ID importantes:

| Event ID | Descripción               |
| -------- | ------------------------- |
| 4624     | Inicio de sesión correcto |
| 4625     | Inicio de sesión fallido  |
| 4663     | Acceso a objetos          |
| 4688     | Proceso iniciado          |
| 4689     | Proceso finalizado        |
| 4720     | Usuario creado            |
| 4722     | Usuario activado          |
| 4725     | Usuario desactivado       |
| 4726     | Usuario eliminado         |

---

# Parte práctica

# 1. Activar las políticas de auditoría

Primero abrimos las directivas de seguridad locales.

```text
Win + R → secpol.msc
```

Accedemos a:

```text
Directivas locales → Directiva de auditoría
```

Activamos las opciones:

* Auditar eventos de inicio de sesión
* Auditar el acceso a objetos

Configuraremos tanto:

* Correcto
* Erróneo


<img width="703" height="330" alt="2026-05-19_01-15" src="https://github.com/user-attachments/assets/b57ac884-a8e7-4dee-905c-8852829846bd" />

---

# 2. Verificar inicio de sesión correcto

Iniciamos sesión con cualquier usuario del sistema.

Después abrimos:

```text
Win + R → eventvwr.msc
```

Ruta:

```text
Registros de Windows → Seguridad
```

Buscamos el Event ID:

```text
4624
```

Este evento indica que el inicio de sesión se ha realizado correctamente.


<img width="664" height="751" alt="2026-05-19_01-16" src="https://github.com/user-attachments/assets/b711bc49-612d-4cb3-9ef2-478269302749" />


---

# 3. Crear carpeta para auditar accesos

Creamos una carpeta nueva.

Ejemplo:

```text
C:\Auditoria
```

Botón derecho sobre la carpeta:

```text
Propiedades → Seguridad → Opciones avanzadas → Auditoría
```

Añadimos el usuario:

```text
Administrador
```

Permisos:

```text
Lectura
```


<img width="763" height="511" alt="image" src="https://github.com/user-attachments/assets/0d22a3d1-cad4-4ee8-84c9-8a4acd187418" />

---

# 4. Añadir administrador con control total

Añadimos también:

```text
Administrador
```

Permisos:

```text
Control total
```

Esto permitirá realizar diferentes pruebas dentro de la carpeta.


<img width="763" height="511" alt="image" src="https://github.com/user-attachments/assets/5f06e8d8-f0df-43c0-b61c-af911102f41c" />

---

# 5. Generar Event ID 4663

Realizamos acciones dentro de la carpeta:

* Crear archivos
* Abrir archivos
* Modificar archivos
* Eliminar archivos

Después revisamos:

```text
eventvwr.msc
```

Buscamos:

```text
Event ID 4663
```

Este evento indica acceso a objetos.


<img width="814" height="684" alt="2026-05-19_01-18" src="https://github.com/user-attachments/assets/b6215f5e-287f-4220-a7f9-81518baf4fd7" />

---

# 6. Auditar seguimiento de procesos

Volvemos a:

```text
secpol.msc
```

Activamos:

```text
Auditar el seguimiento de procesos
```

Opciones:

* Correcto
* Erróneo


<img width="683" height="282" alt="2026-05-19_01-19" src="https://github.com/user-attachments/assets/9f9f2ea1-3001-4ca3-976d-f28d1b3a6ad1" />

---

# 7. Generar Event ID 4688

Abrimos un programa.

Ejemplo:

```text
Microsoft Edge
```

Después revisamos el Visor de eventos y buscamos:

```text
4688
```

Este evento indica que se ha iniciado un proceso.


<img width="827" height="697" alt="2026-05-19_01-20" src="https://github.com/user-attachments/assets/7c78d002-a495-4f4a-84a9-1b2cea98540f" />


---

# 8. Generar Event ID 4689

Cerramos Edge desde:

```text
Administrador de tareas
```

Buscamos ahora:

```text
4689
```

Este evento indica la finalización de un proceso.


<img width="822" height="691" alt="2026-05-19_01-20_1" src="https://github.com/user-attachments/assets/db82ef3e-055c-455c-86d8-ed6f76962c02" />


---

# 9. Auditar administración de cuentas

Volvemos a:

```text
secpol.msc
```

Activamos:

```text
Auditar la administración de cuentas
```

Opciones:

* Correcto
* Erróneo


<img width="681" height="291" alt="2026-05-19_01-21" src="https://github.com/user-attachments/assets/fbdfbb9f-8a8d-4e32-95de-fac942b496f4" />


---

# 10. Crear un usuario nuevo

Creamos un usuario nuevo desde:

```text
Administración de equipos → Usuarios y grupos locales
```

Ejemplo:

```text
UsuarioPrueba
```

Después revisamos el Visor de eventos.

Eventos esperados:

| Event ID | Significado      |
| -------- | ---------------- |
| 4720     | Usuario creado   |
| 4722     | Usuario activado |


<img width="823" height="721" alt="2026-05-19_01-21_1" src="https://github.com/user-attachments/assets/f3cbe9aa-9e9c-4885-8dca-d043733a5299" />


<img width="820" height="704" alt="2026-05-19_01-22" src="https://github.com/user-attachments/assets/5922c7ea-3207-4fcc-8d00-d8fb04fed28d" />


---

# 11. Desactivar el usuario

Desactivamos el usuario creado.

Buscamos:

```text
4725
```

Este evento indica que la cuenta ha sido desactivada.


<img width="823" height="711" alt="2026-05-19_01-23" src="https://github.com/user-attachments/assets/758d1556-85ee-4c62-9686-834771333cec" />


---

# 12. Eliminar el usuario

Eliminamos el usuario.

Después revisamos:

```text
4726
```

Este evento indica que la cuenta ha sido eliminada.


<img width="815" height="707" alt="2026-05-19_01-24" src="https://github.com/user-attachments/assets/58bcdd9d-bdc1-4bb5-83d5-40fb1171ff8e" />


---

# Conclusiones

Las auditorías de Windows Server permiten controlar y registrar actividades importantes del sistema. Esto ayuda a detectar accesos no autorizados, comprobar las acciones realizadas por los usuarios y aumentar la seguridad del servidor.

Mediante el Visor de eventos es posible analizar todos los eventos generados y verificar si el sistema funciona correctamente.

También es importante no activar auditorías innecesarias, ya que pueden afectar al rendimiento del sistema.

---


# Guía de Monitorización del Rendimiento en Sistemas Windows Server

### 1. Introducción a la Supervisión de Recursos
La monitorización activa de los componentes de hardware y software es un pilar fundamental para garantizar la disponibilidad, estabilidad y eficiencia operativa de un servidor Windows. Mediante el análisis de métricas clave, los administradores de sistemas pueden diagnosticar cuellos de botella, anticipar anomalías y evaluar el impacto en el rendimiento provocado por la ejecución de aplicaciones y servicios en segundo plano.

A continuación, se exponen los principales indicadores de rendimiento divididos por componentes de hardware y se detalla el procedimiento para analizarlos de manera práctica a través de las herramientas nativas del sistema operativo.

---

### 2. Métricas Fundamentales de Rendimiento

#### 2.1. Unidad Central de Procesamiento (CPU)
* **Elementos Registrados:** Muestra el conjunto completo de procesos activos junto con el porcentaje específico de capacidad de procesamiento que consumen en cada instante. Asimismo, detalla los subprocesos, servicios vinculados y estadísticas de trazabilidad como el recuento de hilos o el identificador único de proceso (PID).
* **Interpretación de Datos:** El porcentaje de CPU indica la fracción del procesador asignada a una tarea. Si un servicio mantiene de forma sostenida valores superiores al 80-90%, debe considerarse como un indicio de sobrecarga o de un fallo en la aplicación. El PID facilita la correlación del proceso con otros diagnósticos en el Visor de Eventos o en consolas PowerShell, mientras que el nombre ayuda a diferenciar ejecutables legítimos de posibles anomalías del sistema.

#### 2.2. Memoria Volátil (RAM)
* **Elementos Registrados:** Indexa la cantidad de memoria física retenida por cada proceso en ejecución. Detalla el estado global de la RAM física (libre, modificada, en uso, en espera), además del dimensionamiento del archivo de paginación (*swap*) y las incidencias de acceso a las direcciones de memoria.
* **Interpretación de Datos:** La memoria en uso es la porción física ocupada de forma instantánea por el sistema y las aplicaciones. La memoria en espera contiene datos listos para ser reutilizados rápidamente por Windows si es necesario, y la disponible es la suma de la memoria libre y la de espera. Un uso intensivo de la memoria virtual (RAM combinada con el archivo en disco) suele indicar una carencia grave de memoria física instalada.

#### 2.3. Subsistema de Disco
* **Elementos Registrados:** Identifica qué procesos están efectuando operaciones de entrada/salida (lectura y escritura) sobre las unidades de almacenamiento, el volumen de datos transferido por segundo, los tiempos de respuesta, la latencia de las operaciones y las rutas específicas de los archivos en uso.
* **Interpretación de Datos:** La velocidad de lectura/escritura (expresada en Bytes por segundo) alerta sobre procesos con una alta dependencia del disco. Un tiempo de respuesta que supere de manera continua el umbral de los 20-30 ms denota problemas de rendimiento en la unidad. Si la cola de disco es elevada, significa que el hardware es incapaz de atender las peticiones al mismo ritmo que se generan, lo que provoca la ralentización general del servidor.

#### 2.4. Interfaz de Red
* **Elementos Registrados:** Monitoriza las aplicaciones que se encuentran transmitiendo o recibiendo tramas de datos a través de las tarjetas de red. Detalla los puertos de comunicación locales y remotos empleados, las direcciones IP de destino y el volumen total de bytes transferidos por segundo, tanto en envío como en recepción ($Tx$ y $Rx$).
* **Interpretación de Datos:** El porcentaje de utilización de la red evalúa el estado de ocupación de la línea respecto a su ancho de banda total. La lista de puertos ayuda a diagnosticar qué servicios están activos (por ejemplo, el puerto 80 para HTTP o el 443 para HTTPS), mientras que la identificación de las IP remotas y las conexiones activas resulta crucial para auditar posibles flujos de datos sospechosos o tráfico hacia destinos no deseados.

---

### 3. Procedimientos Prácticos de Monitorización

#### Paso 1: Acceso al Administrador de Tareas
Para realizar una primera aproximación al consumo de recursos en tiempo real, iniciamos la utilidad nativa del sistema operativo presionando la combinación de teclas `Ctrl + Shift + Esc`. Dentro de este entorno, en la pestaña principal, podremos consultar el gasto de recursos distribuido de forma granular por aplicaciones, procesos en segundo plano y servicios.

![image](https://github.com/user-attachments/assets/1c0008c0-d685-487f-bd75-818c6c63cf74)

#### Paso 2: Monitorización de la Gráfica de Rendimiento de CPU y Memoria
Para disponer de una perspectiva histórica y visual del uso de la infraestructura, nos desplazamos hacia la pestaña "Rendimiento" de la misma herramienta. Desde este panel podemos analizar el comportamiento y la tendencia tanto de la CPU como de la memoria RAM y los discos.

![image](https://github.com/user-attachments/assets/bc87c7be-d63b-4da7-a023-f5b88411fc5f)

![image](https://github.com/user-attachments/assets/45cd2924-c524-4bcc-a14f-32ff170d75a3)

![image](https://github.com/user-attachments/assets/93513f2b-d77b-4445-8320-d22ebc773ba5)

![image](https://github.com/user-attachments/assets/7fd15606-e776-468e-a20e-feba493eda92)

![image](https://github.com/user-attachments/assets/8c17e37a-467c-454a-8cf3-ddff23549304)

#### Paso 3: Diagnóstico Detallado con el Monitor de Recursos
Cuando se requiere un análisis mucho más exhaustivo y minucioso que supere el nivel de detalle aportado por el Administrador de Tareas, recurrimos a la herramienta "Monitor de recursos" (accesible mediante el comando `resmon` o desde la propia pestaña de Rendimiento). Esta utilidad se organiza mediante pestañas dedicadas exclusivamente a cada uno de los componentes de hardware analizados anteriormente, permitiendo ver qué archivos o direcciones IP exactas está tocando cada proceso.

![image](https://github.com/user-attachments/assets/beff16cc-7152-43c1-b275-3fa8a8c4eb8d)

![image](https://github.com/user-attachments/assets/98649c2e-069d-4e76-ba83-6fae3fc70798)

![image](https://github.com/user-attachments/assets/95ffc0b7-3c2d-4174-b655-76c32c35a31d)

![image](https://github.com/user-attachments/assets/54bad642-c4ad-4d3e-a63e-e9c2340ca34f)

![image](https://github.com/user-attachments/assets/67b7aaca-872f-4773-8d2c-9310ae3e6dba)

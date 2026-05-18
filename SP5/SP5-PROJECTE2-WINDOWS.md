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

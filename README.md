![Logo Institucional](https://github.com/JonatanBogadoUNLZ/PPS-Jonatan-Bogado/blob/9952aac097aca83a1aadfc26679fc7ec57369d82/LOGO%20AZUL%20HORIZONTAL%20-%20fondo%20transparente.png)

# UNLZ — Facultad de Ingeniería
## Ingeniería Mecatrónica — README

---

# ESTACIÓN DE CALIDAD - ROBOT SCARA - CIM

**Tipo:** PPS   
**Año:** 2026 — **Cuatrimestre:** 2C  

**Carrera:** Ingeniería Mecatrónica  
**Materia / Curso:** Laboratorio de Robótica (CIM)  
**Docente / Cátedra:** GONZÁLES, Martín; HIRAK Matías; MACEDA Mauro; FRANCO Nicolás  
**Autor/es:** [ORTEGA, Karen Aldana — Legajo]

---

## Introducción / Objetivo

**Contexto (2–4 líneas):**  
El proyecto se desarrolló en el Laboratorio CIM de la Facultad de Ingeniería de la Universidad Nacional de Lomas de Zamora, un entorno didáctico que reproduce una línea de manufactura flexible mediante estaciones automatizadas y una cinta transportadora. El trabajo se concentró en la estación final, destinada a la manipulación de bandejas y a la simulación de operaciones asociadas al control de calidad.

**Problema a resolver:**  
La disposición original de la estación limitaba el alcance operativo del robot SCARA sobre los carros de la cinta y contaba con pocas posiciones disponibles para apoyar o almacenar bandejas. Además, era necesario coordinar los movimientos del manipulador con las señales provenientes del tablero central y organizar las distintas operaciones en programas reutilizables.

**Objetivo general:**  
Adecuar y programar la estación para que el robot SCARA pueda recibir, trasladar y devolver bandejas de manera coordinada, ejecutando distintas secuencias de trabajo según las señales digitales recibidas. El sistema también contempla la interacción con un robot cartesiano y un dispensador de bolillas para realizar operaciones de manipulación y simulación de inspección.


---

## Índice
- [Brief](#brief)
- [Descripción técnica](#descripción-técnica)
- [Arquitectura del sistema](#arquitectura-del-sistema)
- [Instrucciones de uso](#instrucciones-de-uso)
- [Tecnologías utilizadas](#tecnologías-utilizadas)
- [Listado de componentes](#listado-de-componentes)
- [Fotos / Videos](#fotos--videos)
- [Estructura del repositorio](#estructura-del-repositorio)
- [Autor](#autor)
- [Licencia](#licencia)

---

## Brief

**One-liner (1 frase):**  
Estación didáctica de manufactura flexible que utiliza un robot SCARA para manipular bandejas y ejecutar secuencias automatizadas coordinadas con un robot cartesiano, la cinta transportadora y un dispensador de bolillas.

**Elevator pitch (30 segundos):**  
Este proyecto Estación de Calidad — Robot SCARA — CIM (tipo PPS, 2026 — 2.º cuatrimestre) aborda la adecuación y automatización de una estación de trabajo del Laboratorio CIM. La solución combina la reorganización física del puesto, la ampliación de las posiciones porta-bandejas y la programación modular del robot SCARA. Está orientada al entorno de formación en robótica y automatización industrial, y permite ejecutar cuatro secuencias de trabajo seleccionadas mediante señales digitales del tablero central. Se implementa con un manipulador SCARA de cuatro ejes, un robot cartesiano de dos ejes, un controlador de robot y señales digitales de entrada y salida. El funcionamiento se demuestra mediante las rutinas de manipulación, alimentación de bolillas y posicionamiento de bandejas en la zona de inspección.

### Problema
- **Contexto:** Laboratorio universitario de manufactura flexible.
- **Dolor principal:** El alcance del SCARA sobre la cinta presentaba inconvenientes con la altura original de montaje y la estación disponía inicialmente de solo dos bases porta-bandejas, lo que restringía las posiciones de trabajo y almacenamiento. También era necesario organizar la coordinación entre las señales del tablero y las rutinas del robot.
- **Impacto:** Las limitaciones dificultaban la operación de la estación y la ejecución ordenada de las distintas secuencias de manipulación.

### Solución propuesta
- **Qué hace (features):**
  - Adecuación de la altura de la mesa de trabajo para mejorar el alcance del SCARA sobre los carros de la cinta.
  - Diseño, confección e impresión 3D de cuatro bases adicionales, ampliando de dos a seis las posiciones disponibles, más una base destinada al robot cartesiano.
  - Programación de funciones modulares GET y PUT para tomar y depositar bandejas en distintas posiciones.
  - Implementación de cuatro rutinas principales (R1, R2, R3 y R4), activadas mediante entradas digitales.
  - Integración de secuencias de manipulación de recipientes y alimentación de bolillas en las rutinas R3 y R4.
  - Traslado de bandejas al área ubicada debajo de la cámara mediante la interacción con el robot cartesiano.
- **Cómo lo hace (alto nivel):** El tablero central envía una señal digital asociada al carro que llega a la estación. El controlador del SCARA identifica la entrada activa y ejecuta la rutina correspondiente. El robot manipula las bandejas mediante posiciones previamente registradas, interactúa con las bases y, cuando corresponde, con el dispensador y el robot cartesiano. Al finalizar, envía una señal de salida al sistema central para indicar que la secuencia terminó.
- **Valor diferencial:** La programación modular permite reutilizar movimientos de toma y depósito, mientras que las cuatro rutinas principales organizan distintas operaciones sin repetir toda la secuencia de movimientos en cada programa. La ampliación de las bases aumenta la flexibilidad de uso de la estación.

### Alcance
**Incluye:**
- Adecuación física de la altura de la mesa de trabajo.
-Incorporación de cuatro bases porta-bandejas impresas en 3D y una base adicional para el robot cartesiano.
-Registro de posiciones del SCARA en el vector CIM2[] y utilización de los vectores TESTB[] y AUX[].
-Programación del programa principal RUT, las rutinas R1 a R4 y las subrutinas de manipulación y alimentación.
-Coordinación mediante entradas digitales 9, 10, 11 y 12, y salidas digitales 11 y 2.
-Manipulación de bandejas y recipientes, dosificación de bolillas y posicionamiento de bandejas bajo la cámara.

**No incluye (por ahora):**
- Inspección visual automática mediante la cámara: la cámara analógica de la estación se encontraba fuera de funcionamiento.
-Desarrollo de un sistema de visión artificial o de un algoritmo de clasificación de piezas.
-Modificación del sistema general de transporte de toda la línea CIM.
-Integración de los otros robots Yaskawa de seis ejes del laboratorio.

### Estado del proyecto
- **Madurez:** Prototipo funcional desarrollado y programado en el entorno físico del Laboratorio CIM. El informe documenta las adecuaciones y las rutinas implementadas; no presenta métricas cuantitativas de rendimiento.
- **Qué funciona hoy:**
- Adecuación de la altura de la mesa y ampliación de las posiciones porta-bandejas.
-Funciones GET y PUT para las distintas posiciones.
-Programa principal de espera y activación de las cuatro rutinas.
-Secuencias de manipulación, traslado al robot cartesiano y alimentación de bolillas.
-Señalización de finalización de las rutinas mediante la salida digital 11.
- **Próximos pasos:** 
-Documentar en el repositorio los archivos originales de los programas del controlador, si están disponibles.
-Incorporar planos, archivos CAD y archivos de impresión 3D de las bases.
-Registrar pruebas de funcionamiento y tiempos de ciclo.
-Evaluar la recuperación o sustitución de la cámara para implementar una inspección visual efectiva.

### Demo rápida
- **Video / GIF:** [link o ruta en MULTIMEDIA]
- **Instrucciones express (2 minutos):**
  1) Verificar que la estación, el SCARA, el robot cartesiano y el sistema de señales estén habilitados.
  2) Desde el tablero central, seleccionar el carro/secuencia que corresponda para activar una de las entradas 9 a 12.
  3) Observar la ejecución de la rutina correspondiente y la señal de finalización por la salida 11.

---

## Descripción técnica
La estación corresponde a la etapa final de la línea de manufactura flexible del Laboratorio CIM. Está montada junto a la cinta transportadora y utiliza un manipulador SCARA de cuatro ejes para retirar bandejas de los carros, trasladarlas entre distintas bases de trabajo y devolverlas al transporte. Un robot cartesiano de dos ejes permite posicionar las bandejas en la zona ubicada debajo de una cámara, simulando el puesto de inspección final.

Como primera tarea se modificó la altura de la mesa donde están montados los manipuladores. La configuración original impedía que el SCARA alcanzara correctamente los carros de la cinta sin exceder su límite operativo. Luego se confeccionaron e imprimieron cuatro bases porta-bandejas adicionales. De esta manera, las posiciones disponibles pasaron de dos a seis, y se agregó una base para el robot cartesiano.

La programación se organizó en funciones reutilizables. Para cada operación de toma (GET) o depósito (PUT) se utilizan posiciones previamente registradas en el controlador. El vector CIM2[] almacena puntos del SCARA correspondientes a la cinta, las bases laterales, las bases de mesa y la zona del robot cartesiano. Cada operación de manipulación contempla una posición superior, una posición de aproximación o seguridad y una posición final de agarre o depósito. También se utilizan los vectores TESTB[], para puntos asociados al robot cartesiano y la zona de inspección, y AUX[], para la manipulación del recipiente y la aproximación al dispensador.

El programa principal RUT inicia las cuatro rutinas y deja el sistema a la espera de señales. Las entradas digitales 9, 10, 11 y 12 activan respectivamente las rutinas R1, R2, R3 y R4. Para evitar movimientos simultáneos incompatibles, la rutina activada detiene las restantes durante su ejecución. Al terminar, se activa brevemente la salida digital 11 para informar la finalización y se vuelve al estado de espera.
- R1: toma la bandeja del carro, la deposita en el robot cartesiano, posiciona la bandeja debajo de la cámara durante un tiempo de espera y luego la devuelve al carro.
- R2: intercambia bandejas entre el carro de la cinta y las bases laterales.
- R3: toma la bandeja, la deposita en una base de trabajo, retira el recipiente, lo lleva al dispensador y solicita la cantidad de bolillas. Luego devuelve el recipiente a la bandeja, traslada la bandeja a la zona de inspección y finalmente la devuelve a la cinta.
- R4: realiza una secuencia similar a R3, pero utiliza la rutina de alimentación configurada para una cantidad fija de dos bolillas antes de llevar la bandeja a la zona de inspección.
El dispensador se acciona mediante la salida digital 2 y utiliza la entrada digital 2 para registrar los pulsos asociados al paso de las bolillas. La cámara analógica se encontraba fuera de funcionamiento durante la práctica: por lo tanto, el posicionamiento debajo de ella y la espera programada representan una simulación del tiempo de inspección, no una evaluación visual automática de las piezas.

---

## Arquitectura del sistema

**Entradas (sensores / señales):**
- IN 9: activa la rutina R1.
- IN 10: activa la rutina R2.
- IN 11: activa la rutina R3.
- IN 12: activa la rutina R4.
- IN 2: recibe los pulsos del sensor asociado al paso de bolillas en el dispensador.
- Señales provenientes del tablero central de control, asociadas a la detección y selección de los carros en la estación.

**Procesamiento / Control:**
- Controlador del robot SCARA y programas desarrollados en el lenguaje del controlador.
- Programa principal RUT y subrutinas R1, R2, R3 y R4.
- Funciones reutilizables GETxx y PUTxx para tomar y depositar bandejas.
- Subrutinas GB22, PB22, ALIMB, ALIM2, BOLIT y BOL2 para manipular el recipiente y controlar la alimentación de bolillas.
- Vectores de posiciones CIM2[], TESTB[] y AUX[].

**Salidas (actuadores / señales):**
- OUT 11: informa al sistema central que finalizó la rutina del SCARA.
- OUT 2: acciona el dispensador de bolillas.
- Gripper del SCARA para tomar y liberar bandejas y recipientes.
- Movimientos del robot cartesiano para posicionar la bandeja en la zona de inspección.
- Accionamiento neumático de los pistones de la estación, coordinado desde el sistema de control central.

---

## Instrucciones de uso

### Requisitos previos
Acceso a la estación física del Laboratorio CIM.
Robot SCARA, controlador, gripper, robot cartesiano y tablero central disponibles.
Sistema de cinta transportadora y señales de estación habilitados.
Dispensador y señal de conteo disponibles para ejecutar las rutinas R3 y R4.
Programas y posiciones correspondientes cargados en el controlador.
Teach pendant y terminal de programación compatibles con el controlador instalado.

### Instalación / Puesta en marcha
Este proyecto fue desarrollado sobre equipamiento físico del Laboratorio CIM; no es una aplicación que pueda ejecutarse únicamente clonando el repositorio.
1. Clonar o descargar el repositorio para consultar la documentación y los archivos disponibles.
2. Verificar que se dispone del robot, controlador y periféricos compatibles con la estación.
3. Cargar en el controlador los programas y los vectores de posiciones correspondientes. Las posiciones deben estar enseñadas y verificadas en la estación física.
4. Comprobar las señales de entrada y salida con el sistema de control central antes de ejecutar una rutina.
5. Realizar una prueba supervisada de cada secuencia y verificar el retorno del sistema al estado de espera.

### Uso
- **Modo normal:** el programa RUT permanece a la espera de una señal. Según la entrada activada (9, 10, 11 o 12), se ejecuta R1, R2, R3 o R4. Al finalizar, se activa OUT 11 y el programa vuelve a esperar una nueva orden.
- Alimentación de bolillas: R3 solicita la cantidad a dispensar mediante BOLIT; R4 utiliza BOL2, configurada para dos unidades.
- **Calibración:** las posiciones se registran desde el teach pendant en los vectores CIM2[], TESTB[] y AUX[]. Cualquier modificación debe verificarse en el puesto real antes de ejecutar movimientos automáticos.
- **Notas:** no ejecutar el robot sin supervisión y sin comprobar que el área de trabajo esté despejada. Verificar los puntos de aproximación y seguridad, el estado del gripper y la coordinación con la cinta y los pistones. La cámara no realiza una inspección automática porque se encontraba fuera de funcionamiento.

### Troubleshooting (opcional)
- El programa no inicia una rutina: verificar que el programa RUT esté ejecutándose y que llegue la entrada digital correspondiente (IN 9, 10, 11 o 12).
- El robot no alcanza correctamente una posición: revisar el registro de puntos y las condiciones físicas de montaje; no modificar posiciones sin comprobarlas en la estación.
- El dispensador no completa el conteo: verificar la señal de salida OUT 2 y los pulsos recibidos por IN 2.
- La cinta no continúa luego de una rutina: comprobar que se genere el pulso de finalización mediante OUT 11 y que el tablero central reciba la señal.

---

## Tecnologías utilizadas
- **Robótica / Control:** manipulador industrial SCARA de cuatro ejes; robot cartesiano de dos ejes; controlador de robot y teach pendant.
- **Electrónica:** entradas y salidas digitales; sensor de proximidad inductivo NPN en la estación; señal de conteo del dispensador; tablero central de control.
- Actuación: gripper del SCARA, dispensador de bolillas accionado por motor y accionamiento neumático de pistones.
- **Programación:** lenguaje propio del controlador del robot, con programas, subrutinas, llamadas a funciones, temporizaciones, condiciones de espera y contadores.
- **Plataformas / Tools:** diseño y fabricación mediante impresión 3D de bases porta-bandejas.

---

## Listado de componentes

| Componente | Cantidad | Modelo / Especificación | Función |
|---|---:|---|---|
| Robot industrial SCARA | 1 | 4 ejes | Manipulación de bandejas y recipientes |
| Robot cartesiano | 1 | 2 ejes | 	Posicionamiento de bandejas bajo la cámara |
| Bases porta-bandejas | 6 posiciones | Cuatro bases nuevas impresas en 3D, más las dos existentes en la cinta |Apoyo y almacenamiento de bandejas |
| Cámara | 1 | Analógica; fuera de funcionamiento durante la práctica | Ubicación de referencia para la simulación de inspección |
| Dispensador de bolillas | 1 | Accionado por motor | Dosificación de bolillas |
| Gripper | 1 | Integrado al SCARA | Sujeción y liberación de bandejas y recipientes |


---

## Fotos / Videos
<img src="Multimedia (Imágenes y videos)/Anexo1_Estación_SCARA.png" alt="Estación SCARA" width="600">
<img src="Multimedia (Imágenes y videos)/Anexo2_Bases_de_trabajo.png" alt="Bases de trabajo" width="600">
<img src="Multimedia (Imágenes y videos)/Anexo3_Programa_principal.jpg" alt="Programa principal" width="600">
<img src="Multimedia (Imágenes y videos)/Anexo4_Posición_del_recipiente_rutinas_R3_R4.png" alt="Posición del recipiente rutinas R3/R4" width="600">
<img src="Multimedia (Imágenes y videos)/Anexo5_Dispensador_de_bolitas.png" alt="Dispensador de bolitas" width="600">

*[Ver Video Programa R1](Multimedia%20(Imágenes%20y%20videos)/Programa_R1.mp4)
*[Ver Video Programa R2](Multimedia%20(Imágenes%20y%20videos)/Programa_R2.mp4)
*[Ver Video Programa R3 y R4](Multimedia%20(Imágenes%20y%20videos)/Programa_R3_y_R4.mp4)

---

## Estructura del repositorio
- `CODIGO/` — Código fuente del proyecto.
- `MULTIMEDIA/` — Imágenes y videos.
- `PLANOS/` — Esquemáticos y diagramas.
- `DATASHEET/` — Hojas de datos y especificaciones.
- `INFORMES/` — Informes, Gantt, manuales, PDFs.

---

## Autor
**ORTEGA, Karen Aldana**  

---

## Licencia
uso académico

---

## About (descripción corta del repositorio)

Usar este texto (o similar) en el campo **About** de GitHub:

**PPS — ESTACIÓN DE CALIDAD - ROBOT SCARA - CIM — FI-UNLZ — 2026 2C — ORTEGA, Karen**

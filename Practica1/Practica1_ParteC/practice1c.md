
# Práctica 1C. Mediciones de potencia y frecuencia

### Integrantes
- **Danny Carolina Sierra Téllez** - 2220409
- **Michel Dayanna Salazar Gómez** - 2214194

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

### Fecha
07 de marzo de 2025

---
## Contenido

### Resumen
En esta práctica, se utilizó el sofware GNU Radio, así como equipos tales como el osciloscopio, el analizador de espectros y el USRP 2920. Se empezó a familiarizar con conceptos básicos sobre el uso de estas herramientas, mediante la simulación de flujogramas, así como la integración de los equipos para tomar medidas en el dominio del tiempo y frecuencia. Dentro de las medidas claves en comunicaciones, se encuentran el ancho de banda, relación señal a ruido, piso de ruido, potencia y diferentes análisis que permiten ver la variación de la señal, ruido y transmisión de la misma; confirmando el comportamiento teórico esperado.


**Palabras clave:** GNU Radio, Espectro de Frecuencia, USRP 2920. 

### Introducción
En comunicaciones es clave el procesamiento y análisis de las señales para garantizar un buen proceso de transmisión y recepción de mensajes. Dentro de las medidas que están directamente relacionadas a estas, se destacan: la potencia, el piso de ruido y el ancho de banda; escenciales para buscar mejoras y evaluar los procesos de los sistemas de comunicación. Ahora bien, en la asignatura se hace uso de la herramienta de GNU Radio, así como de otros equipos de laboratorio como osciloscopio, analizador de espectros, antenas, radio entre otros; los cuales, permiten estudiar la relación de las medidas anteriormente mencionadas en el cambio de diferentes condiciones a señales.

## Declaración de Originalidad y Responsabilidad
Los autores de este informe certifican que el contenido aquí presentado es original y ha sido elaborado de manera independiente. Se han utilizado fuentes externas únicamente como referencia y han sido debidamente citadas.

Asimismo, los autores asumen plena responsabilidad por la información contenida en este documento. 

Uso de IA: [Indicar si se usó IA y para qué aspectos específicos, por ejemplo: "Se utilizó ChatGPT para reformular secciones del texto y verificar gramática, pero el contenido técnico fue desarrollado íntegramente por los autores."]

---
## Contenido

## **Objetivo General**

Familiarizarse con el uso de herramientas de software definido por radio (SDR) como GNU Radio, junto con equipos de medición como el USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000. Los estudiantes aprenderán a medir y analizar parámetros clave en comunicaciones, como potencia, ancho de banda, relación señal a ruido (SNR) y piso de ruido.
Analizar los resultados obtenidos y sacar conclusiones sobre el comportamiento de las señales en diferentes condiciones para elaborar el informe.

---

### Procedimiento

## **Materiales y Equipos**
- **USRP 2920**: Radio definido por software.
- **Osciloscopio R&S RTB2004**: Para visualización de señales en el dominio del tiempo y frecuencia.
- **Analizador de Espectros R&S FPC1000**: Para mediciones en el dominio de la frecuencia.
- **Computador con GNU Radio**: Para simulación y generación de señales usando el USRP 2920.
- **Cables y conectores**: Para interconexión de equipos.

---

## **Actividad 1: Revisión de Especificaciones de los Equipos**

### **Objetivo**
Familiarizarse con las especificaciones técnicas de los equipos de laboratorio y entender cómo configurarlos para realizar mediciones.

### **Procedimiento**
1. Se revisaron los manuales sobre cada uno de los equipos usados durante el desarrollo de las clases de laboratorio, con el fin de identificar especificaciones relevantes así como modo de uso, herramientas y controles de los mismos.
  
2. **Evidencia  y especificaciones Relevantes**:
   *USRP 2920*
      - Rango de frecuencia:  50MGz a 2.2GHz
      - Ganancia configurable: 0 a 31.5dB pasos de 0.5dB
      - Ancho de banda: 20M a 40MHz
      - Resolución de frecuencia: <1kHz
      - Potencia máxima de salida: 50m a 100mW
        
   *Osciloscopio R&S RTB2004*
      - Ancho de banda mínimo: 70MHz a 300MHzbus
      - Resolución vertical: 10bits
      - Tipos de mediciones: básico, horizontal, vertical, cuenta.
      - Escala vertical: 1mV a 5V
      - Tasa de muestreo: 2.5GSa/s
        
   *Analizador de Espectros R&S FPC1000*
      - Rango de frecuencia: 0 a 1GHz
      - Resolución Bw: 1Hz a 3MHz
      - Ruido de fondo: bajo -150dBm 
      - Potencia piso de ruido: <-97.88dBm

Medición Piso de ruido:
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Piso_ruido.jpeg)

### **Preguntas Orientadoras**
1. ¿Cuál es el rango de frecuencia del USRP 2920 y cómo se compara con el del analizador de espectros?
   
   El rango de frecuencia del USRP 2920 es indiscutiblemente más amplio que el del analizador de espectros, permitiendo cubrir frecuencias mayores.
   
2. ¿Qué parámetros del USRP 2920 se deben configurar para transmitir una señal en una frecuencia específica?
   
   Dentro de los parámetros a cambiar para trasnmitir a cierta señal está la frecuencia central, el ancho de banda, ganancia y tipo de modulación.
   
3. ¿Cómo se configura el osciloscopio para medir la amplitud y la frecuencia de una señal?
   
   Luego de la conexión, y ajuste a las escalas tanto horizontales como verticales sin saturar la señal. Se puede seleccionar una de las mediciones automáticas del osciloscopio para valores más precisos.
   
4. ¿Qué diferencia hay entre medir una señal en el dominio del tiempo (osciloscopio) y en el dominio de la frecuencia (analizador de espectros)?
   
   La diferencia está en que cada uno representa algo diferente, en el oscilador se vé la variación de la señal en el tiempo, permitiendo tomar valores como amplitud, transitorios o ver las formas de onda.
   Por otro lado, el analizador de espectro muestra la distribución de la señal en las frecuencias, permitiendo ver componentes como armónicos, ruido, potencia y demás.
   
5. ¿Cómo se mide el piso de ruido en el analizador de espectros? ¿Cómo afecta la frecuencia central, SPAN y RBW la medida de piso de ruido? ¿Por qué?
   
    Conectar y configurar el RBW, reducir el SPAN, la frecuencia central ya que mejoran la precisión y con ayuda de marcadores se puede observar el nivel de ruido mostrado en la pantalla. Por ejemplo un RBW mejora la detección de señales débiles pero aumenta el tiempo de respuesta o gráfico del analizador. 

*Imágenes de Evidencia..*
- Flujograma Usado:
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Flujograma.jpeg)
- Escala vertical:
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Escala%20vertical.jpeg)
- Tipos de mediciones osciloscopio:
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/TipoMedida1.jpeg)
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/TipoMedida2.jpeg)
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/TipoMedida3.jpeg)
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/TipoMedida4.jpeg)
---

## **Actividad 2: Simulación de Señales en GNU Radio**

### **Objetivo**
Generar y analizar señales en GNU Radio para entender cómo se comportan diferentes formas de onda en tiempo y frecuencia.

### **Procedimiento**  
   Primero, se inició configurando el GNU Radio cargando el diseño de flujograma propuesto en la guía de laboratorio; se ajustaron parámetros como frecuencia de muestreo y ganancia de transmisión. Luego, la señal generada se observó para el dominio del tiempo en el osciloscopio y para las frecuencias en el espectro. Además, se hicieron variaciones en tipo de dato, frecuencia, amplitud y otros para evaluar los cambios en su representación.

### **Preguntas Orientadoras**
1. ¿Cómo se puede explicar matemáticamente la diferencia entre una fuente de tipo flotante y una de tipo complejo?

Las fuentes de tipo flotnate son aquellas que matematicamente se pueden modelar como el espectro de

$V_s(t) = V_1(t) - V_2(t)$

Este modelo permite eliminar componentes de ruido comunes, mejorando la relación señal/ruido. Por otro lado, las fuentes referenciadas, también llamadas fuentes complejas, pueden verse afectadas por el ruido de su referencia. Su señal se describe como:

$V_s(t) = V_{\text{ref}} + A \cos(\omega t + \theta)$

Debido a su conexión con un punto de referencia fijo, pueden introducir ruido adicional en la señal medida.

2. ¿Cómo afecta la forma de onda a la distribución de energía (potencia) en el dominio de la frecuencia?

Afecta de diferentes formas dependiedno de la forma de onda de la señal, ya que por ejemplo para señales senoidales los espectros son concentrados, para señales rectangulares estos suelen tener espectros muy anchos y las señales que tengas tiempos cortos ocupan un mayor ancho de banda. 


3. ¿Qué sucede con la señal en el dominio del tiempo y la frecuencia si se modifican los diferentes parámetros de la fuente? ¿Lo observado corresponde a lo esperado teóricamente?

   Al realizar modificaciones,como lo es la amplitud, la frecuencia o entre otros parametros se puede comprobar de manera teorica asi como en el laboratorio los cambios que suele tener esta, debido a que los modelos se ajustan para que los valores sean lo más parecido posible, a pesar de ello existen factores que no se pueden ignorar como el ruido, que afecta directamente la señal.

   
5. ¿Cómo se relaciona la amplitud de la señal con la potencia observada en el dominio de la frecuencia?

La amplictud y la potencia estan directamente relacionados con la potencia que estan opbservados en el dominio dela frecuencia esto a traves de una relación cuadratica. Es decir, que la potencia es proporcional al cuadrado de la amplitud de la  señal. 


6. ¿Qué diferencias se observan entre una señal senoidal y una señal cuadrada en el dominio de la frecuencia?

La principal diferencia es que su respuesta en frecuencia para la señal es diferente, debido a que la señal solo tiene una frecuencia fundamental f0 sin armonicos adicionales.
Por otro lado, la señal cuadrada está compuesta por un conjunto infinito de armónicos impares, (es decir, frecuencias múltiplos impares de , cuya amplitud decrece según una relación inversamente proporcional al orden del armónico (1/n, donde n es el orden del armónico). Esto hace que su representación en el dominio de la frecuencia muestre múltiples picos correspondientes a estos armónicos, con amplitudes que disminuyen progresivamente.



### **Evidencias**
En las siguientes imagenes se puede observar el fenomeno antes mencionado. ![Primero](Primer punto/Imagenes/SCR05.PNG)


## **Actividad 3: Transmisión y Medición de Señales con el USRP 2920**

### **Objetivo**
Transmitir señales usando el USRP 2920 y medir parámetros clave como potencia, ancho de banda, piso de ruido y relación señal a ruido (SNR).

### **Procedimiento**
   Se realizaron mediciones bajo diferentes configuraciones de parámetros, con el fin de comparar los resultados de las simulaciones con las mostradas en el analizador de espectros o osciloscopio.
   
1. **Configurar el USRP 2920**:
   - Configure el flujograma en GNU Radio para transmitir una señal a través del USRP. Habilite o deshabilite los bloques correspondientes (Channel Model, Throttle, UHD: USRP Sink, Virtual Sink). Para esto seleccione el bloque deseado y presionando `E` (enable) o `D` (disable), respectivamente.
   - Identifique el bloque de frecuencia de muestreo (samp_rate) y observe el efecto de cambiar su valor (e.g. 10 kHz).
   - Configure la frecuencia de muestreo (samp_rate) en 1 MHz.
   - Verifique el efecto de modificar la frecuencia y ganancia del USRP. 

2. **Medición con el Analizador de Espectros**:
   - Conecte la salida del USRP al analizador de espectros.
   - Mida el piso de ruido normalizado a la frecuencia de portadora que va a utilizar.
   - Compare el espectro de la señal observada en el analizador de espectros con la observada en la pantalla de simulación. Tenga en cuenta que el radio (USRP) equivale al diagrama de bloques mostrado en la figura.
1. Configurar USRP 2920.
       
   A.  Analizador de espectros Piso de ruido a 700MHz
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Espectro_piso%20de%20ruido%20norm.jpeg)
  - Pantalla simulación Piso de ruido a fc = 700MHz
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Sim_Piso%20de%20ruido%20norma.jpeg)

   B.  Analizador de espectros frecuencia de muestreo diferente.

   /1MHz (FOTO 1 MEMORIA 3 MARZO)
   /10kHz (FOTO 2 MEMORIA 3 MARZO)

   ANALISIS DE MODIFICAR FC Y GANANCIA...


2. Medición analizador de espectros.

   A.  Medición piso de ruido normalizado a Fc = 100MHz
   
  - Analizador de espectros.
   / (FOTO 3 MEMORIA 3 MARZO)
   
  - Pantalla simulación
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Pto2_A_Piso%20de%20ruido%20norm%20sim.jpeg)

  B. Variación en dominio de la frecuencia.
  
  - Analizador de espectros.
   / (FOTO 4 MEMORIA 3 MARZO)
   
  - Pantalla simulación
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Variaci%C3%B3n_PTO2_B_sim.jpeg)

  C. Potencia
  
  - Analizador de espectros.
  ![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/PTO2_C_ESP_pwtrans_SIM.jpeg)
   
  - Pantalla simulación
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/PTO2_C_pwtransSIM.jpeg)


  D. Ancho de Banda
 /SENOIDAL
 /TRIANGULAR

 E. ANTENA
<img src="qam_modulator.png" alt="QAM Modulator" width="400">
     
   - Analice y valide los resultados en el dominio de la frecuencia si se modifica:
     - el tipo de dato de la fuente (compleja o flotante)
     - la forma de onda 
     - la frecuencia y fase de la señal
     - la amplitud de la señal generada.
   - Mida potencia de la señal transmitida y ancho de banda de diferentes señales generadas.

   ultima vez!!!!!
   - Conecte una antena apropiada a la entrada del analizador de espectros y observe el espectro de una señal FM (las estaciones FM se sitúan entre los 88 MHz y 108 MHz). Mida su ancho de banda y relación señal a ruido. 
   - Determinar la máxima potencia de transmisión.
   - Evalúe la respuesta en frecuencia del canal midiendo los cambios de ganancia del sistema cuando varía la frecuencia de portadora.
   - Compare los resultados de transmitir usando un cable y usando antenas.

4. **Medición con el Osciloscopio**:
   - Analice y valide los resultados en el dominio del tiempo si se modifica:
     - el tipo de dato de la fuente (compleja o flotante)
     - la forma de onda 
     - la frecuencia y fase de la señal
     - la amplitud de la señal generada.
  - Contraste estos resultados con los obtenidos con el analizador de espectros.

5. **Cálculo de la Relación Señal a Ruido (SNR)**:
   - Usar las mediciones de potencia y piso de ruido para calcular la SNR de algunas de las señales generadas.
   - Anotar el valor de la SNR en dB.

### **Preguntas Orientadoras**
1. ¿Cómo se configura el USRP 2920 para transmitir una señal en una frecuencia específica?
2. ¿Qué parámetros del flujograma afectan la potencia de la señal transmitida?
3. ¿Cómo se mide el ancho de banda de la señal transmitida en el analizador de espectros?
4. ¿Cómo se calcula la relación señal a ruido (SNR) a partir de las mediciones de potencia y piso de ruido?
5. ¿Qué diferencias se observan en las mediciones de potencia cuando se varía la ganancia del USRP?
6. ¿Es posible medir o estimar la potencia de la señal observada en el osciloscopio? ¿Por qué?

### **Evidencia**
- Capturas de pantalla de señales generadas en el dominio del tiempo y la frecuencia que evidencien las principales comparaciones realizadas.
- Captura de la señal FM usada para medición de ancho de banda.

---

## **Actividad 4: Análisis de Resultados y Conclusiones**

### **Para la Elaboración del Informe**
1. **Comparar Resultados**:
   - Compare los resultados obtenidos en las simulaciones y las transmisiones reales.
   - Discuta las diferencias entre las mediciones realizadas con el osciloscopio y el analizador de espectros.

2. **Reflexionar sobre la SNR**:
   - Analice la importancia de la relación señal a ruido (SNR) en las comunicaciones inalámbricas.
   - Discuta cómo el piso de ruido afecta la capacidad de detectar señales débiles.
La SNR es importante debido a que es de lo más usado en comunicaciones inalambricas, ya que afecta directamente a la señal, la capacidad de transmision de datos y la eficiencia del sistema.

3. **Conclusiones**:

Las limitaciones en el laboratorio pueden deberse a diversos fenómenos que generan ruido, lo que perturba la señal y afecta la precisión de las mediciones. Esto puede provocar discrepancias entre los resultados experimentales y los análisis teóricos.
Para mejorar la precisión de las mediciones, es fundamental minimizar el ruido que afecta la señal, por ejemplo, mediante el uso de cables con mejor blindaje o técnicas de filtrado adecuadas. Además, contar con un ancho de banda más amplio permitiría analizar el espectro de la señal con mayor detalle, especialmente en frecuencias más altas.


### **Preguntas Orientadoras**
1. ¿Qué conclusiones se pueden obtener sobre la relación entre la potencia de la señal y la calidad de la comunicación?
2. ¿Cómo afecta el piso de ruido a la capacidad de detectar señales débiles?
3. ¿Qué limitaciones tienen los equipos utilizados en términos de ancho de banda y precisión en las mediciones?
4. ¿Cómo se pueden mejorar las mediciones de señal en un entorno con alto nivel de ruido?
5. ¿Qué aplicaciones prácticas tienen las mediciones de potencia y ancho de banda en sistemas de comunicaciones reales?
6. ¿Cómo se puede medir la respuesta en frecuencia de un canal alámbrico?
7. ¿Cómo se puede obtener un modelo sencillo de las pérdidas (_pathloss_) en un canal inalámbrico?

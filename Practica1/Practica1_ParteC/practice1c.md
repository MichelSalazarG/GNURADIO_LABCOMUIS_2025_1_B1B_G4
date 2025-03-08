
# Práctica 1C. Mediciones de potencia y frecuencia

### Integrantes
- **PRIMER INTEGRANTE** - Código
- **Michel Dayanna Salazar Gómez** - 2214194

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

### Fecha
07 de marzo de 2025

---
## **Objetivo General**
Familiarizarse con el uso de herramientas de software definido por radio (SDR) como GNU Radio, junto con equipos de medición como el USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000. Los estudiantes aprenderán a medir y analizar parámetros clave en comunicaciones, como potencia, ancho de banda, relación señal a ruido (SNR) y piso de ruido.
Analizar los resultados obtenidos y sacar conclusiones sobre el comportamiento de las señales en diferentes condiciones para elaborar el informe.

---
## Contenido

### Resumen
Descripción en no más de 150 palabras del contenido de la práctica. Debe ser conciso y brindar una idea clara sobre el trabajo realizado y sus conclusiones.

**Palabras clave:** de 2 a 5 palabras clave. 

### Introducción
Cada práctica contará con preguntas orientadoras para la elaboración de la introducción. Por ejemplo: 
- ¿Qué tan importante es la teoría de muestreo en el procesamiento de señales?
- ¿Cuáles son los principales potenciales de GNURADIO en el laboratorio de comunicaciones?
- ¿Qué pasa cuando se alcanza el límite de Nyquist?
- ¿Qué tan alta debe ser la relación entre la frecuencia de muestreo y la frecuencia de la señal para visualizar la señal correctamente?
- ¿Cuándo es importante interpolar una señal?
- ¿Cuándo es importante diezmar una señal?
- ¿Qué pasa cuando se asigna una frecuencia de muestreo inadecuada?

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
1. **Revisar Manuales y Verificar Equipos**:
   - Revisar las especificaciones de los equipos de laboratorio (USRP 2920, Osciloscopio R&S RTB2004 y Analizador de Espectros R&S FPC1000).
   - Identificar las principales funciones y controles de los equipos.

2. **Seleccionar Especificaciones Relevantes**:
   - Seleccionar las **5 especificaciones** que consideren **más relevantes** de cada equipo. 

3. **Configuración de los Equipos**:
   - **USRP 2920**: Identificar el rango de frecuencia y ganancia configurable del radio. Para esto, conecte la alimentación y el cable de red al radio, y desde un terminal (Ctrl + Alt + T) ejecute el comando `uhd_usrp_probe`.
   - **Osciloscopio R&S RTB2004**: Identificar el ancho de banda máximo, resolución vertical y tipos de mediciones soportadas.
   - **Analizador de Espectros R&S FPC1000**: Identificar el rango de frecuencia, resolución y figura de ruido.

### **Preguntas Orientadoras**
1. ¿Cuál es el rango de frecuencia del USRP 2920 y cómo se compara con el del analizador de espectros?
2. ¿Qué parámetros del USRP 2920 se deben configurar para transmitir una señal en una frecuencia específica?
3. ¿Cómo se configura el osciloscopio para medir la amplitud y la frecuencia de una señal?
4. ¿Qué diferencia hay entre medir una señal en el dominio del tiempo (osciloscopio) y en el dominio de la frecuencia (analizador de espectros)?
5. ¿Cómo se mide el piso de ruido en el analizador de espectros? ¿Cómo afecta la frecuencia central, SPAN y RBW la medida de piso de ruido? ¿Por qué?

### **Evidencia**
- Lista con las 5 especificaciones más relevantes de cada equipo.
- Realice una medición de piso de ruido normalizado.

---

## **Actividad 2: Simulación de Señales en GNU Radio**

### **Objetivo**
Generar y analizar señales en GNU Radio para entender cómo se comportan diferentes formas de onda en tiempo y frecuencia.

### **Procedimiento**  

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
1. **Configurar el USRP 2920**:
   - Configure el flujograma en GNU Radio para transmitir una señal a través del USRP. Habilite o deshabilite los bloques correspondientes (Channel Model, Throttle, UHD: USRP Sink, Virtual Sink). Para esto seleccione el bloque deseado y presionando `E` (enable) o `D` (disable), respectivamente.
   - Identifique el bloque de frecuencia de muestreo (samp_rate) y observe el efecto de cambiar su valor (e.g. 10 kHz).
   - Configure la frecuencia de muestreo (samp_rate) en 1 MHz.
   - Verifique el efecto de modificar la frecuencia y ganancia del USRP. 

2. **Medición con el Analizador de Espectros**:
   - Conecte la salida del USRP al analizador de espectros.
   - Mida el piso de ruido normalizado a la frecuencia de portadora que va a utilizar.
   - Compare el espectro de la señal observada en el analizador de espectros con la observada en la pantalla de simulación. Tenga en cuenta que el radio (USRP) equivale al diagrama de bloques mostrado en la figura.

<img src="qam_modulator.png" alt="QAM Modulator" width="400">
     
   - Analice y valide los resultados en el dominio de la frecuencia si se modifica:
     - el tipo de dato de la fuente (compleja o flotante)
     - la forma de onda 
     - la frecuencia y fase de la señal
     - la amplitud de la señal generada.
   - Mida potencia de la señal transmitida y ancho de banda de diferentes señales generadas.
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


# Práctica 1. Reconocimiento de equipos, GNU Radio, Mediciones de potencia y frecuencia

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

Uso de IA: Se utilizó para reformular ciertas secciones del texto, verificar gramática, y optimizar la redacción general. Sin embargo, el contenido técnico, análisis y las conclusiones del informe, fueron desarrollados por los autores.

---
## Contenido

## **Objetivo General**

Familiarizarse con el uso de herramientas de software definido por radio (SDR) como GNU Radio, junto con equipos de medición como el USRP 2920, el osciloscopio R&S RTB2004 y el analizador de espectros R&S FPC1000. Aprender a medir y analizar parámetros clave en comunicaciones, como potencia, ancho de banda, relación señal a ruido (SNR) y piso de ruido.

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

Las formas de las ondas influyen mucho en cómo se divide la energía en el área de frecuencias. Esto ocurre debido a que cada tipo de señal posee rasgos distintos en su espectro. Un ejemplo de ello, son aquellas señales que como el Seno tienen espectros en frecuencias precisas, ͏sin embargo͏, las señales que son rectangulares tienden a tener espectros más ampl͏ios, con partes de frecuencias que cubren un rango más gran͏de. Además, la͏s señales quíen duran menos su͏elen ocupar un ancho de banda mayor͏ en el ámbito de ͏frecu͏en͏cia.͏

3. ¿Qué sucede con la señal en el dominio del tiempo y la frecuencia si se modifican los diferentes parámetros de la fuente? ¿Lo observado corresponde a lo esperado teóricamente?

   Al realizar modificaciones,como lo es la amplitud, la frecuencia o entre otros parametros se puede comprobar de manera teorica asi como en el laboratorio los cambios que suele tener esta, debido a que los modelos se ajustan para que los valores sean lo más parecido posible, a pesar de ello existen factores que no se pueden ignorar como el ruido, que afecta directamente la señal.

   
5. ¿Cómo se relaciona la amplitud de la señal con la potencia observada en el dominio de la frecuencia?

La potencia de la señal y su amplitud están directamente relacionados en el dominio de la frecuencia. Esta relación surge de una relación cuadrática, esto significa que la potencia es proporcional al cuadrado de la amplitud de la señal. Es decir, que si la amplitud aumenta la señal también aumenta, la potencia que se observa en el dominio de la frecuencia incrementa de acuerdo con el cuadrado de ese cambio dado. 


6. ¿Qué diferencias se observan entre una señal senoidal y una señal cuadrada en el dominio de la frecuencia?

La principal diferencia es que su respuesta en frecuencia para la señal es diferente, debido a que la señal solo tiene una frecuencia fundamental f0 sin armonicos adicionales.
Por otro lado, la señal cuadrada está compuesta por un conjunto infinito de armónicos impares, (es decir, frecuencias múltiplos impares de , cuya amplitud decrece según una relación inversamente proporcional al orden del armónico (1/n, donde n es el orden del armónico). Esto hace que su representación en el dominio de la frecuencia muestre múltiples picos correspondientes a estos armónicos, con amplitudes que disminuyen progresivamente.



### **Evidencias**
En las siguientes imagenes se puede observar como en GNU radio se pueden ajustar los parametros antes mencionados.
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/GNURADIO.png)



## **Actividad 3: Transmisión y Medición de Señales con el USRP 2920** 

### **Objetivo**
Transmitir señales usando el USRP 2920 y medir parámetros clave como potencia, ancho de banda, piso de ruido y relación señal a ruido (SNR).

### **Procedimiento**
   Se realizaron mediciones bajo diferentes configuraciones de parámetros, con el fin de comparar los resultados de las simulaciones con las mostradas en el analizador de espectros o osciloscopio.

### **Evidencia y cambios realizados**  
  
1. *Configurar USRP 2920*
       
   A.  Analizador de espectros Piso de ruido a 700MHz
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Espectro_piso%20de%20ruido%20norm.jpeg)
  - Pantalla simulación Piso de ruido a fc = 700MHz
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Sim_Piso%20de%20ruido%20norma.jpeg)

   B.  Analizador de espectros frecuencia de muestreo diferente.

   - Sam_rate = 1MHz
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Measurement0062.png)
      
   - Sam_rate = 10kHz
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Measurement0063.png) 

   **ANALISIS DE MODIFICAR FC Y GANANCIA...**


2. *Medición analizador de espectros*

   A.  Medición piso de ruido normalizado a Fc = 100MHz
   
  - Analizador de espectros.
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Measurement0064.png) 
   
  - Pantalla simulación
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Pto2_A_Piso%20de%20ruido%20norm%20sim.jpeg)

  B. Variación en dominio de la frecuencia.
  
  - Analizador de espectros.
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Measurement0065.png)
   
  - Pantalla simulación
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Variaci%C3%B3n_PTO2_B_sim.jpeg)

  C. Potencia
  
  - Analizador de espectros.
  ![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/PTO2_C_ESP_pwtrans_SIM.jpeg)
   
  - Pantalla simulación
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/PTO2_C_pwtransSIM.jpeg)


  D. Ancho de Banda
 /SENOIDAL 
 ![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Measurement0069.png)   
 /TRIANGULAR
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Measurement0068.png)   

**ANALIZAR**
 E. ANTENA
 
   I) Ancho de Banda.
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Measurement0073.png)   
   
   II) Relación señal a Ruido.
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/Measurement0074.png)  
   
 3. *Medición osciloscopio*
    
- Señal Seno:
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/SCR03.PNG)
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/OS03_sim_cap.jpeg)

- Señal Cuadrada:
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/SCR04.PNG)
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/OS04_sim.jpeg)

- Señal cos:
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/SCR05.PNG)
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/OS05_Sim.jpeg)

- Señal cos:
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/SCR06.PNG)
![](https://github.com/MichelSalazarG/GNURADIO_LABCOMUIS_2025_1_B1B_G4/blob/main/Practica1/Primer%20punto/Imagenes/OS06_sim.jpeg)

    
### **Preguntas Orientadoras**
1. ¿Cómo se configura el USRP 2920 para transmitir una señal en una frecuencia específica?

Para configurar el USRP 2920 a una frecuencia específica es necesario cambiar en el diagrama de flujo algunos parámetros como frecuencia, ganancia y ancho de banda.

2. ¿Qué parámetros del flujograma afectan la potencia de la señal transmitida?

La ganancia, ancho de banda y frecuencia de muestreo son algunos de los parámetros que afectan la potencia de la señal.

3. ¿Cómo se mide el ancho de banda de la señal transmitida en el analizador de espectros?

Para medir el ancho de banda en el analizador de espectros, se puede hacer uso de marcadores para medir el rango de frecuencias donde la potencia es significativa.

4. ¿Cómo se calcula la relación señal a ruido (SNR) a partir de las mediciones de potencia y piso de ruido?

Se puede hacer uso de la siguiente fórmula:

Relación señal/ruido (dB) = 10 · log₁₀ (Potencia de la señal / Potencia del ruido)

5. ¿Qué diferencias se observan en las mediciones de potencia cuando se varía la ganancia del USRP?

Aumentar la ganancia o disminuirla, puede variar el ruido o calidad de la señal transmitida y por tanto, la potencia.
  
6. ¿Es posible medir o estimar la potencia de la señal observada en el osciloscopio? ¿Por qué?

Si, por ejemplo en una señal seno, la relación de potencia está dado por la Amplitud al cuadrado por un medio. Entonces si se tiene la amplitud, medida de la cual el osciloscopio si está "diseñado" para medir nos serviría al medir o estimar la potencia.


## ** Análisis de Resultados y Conclusiones**

La SNR es importante debido a que es de lo más usado en comunicaciones inalambricas, ya que afecta directamente a la señal, la capacidad de transmision de datos y la eficiencia del sistema.

3. **Conclusiones**:

El osciloscopio está diseñado para observar las señales en el dominio del tiempo, por otro lado, el analizador de espectros mide señales en el dominio de la frecuencia. A pesar que es el analizador de espectros la herramienta más precisa para medir la potencia, esta se puede medir indirectamente por la amplitud y tipo de señal con el osciloscopio.

La relación señal a ruido **SNR** es un factor importante en las comunicaciones inalámbricas, que da información sobre la calidad, alcance y eficiencia de un sistema de comunicaciones.

Las limitaciones en el laboratorio pueden deberse a diversos fenómenos que generan ruido, lo que perturba la señal y afecta la precisión de las mediciones. Esto puede provocar discrepancias entre los resultados experimentales y los análisis teóricos.*
*Para mejorar la precisión de las mediciones, es fundamental minimizar el ruido que afecta la señal, por ejemplo, mediante el uso de cables con mejor blindaje o técnicas de filtrado adecuadas. Además, contar con un ancho de banda más amplio permitiría analizar el espectro de la señal con mayor detalle, especialmente en frecuencias más altas.

### **Preguntas Orientadoras**
1. ¿Qué conclusiones se pueden obtener sobre la relación entre la potencia de la señal y la calidad de la comunicación?

Es muy esencial para las comunicaciones debido a que una mayor potencia mejora la señal, debido a que una potencia de un nivel superior al ruido puede eliminar el ruido presente en el canal. esto aumenta el SNR, mejorando la fiabilidad y claridad del sonido de la comunicación, Pero, aumentar demasiado la potencia puede intervenir con otras señales y afectar las mismas, lo que hace que se apliquen otras técnicas que ayuden a mejorar el ruido y entre otros fenómenos, como lo son algoritmos de corrección de errores y modulaciones adaptativas para mejorar la comunicación de manera eficiente.

2. ¿Cómo afecta el piso de ruido a la capacidad de detectar señales débiles?

$$ SNR = \frac{P_{\text{señal}}}{P_{\text{ruido}}} $$
El piso de ruido alto, hace que el SNR baje, lo que hace que las detecciones de las señales débiles se dificulten, y si en cambio se reduce el ruido de fondo, mejora el SNR y mejora la recepción de señales de baja potencia, Como lo describe la fórmula.
Si la señal está muy cerca del piso de ruido lo que hace que el receptor se le dificulta distinguir la señal recibida, esto afecta principalmente al momento de recibir datos de larga distancia o entornos con interferencia. 


3. ¿Qué limitaciones tienen los equipos utilizados en términos de ancho de banda y precisión en las mediciones?

Las principales restricciones en el ancho de banda son las restricciones de frecuencia, debido a que dependiendo del ancho de banda de los equipos, no se puede analizar señales de alta frecuencia o señales con gran contenido espectral. También la dispersión de la señal, ya que debido a que si el ancho de banda del receptor es inferior al de la señal transmitida, esto hará que se pierdan componentes de altas frecuencias y esto hace que se distorsione la forma de onda. Y el ruido suele ser también una limitante debido a que los componentes que se utilizan como los cables tienen cierto nivel de ruido que afecta a la señal.

4. ¿Cómo se pueden mejorar las mediciones de señal en un entorno con alto nivel de ruido?

Para mejorar las mediciones se pueden usar filtros que ayuden con la disminución del ruido, ya sean filtros como pasa-banda, pasa-alta o pasa.banda que lo que hacen es eliminar componentes no deseados del espectro. Aumentar la potencia para mejorar la SNR. El tener conexiones a tierras adecuadas también ayudan a mejorar las mediciones. También incrementando la frecuencia de muestreo, debido a que se tiene una mayor captura de la variación de la señal. 

5. ¿Qué aplicaciones prácticas tienen las mediciones de potencia y ancho de banda en sistemas de comunicaciones reales?

Tienen diferentes aplicaciones como lo son: 
Prueba y diseño de dispositivos de radiofrecuencia se hace con el fin de garantizar que cumplen con las normas establecidas como el ancho de banda.  También es usado en aplicaciones de seguridad y defensa como para monitorear señales que no estén autorizadas en el espectro. Tambien para optimizar el consumo, como en los  Dispositivos IoT deben ajustar su potencia de transmisión para maximizar la duración de la batería.

6. ¿Cómo se puede medir la respuesta en frecuencia de un canal alámbrico?

Se puede medir utilizando un analizador de red también llamado VNA, un osciloscopio con generadores de señales, análisis con la FFT, pero el método depende de qué tan precisa se requiere la medición. 

7. ¿Cómo se puede obtener un modelo sencillo de las pérdidas (_pathloss_) en un canal inalámbrico?

Un modelo sencillo del _pathlos_ se puede obtener de dos maneras, ya sea por ecuacion de espacio libre

$$ PL_{\text{FS}}(dB) = 20\log_{10}(d) + 20\log_{10}(f) + 20\log_{10}\left(\frac{4\pi}{c}\right) $$

o por el modelo con exponente de pérdida, en el cual se ajusta el parámetro n dependiendo del entorno. Siendo la ecuacion para entornos no ideales: 

$$ PL(d) = PL(d_0) + 10n \log_{10} \left(\frac{d}{d_0} \right) $$



### Referencias
- [Rohde & Schwarz, *R&S® RTB2000 Digital Oscilloscope User Manual*, 2017](https://www.rohde-schwarz.com)
  
- [Rohde & Schwarz, *R&S® FPC1000 Spectrum Analyzer User Manual*, 2017](https://www.rohde-schwarz.com)

- [Proakis, 2014] J. Proakis, M. Salehi. Fundamentals of communication systems. 2 ed. England: Pearson Education Limited, 2014. p. 164-165, 346. Chapter 5 In: [Biblioteca UIS](https://uis.primo.exlibrisgroup.com/permalink/57UIDS_INST/63p0of/cdi_askewsholts_vlebooks_9781292015699)

- "Se utilizó ChatGPT para reformular secciones del texto y verificar gramática, pero el contenido técnico fue desarrollado íntegramente por los autores."

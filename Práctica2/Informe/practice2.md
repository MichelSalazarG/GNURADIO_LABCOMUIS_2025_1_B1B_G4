# Laboratorio de Comunicaciones  
## Universidad Industrial de Santander  

# Práctica 2A. Modelo de canal

### Integrantes  

- **PRIMER INTEGRANTE** - Código  
- **Michel Dayanna Salazar Gómez** - 2214194
## Objetivos
- Observar cómo el canal puede afectar la calidad de la señal transmitida y cómo  mitigar sus efectos.
- Evaluar aspectos clave como la relación señal-ruido y la eficiencia en la transmisión de datos.
- Estudiar el fenomeno de las señales en tiempo y en frecuencia. 
---
## Contenido

### Resumen
En esta práctica se utilizó GNU Radio para generar diversas señales con distintos fenómenos, permitiendo su observación tanto en el osciloscopio como en el analizador de espectro. De esta manera, se pudo analizar la forma de onda y los cambios que experimenta bajo diferentes condiciones.
**Palabras clave:** Frecuencia, desviacion, amplitud, potencia, SNR. 

### Introducción
Los efectos del canal juegan un papel importante en la calidad y la confiabilidad de la señal recibida. Factores como la atenuacion, el ruido, la propagación y la interferencia pueden dividir la señal que afecta su calidad e inhibir la interpretación exacta. En este ejercicio, estos resultados se estudian utilizando GNU-Radio, URP 2920, análisis de osciloscopio y espectro, lo que permite analizar los efectos de varios estados de transmisión en la señal de tiempo.

- 
## Materiales y Equipos

- **USRP 2920:** Radio definido por software.
- **Osciloscopio R&S RTB2004:** Para visualización de señales en el dominio del tiempo y la frecuencia.
- **Analizador de Espectros R&S FPC1000:** Para mediciones en el dominio de la frecuencia.
- **Computador con GNU Radio:** Para simulación y generación de señales usando el USRP 2920.
- **Cables y conectores:** Para interconexión de equipos.
- **Audífonos y micrófono** (opcional, debe traerlo cada grupo)

### Ajustes preliminares

- En el [flujograma](filters_flowgraph.grc) propuesto para esta práctica, se incluye un bloque "Wav File Source". **Antes** de ejecutar el flujograma, seleccione un archivo WAV para ser usado por este bloque. Algunos archivos WAV de ejemplo los puede encontrar en: [LabComUIS/samples/](../../samples/) 
- Tenga en cuenta que existen instrumentos de visualización en dominio tiempo y frecuencia tanto para la señal ANTES como DESPUÉS del filtro.
---

## Actividad 1: Actividades de simulación de canal en GNU Radio

### Objetivo

Familiarizarse con algunos fenómenos de canal en un ambiente simulado.

### Procedimiento

**Simulación**
   - Verificar equipos y elementos a utilizar (revisar manuales de ser necesario)
   - Cargar el flujograma: [filters_flowgraph.grc](filters_flowgraph.grc).
   - Configurar siempre la frecuencia de muestreo (`samp_rate`) en $25e6/2^n$ Hz`, donde $n$ es un número entero mayor a 2.
   - Genere diferentes señales y observe el efecto de variar las frecuencias de corte del filtro.
   - Analice el efecto del ruido en el dominio del tiempo y la frecuencia para al menos dos formas de onda distintas.
   - Muestre con un ejemplo gráfico el umbral de máximo de ruido ante el cual considera que es posible recuperar cada forma de onda utilizando únicamente filtrado.

### Preguntas Orientadoras

- ¿Cuál es el efecto de filtrar las frecuencias altas de una señal?
  
![Imagen de WhatsApp 2025-03-18 a las 18 54 11_c6e4f346](https://github.com/user-attachments/assets/2a63c931-f3c8-43b8-8275-a0299c53e1f8)

Se estaría aplicando un filtro banda base, donde se eliminan las frecuencias altas dejando solo aqueñas frecuencias de la señal dentro del rango permitido; lo que hace suavizar la señal reduciendo  y atenuando el ruido de alta frecuencia.

- ¿Qué sucede al filtrar muy cerca de la frecuencia fundamental de la señal?

Señal constante filtrada cerca a 1000Hz:
![Imagen de WhatsApp 2025-03-18 a las 16 52 32_16314ef6](https://github.com/user-attachments/assets/50db37c1-ceb7-441c-b066-13a15ced5d88)

Señal seno con ruido:
![Imagen de WhatsApp 2025-03-18 a las 16 52 37_ec576c05](https://github.com/user-attachments/assets/7aac11b3-f927-4c95-b137-7a0fa7fa4486)

Señal seno filtrada cerca a 1000Hz:
![Imagen de WhatsApp 2025-03-18 a las 16 52 48_003380f8](https://github.com/user-attachments/assets/329c568b-4835-48e9-9c9a-dcdfcd4be857)

Como se puede observar en las imágenes anteriores, al aplicar el filtro cerca de la frecuencia fundamental de la señal, esta se mantiene prácticamente intacta, mientras que el ruido y componentes no deseados logran una reducción significativa preservando la señal original.

- ¿Cuál es el efecto de filtrar las frecuencias bajas de una señal?

![Imagen de WhatsApp 2025-03-18 a las 16 53 02_45f907e1](https://github.com/user-attachments/assets/c87f2746-0acc-43ec-876c-04a4e13b2591)

![Imagen de WhatsApp 2025-03-18 a las 16 53 09_955fab73](https://github.com/user-attachments/assets/869dacce-c0cc-4898-999e-0d8ae1a324ed)

Cuando se filtran las frecuencias bajas de una señal, se está aplicando un filtro pasa banda o pasa alta, lo que significa que se eliminan los componentes de frecuencia más bajas manteniendo las frecuencias altas. 

- ¿Qué ocurre al eliminar armónicos de una señal?
  
![Imagen de WhatsApp 2025-03-18 a las 16 54 15_66f7cb33](https://github.com/user-attachments/assets/90c0601d-789a-4446-8bae-f89e571ab549)

![Imagen de WhatsApp 2025-03-18 a las 16 54 25_0dcc0369](https://github.com/user-attachments/assets/bdf78fd0-284b-40da-bf0d-1207a6351472)

![Imagen de WhatsApp 2025-03-18 a las 16 54 32_78fcc9bb](https://github.com/user-attachments/assets/20a7e28d-de2f-43c8-be90-ab11d2f3e171)

Al eliminar armónicos con un filtro tiende a cambiar la estructura de la señal, se pierden los detalles en la forma de onda así como la reducción de la amplitud de ciertas frecuencias.

- ¿Qué efecto tiene la desviación de frecuencia en la señal recibida? ¿Qué efecto(s) produce el filtro cuando la señal recibida se ve afectada por desviación de frecuencia?
  
![Imagen de WhatsApp 2025-03-18 a las 18 49 49_be094ff1](https://github.com/user-attachments/assets/7df97105-3cb6-4aea-af59-4a52c8923eb4)

Desviación Negativa:
![Imagen de WhatsApp 2025-03-18 a las 18 50 03_ca9f29cf](https://github.com/user-attachments/assets/5e2dc48f-2278-457c-97e9-51f77b762822)

Desviación positiva:
![Imagen de WhatsApp 2025-03-18 a las 18 50 13_0566963f](https://github.com/user-attachments/assets/b475b5df-1c43-4900-aa8b-634fca4c182f)

Constante:
![Imagen de WhatsApp 2025-03-18 a las 18 50 25_085920d0](https://github.com/user-attachments/assets/9ca26430-00e9-4f8e-a179-926e30b6b3d7)


CUADRADA NORMAL
![Imagen de WhatsApp 2025-03-18 a las 16 55 34_075a793b](https://github.com/user-attachments/assets/c5e499af-2d8a-44a0-b738-2f12bdf32bcd)

DESVIADA
![Imagen de WhatsApp 2025-03-18 a las 16 55 48_bc2b50c1](https://github.com/user-attachments/assets/99fca368-a18a-4cf2-b2d1-9b9548879aa5)

Lo la desviación de frecuencia en una señal como se ve en las imágenes anteriores, genera cambios en el tiempo afectando tanto la forma de onda como la amplitud.  Al analizar la Ganancia relativa de la señal, se ve un desplazamiento tanto para izquierda o derecha en la frecuencia, dependiendo del valor y signo de la desviación.

- ¿Cómo cuantificar la degradación de la señal al aumentar los niveles de ruido?

CONSTANTE

![Imagen de WhatsApp 2025-03-18 a las 16 56 03_efab8ba2](https://github.com/user-attachments/assets/e49de3ca-cae4-47a3-aae2-0f61b4a3a4e8)

![Imagen de WhatsApp 2025-03-18 a las 16 56 12_1d97f865](https://github.com/user-attachments/assets/5e7fcdf1-c624-4e21-bb7b-85b6b4724d23)

DIENTE DE SIERRA

![Imagen de WhatsApp 2025-03-18 a las 16 56 57_bb78de21](https://github.com/user-attachments/assets/2244fbed-b006-4710-afca-5b04eaa089ed)

![Imagen de WhatsApp 2025-03-18 a las 16 57 07_bf34d496](https://github.com/user-attachments/assets/256a5d8b-af8f-45f4-b0fc-2c71b90ca7fc)

Al analizar la señal en el dominio del tiempo, se observa que el ruido genera pequeñas variaciones respecto a la señal de onda original, dejando la onda de ser tan recta y cambiando a ser un poco más ondulada. 
Por otro lado en el dominio de la frecuencia, se ve como salen nuevas componentes aunque de menor magnitud en comparación con las principales.  Una forma de medirlo podría ser con el SNR.

$$
SNR = 10 \log_{10} \left(\frac{P_{\text{señal}}}{P_{\text{ruido}}} \right)
$$

- ¿Cómo se puede mejorar la relación señal a ruido en una señal?
  
![Imagen de WhatsApp 2025-03-18 a las 18 47 32_cc03aae3](https://github.com/user-attachments/assets/62f817ae-8a86-4fa1-b229-4c7312ac0fe5)

![Imagen de WhatsApp 2025-03-18 a las 18 47 39_ee3a00ad](https://github.com/user-attachments/assets/10c52b64-ddd1-44f1-aaa5-4a0023bb2694)

![Imagen de WhatsApp 2025-03-18 a las 18 47 46_f6afd004](https://github.com/user-attachments/assets/a5171b52-e5e9-4e2e-bf7f-c90e4419f7bf)

![Imagen de WhatsApp 2025-03-18 a las 18 48 00_b56d62ed](https://github.com/user-attachments/assets/bb05199a-8b46-4a67-97df-177d54e80573)

![Imagen de WhatsApp 2025-03-18 a las 18 48 07_fdd2ccd7](https://github.com/user-attachments/assets/e0998302-4ba7-42bb-9374-e3ec57bd43c8)

Como se observa en las imágenes una forma de mejorar la relación señal a ruido meramente con el filtrado sería usar filtros con frecuencia de corte alta cerca a la frecuencia de corte fundamental usada en la señal.

- ¿Cómo podría cuantificar la calidad de la señal recibida? Considere el caso de señales analógicas y digitales.

La manera de cuantificar la calidad de la señal recibida sería con relaciones de señal a ruido o proporción de márgenes de error o ruido.

### Evidencia

*(Adjuntar las evidencias de la práctica en el Aula Virtual: capturas de pantalla, observaciones, cálculos o mediciones preliminares)*
![e9d3044f-37a6-4a41-80a2-ed21c03d7c07](https://github.com/user-attachments/assets/ff676627-dcda-4d15-a309-cd5d6406be78)

---

## Actividad 2: Fenómenos de canal en el osciloscopio

### Objetivo

Familiarizarse con los fenómenos de un canal alámbrico real en el dominio del tiempo.

### Procedimiento

1. **Configurar el USRP 2920:**
   - Configurar el flujograma [filters_flowgraph.grc](filters_flowgraph.grc) en GNU Radio para transmitir una señal a través del USRP.
   - Habilitar o deshabilitar los bloques correspondientes (`Channel Model`, `Throttle`, `UHD: USRP Sink`, `UHD: USRP Source`, `Virtual Sink`). Para esto, seleccione el bloque deseado y presione **E** (enable) o **D** (disable), según corresponda.
   - Configurar siempre la frecuencia de muestreo (`samp_rate`) en $25e6/2^n$ Hz`, donde $n$ es un número entero mayor a 2. Verifique que la frecuencia de muestreo durante la ejecución, sea la misma que ha configurado en el flujograma.

2. **Configurar el osciloscopio:**
   - Encender, configurar y conectar el osciloscopio a la salida del USRP 2920 usando diferentes cables coaxiales, y ajustando los parámetros necesarios para evidenciar los fenómenos de canal analizados en la Actividad 1.
   - Variar la frecuencia de portadora del USRP entre 50 MHz hasta 500 MHz y anaalizar los resultados.

### Preguntas Orientadoras

- ¿Cuál es el efecto del ruido sobre la amplitud de las señales medidas en el osciloscopio? ¿Conservan las mismas relaciones que se evidencian en la simulación?
Como se observa en las imágenes, el ruido aumenta significativamente en comparación con la señal, lo que provoca su distorsión y afecta su correcta interpretación.
SAWTOOTH SIN RUIDO
![SCR05](https://github.com/user-attachments/assets/ad3e121f-bfb7-46d9-aafc-6b4869782a63)

SAWTOOTH CON RUIDO 0.14
![SCR06](https://github.com/user-attachments/assets/bc7e20ad-16b5-4790-b80b-f4488ddcbc56)

COMPARACIÓN CON Y SIN RUIDO 

![SCR07](https://github.com/user-attachments/assets/bcdbf9cc-ab92-4855-9262-d3116f135334)

  SENO SIN RUIDO 
![SCR10](https://github.com/user-attachments/assets/bf68f9a1-26ee-469a-83a8-4b6bce8925d3)

  SENO CON RUIDO 0.2
![SCR11](https://github.com/user-attachments/assets/da04a70c-7058-4f02-a646-4dc907485f70)

  
- ¿La relación señal a ruido creada intencionalmente en el computador se amplifica o se reduce en la señal observada en el osciloscopio?

  La relación señal a ruido, generada intencionalmente en el computador, se amplifica al ser observada en el osciloscopio. Si el ruido es demasiado alto, la señal puede llegar a distorsionarse o incluso perderse.
SENO SIN RUIDO
![SCR08](https://github.com/user-attachments/assets/3bc963f9-8eae-43ec-9525-e528d4238543)
SENO CON RUIDO
![SCR09](https://github.com/user-attachments/assets/002c116a-772c-47e4-9533-66ea40fd0998)



- Demuestre ¿cómo se puede mejorar la relación señal a ruido en una señal?

  La relación señal a ruido (SNR) se puede mejorar mediante varias técnicas, como lo seria: 
  Filtrado: Utilizando filtros pasa bajas, pasa bandas o digitales para reducir el ruido no deseado.
  Aumento de potencia de la señal: Incrementando la amplitud de la señal útil sin amplificar el ruido.

- ¿Cómo se evidencia el fenómeno de desviación de frecuencia en el osciloscopio? Evidenciar al menos con dos formas de onda.
Se puede ver como  la onda mostrada en el osciloscopio presenta variaciones en su período y forma, reflejando cambios en la frecuencia instantánea.

  SEÑAL TRIANGULAR SIN DESVIACION
![SCR13](https://github.com/user-attachments/assets/c18135b3-acca-4706-b403-a1409781c4e7)
DESVIACION DE 1000
![SCR14](https://github.com/user-attachments/assets/4afaf1aa-0137-43a8-88d4-33a9a51d76a3)
DESVIACION DE 5000
![SCR15](https://github.com/user-attachments/assets/0c59d89d-3853-454c-bcb5-463144f20240)

COSENO SIN OFFSET
![SCR17](https://github.com/user-attachments/assets/19af4961-70c1-4b51-9f96-3d6ca7be4f70)
CON OFFSET DE 1000
![SCR18](https://github.com/user-attachments/assets/c0b6fd0e-7e6f-4a2e-bacf-15444b550d94)
CON OFFSET DE 5000
![SCR20](https://github.com/user-attachments/assets/4568ea17-45ee-4395-9ed9-d1251624194b)



  
- Determine la afectación de un medio de transmisión coaxial (usar cables largos) sobre una señal periódica operando a las capacidades máximas de muestreo del USRP.
Unas de las afecciones poddrian ser: Atenuación: A medida que la señal viaja a través del cable coaxial, su amplitud disminuye debido a la resistencia y pérdidas dieléctricas del medio.
Ruido e interferencias externas: Los cables largos pueden actuar como antenas, captando ruido electromagnético del entorno.
- 
  - **NOTA:** La frecuencia de transmisión no debe superar los 500 MHz para ser observada en el osciloscopio. Para el experimento, considere las relaciones de muestreo correspondientes.
- Usando cables coaxiales de diferentes longitudes, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida?

Se puede ver afectada de varias maneras, como por ejemplo la atenuación debido a que a mayor longitud del cable, mayores serán las pérdidas resistivas y dieléctricas, lo que reduce la amplitud de la señal recibida. Estas pérdidas son más pronunciadas en frecuencias altas. Asi como, la dispersión de la señal: En cables largos, la velocidad de propagación puede variar con la frecuencia, causando distorsión en la forma de la señal.

SENO SIN RUIDO 
 ![SCR22](https://github.com/user-attachments/assets/d2408bcc-e453-44b4-add9-014fe9a5fc8c)

CON RUIDO
![SCR23](https://github.com/user-attachments/assets/141fc9cb-c0cf-4ffd-9f52-4a3b24c164c2)

![SCR24](https://github.com/user-attachments/assets/79b7cd87-0ca9-4943-a472-fd3042460b53)


- Usando antenas, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? ¿Es posible compensar el fenómeno?
![SCR01](https://github.com/user-attachments/assets/d1e9de90-ca2e-4c1a-a528-a459a1a8459d)
![SCR02](https://github.com/user-attachments/assets/4167ad66-49e2-4fec-803e-fa6b495a6eb9)
![SCR03](https://github.com/user-attachments/assets/d55f075e-0d80-40cc-a0a1-e10321aa3d4c)


- ¿Qué modelo de canal básico describe mejor las mediciones obtenidas en la práctica?
Al tratarse de un sistema de transmisión por cable coaxial, este puede asemejarse a un canal lineal con ruido aditivo (AWGN). Esto se debe a que el ruido térmico y de fondo pueden afectar la señal observada en el osciloscopio, introduciendo distorsiones. Además, la atenuación, ya que el cable coaxial genera pérdidas que dependen de la frecuencia, reduciendo la amplitud de la señal a medida que la distancia aumenta.

### Evidencia

*(Adjuntar las evidencias de la práctica en el Aula Virtual: capturas de pantalla, observaciones, cálculos o mediciones preliminares)*

---

## Actividad 3: Fenómenos de canal en el analizador de espectro

### Objetivo

Familiarizarse con los fenómenos de un canal alámbrico real en el dominio de la frecuencia.

### Procedimiento

1. **Configurar el USRP 2920:**
   - Configurar el flujograma [filters_flowgraph.grc](filters_flowgraph.grc) en GNU Radio para transmitir una señal a través del USRP.
   - Habilitar o deshabilitar los bloques correspondientes (`Channel Model`, `Throttle`, `UHD: USRP Sink`, `UHD: USRP Source`, `Virtual Sink`). Para esto, seleccione el bloque deseado y presione **E** (enable) o **D** (disable), respectivamente.
   - Configurar siempre la frecuencia de muestreo (`samp_rate`) en $25e6/2^n$ Hz`, donde $n$ es un número entero mayor a 2.  Verifique que la frecuencia de muestreo durante la ejecución, sea la misma que ha configurado en el flujograma.

2. **Configurar el Analizador de Espectros:**
   - Encender, configurar y conectar el analizador de espectros a la salida del USRP 2920 usando diferentes cables coaxiales, y ajustando los parámetros necesarios para evidenciar los fenómenos de canal analizados en la Actividad 1.

### Preguntas Orientadoras

- ¿Cuál es el efecto del ruido sobre la respuesta en frecuencia de las señales medidas en el analizador de espectro? ¿Conservan las mismas relaciones que se evidencian en la simulación?
  
Señal original sin ruido:

![9ab88f8a-1e12-462b-bb1f-a9f8510308f0](https://github.com/user-attachments/assets/a280dd9f-4cb3-43ef-9b14-0e6724371410)
![7e76dfa8-71a3-4658-8b12-b10e2f55e2c3](https://github.com/user-attachments/assets/37e03352-52a5-4e2e-b557-5e9b0b2935f3)

Señal con ruido de 0.25:
![4accd017-26b5-4a88-bc81-98e6eb1ebd41](https://github.com/user-attachments/assets/26c350f2-2c19-4df7-8637-b015ef139518)
![a01a552c-24c5-4076-979e-fc77fc758f11](https://github.com/user-attachments/assets/075975df-de31-43f6-91ba-efd6e1f40b86)
![f4927d40-bd70-4def-9617-841b49c0045c](https://github.com/user-attachments/assets/8cb73dfb-f92e-45e8-befd-2683676bdd65)
![03295f2a-1a35-4a81-b411-4530f65bc96b](https://github.com/user-attachments/assets/9340b84c-64cc-41be-8c68-39022e6c8464)
![d8cb3ebe-6de9-41ef-9d10-28945ef35c7e](https://github.com/user-attachments/assets/0638b15c-db9c-4475-9fb1-d15d9f94d883)

El ruido afecta la señal original, cambiando la forma de la señal original y agregando un nivel de piso de ruido cambiando de esa forma la relación señal a ruido.

- ¿La relación señal a ruido creada intencionalmente desde el computador se amplifica o se reduce en la señal observada en el analizador de espectro?
- Adjunte la evidencia de la medición de la relación señal a ruido de dos formas de onda distintas.
  
Señal triangular sin ruido:
![672e4984-9687-416e-8882-e0997ec3b404](https://github.com/user-attachments/assets/26ba9266-b43a-47c8-86f9-109f3df3b611)
![0e6535b1-9b6f-4fba-8186-78acef41a057](https://github.com/user-attachments/assets/506c9e77-06d0-4cfd-ad1d-db43b6e82457)

Señal triangular con ruido 0.25:
![f0640521-3bf6-4abb-a1dc-a758b46cea16](https://github.com/user-attachments/assets/885cc163-1f6b-4d96-848f-236dd06f301e)
![b924c253-003f-4468-aa12-68d25f0ebbd5](https://github.com/user-attachments/assets/0b045bd7-e61f-4ea6-b657-df01ba79958a)
![7e2a30c8-e539-4e77-8bad-720c8b22d0c3](https://github.com/user-attachments/assets/5024bf77-3531-454e-8590-13ff39fb0b55)
![d5175d5f-f2be-4976-805b-48ae82ff9e60](https://github.com/user-attachments/assets/04e7544b-ffea-4558-9395-31937345d5b8)
![45059b86-2adf-4245-b848-146395a14ce5](https://github.com/user-attachments/assets/b7549399-4582-4572-94cf-9efc3249694e)


SNR[dB]= Pn[dB]-Ps[dB]

Medición Señal a Ruido triangular:
SNR[dB]= Pn[dB]-Ps[dB]




- ¿Cómo se evidencia el fenómeno de desviación de frecuencia en el analizador de espectro? Evidenciar al menos con dos formas de onda.

Coseno sin desviación:
![cbdc2aa3-3ccc-4e23-8aab-d9b8633bad35](https://github.com/user-attachments/assets/a56bea10-1268-461c-9cfd-87cafb4daf41)
![955b0116-7526-48ed-a28f-15558fe8d563](https://github.com/user-attachments/assets/15fd518d-2a48-41bb-b6c9-1e3d5833e1a4)

Desviación de 10kHz:
![33e51af6-3872-43be-b9d0-7a884172bafc](https://github.com/user-attachments/assets/689a1abc-1a7c-4a93-937c-5bf92ab7aa8f)
![cf951f9d-982c-4b7a-8b02-3208f13821d7](https://github.com/user-attachments/assets/19528c0b-f11e-4b0a-a041-eb01b1948c40)

El fenómeno de desviación da como resultado antes del filtro, la señal desplazada por el valor dado de la desviación en la simulación; así mismo en el analizador de espectros se ve como también la señal es desplazada.
Ahora al analizar la desviación con la ganancia relativa después del filtro, se observa como cambia la amplitud y forma de onda de los diferentes componentes en frecuencia.

- Determine la afectación de un medio de transmisión coaxial (usar cables largos) sobre una señal periódica operando a las capacidades máximas de muestreo del USRP.
  - **NOTA:** La frecuencia de transmisión no debe superar los 1000 MHz para ser observada en el analizador. Para el experimento, considere las relaciones de muestreo correspondientes.

Señal triangular Samp_rate=25e6/2
![4cf0e6b9-51b8-4d89-96af-c8e528c02d30](https://github.com/user-attachments/assets/65d93e77-cd8d-44d4-9a03-c55f8d98ec9e)
![ec84d343-bcb0-4959-a8c5-1c9c2ebf6fb0](https://github.com/user-attachments/assets/4ce87feb-4b1c-43af-9401-2f0748d4283a)

Señal seno Samp_rate=25e6/2
![212c6c95-7377-4f87-9fe5-53de9bbfdeb1](https://github.com/user-attachments/assets/33d9010b-b15f-4b7a-a1aa-0d61a3ea11ac)

    
- Usando cables coaxiales de diferentes longitudes, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida?
- Usando antenas, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? ¿Es posible compensar el fenómeno?
![e78a5217-7f7d-4bd9-a789-37927ce6a2f2](https://github.com/user-attachments/assets/bb209095-887a-42e3-8cde-f571bc6cac9b)
![4f7bc292-5ead-4d8c-b5e2-8bc689b929e4](https://github.com/user-attachments/assets/c1edb2e6-5105-4722-a9b2-7290c83e3c8f)
![97b57008-6489-4f63-92aa-dd41f7236163](https://github.com/user-attachments/assets/045d1f9e-8ade-4325-9e93-d6e546805a53)


- ¿Qué modelo de canal básico describe mejor las mediciones obtenidas en la práctica?

### Evidencia Flujograma

![ac983bf3-ac92-46e9-995e-ca9a83748948](https://github.com/user-attachments/assets/991eb082-5bc2-46b2-bd0d-4fea2e063e7a)


## Actividad 4: Efectos de los fenómenos de canal en la conversión de frecuencia

### Objetivo

Familiarizarse con los efectos de los fenómenos de un canal alámbrico e inalámbrico real en la conversión de frecuencia.

### Procedimiento

**Configurar el USRP 2920:**
   - Configurar el flujograma [filters_flowgraph.grc](filters_flowgraph.grc) en GNU Radio para **transmitir y recibir ** una señal a través del USRP.
   - Habilitar o deshabilitar los bloques correspondientes (`Channel Model`, `Throttle`, `UHD: USRP Sink`, `UHD: USRP Source`, `Virtual Sink`). Para esto, seleccione el bloque deseado y presione **E** (enable) o **D** (disable), respectivamente.
   - Configurar siempre la frecuencia de muestreo (`samp_rate`) en $25e6/2^n$ Hz`, donde $n$ es un número entero mayor a 2. Verifique que la frecuencia de muestreo durante la ejecución, sea la misma que ha configurado en el flujograma.
   - Compare los resultados al recibir la señal usando diferentes medios (aire o cable coaxial).

### Preguntas Orientadoras

Usando analizador de espectros
Señal seno sin ruido:
![b5e20bda-9d70-4cd3-8338-88139e117084](https://github.com/user-attachments/assets/ad776de6-a74a-4fbc-b1b7-716530118b76)
![09d9721e-5d15-41f6-b893-660f86e21b3b](https://github.com/user-attachments/assets/846285e2-5a9f-451d-b441-f3c7c3d9b760)

Señal seno con ruido de 0.5:
![65c1d421-e399-4f35-b30e-2a37bfcdd3ed](https://github.com/user-attachments/assets/281b4401-bb46-48dd-8cc1-5339e3e8c9d6)
![bd3f35ef-8dd2-4e7e-92c5-b7f9fc73589f](https://github.com/user-attachments/assets/83b24c16-9463-4593-b88c-3e322fdf9c87)
![7d6d3ba8-a16b-4e85-8d7f-94d6d9c1bf32](https://github.com/user-attachments/assets/0dd33309-1ef3-4f6b-bc1e-17b02b99d193)

Desviación:
![35e2860b-814f-414d-aee6-9c2992819621](https://github.com/user-attachments/assets/a75fefc5-1bd6-4af7-8a4f-818260aa3a4d)

- ¿Cómo se evidencian los diferentes fenómenos de canal en la señal recibida?

Los diferentes fenómenos del canal se evidencian a través de sus efectos en la señal recibida:

Dispersión: Provoca la distorsión de la forma de onda, alterando su estructura original.
Interferencias externas: Introducen ruido no deseado en la señal, afectando su calidad.
Atenuación: Se manifiesta como una reducción en la amplitud de la señal, disminuyendo su intensidad a medida que aumenta la distancia o la frecuencia.

- ¿Cómo se pueden mitigar los efectos del canal en la señal recibida?
Para mitigar estos efectos, lo ideal es utilizar filtros adecuados, ya sea pasa bajas o pasa bandas, para reducir el ruido e interferencias no deseadas. Además, es importante emplear cables de mejor calidad, con menor pérdida y mayor blindaje, para minimizar la atenuación y las interferencias externas. También se pueden utilizar amplificadores para compensar la atenuación y evitar que esta afecte significativamente la señal.

### Conclusiones
En conclusion, en esta práctica se analizaron los diferentes efectos que pueden afectar un canal de comunicación, tales como la variación de frecuencia, el ruido y otros factores. Se observó cómo estos fenómenos se manifiestan tanto en el osciloscopio como en el analizador de espectro, permitiendo comparar la señal generada en GNU Radio con la señal recibida. Esto permitió evidenciar de manera práctica el impacto de las condiciones del canal en la calidad de la señal transmitida.

### Referencias
- [Proakis, 2014] J. Proakis, M. Salehi. Fundamentals of communication systems. 2 ed. England: Pearson Education Limited, 2014. p. 164-165, 346. Chapter 5 In: [Biblioteca UIS](https://uis.primo.exlibrisgroup.com/permalink/57UIDS_INST/63p0of/cdi_askewsholts_vlebooks_9781292015699)

"Se utilizó ChatGPT para reformular secciones del texto y verificar gramática, pero el contenido técnico fue desarrollado íntegramente por los autores."





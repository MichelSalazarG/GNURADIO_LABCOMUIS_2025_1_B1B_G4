# Práctica 2A. Modelo de canal

## Objetivos
- Observar cómo el canal puede afectar la calidad de la señal transmitida y cómo  mitigar sus efectos.
- Evaluar aspectos clave como la relación señal-ruido y la eficiencia en la transmisión de datos.

Este enfoque permitirá no solo verificar la teoría, sino también desarrollar habilidades prácticas en el manejo de equipos de laboratorio, como equipos de medición (USRP 2920, osciloscopio R&S RTB2004 y analizador de espectros R&S FPC1000).

---

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


- ¿Qué sucede al filtrar muy cerca de la frecuencia fundamental de la señal?

![Imagen de WhatsApp 2025-03-18 a las 16 52 32_16314ef6](https://github.com/user-attachments/assets/50db37c1-ceb7-441c-b066-13a15ced5d88)

![Imagen de WhatsApp 2025-03-18 a las 16 52 37_ec576c05](https://github.com/user-attachments/assets/7aac11b3-f927-4c95-b137-7a0fa7fa4486)

![Imagen de WhatsApp 2025-03-18 a las 16 52 48_003380f8](https://github.com/user-attachments/assets/329c568b-4835-48e9-9c9a-dcdfcd4be857)

- ¿Cuál es el efecto de filtrar las frecuencias bajas de una señal?

![Imagen de WhatsApp 2025-03-18 a las 16 53 02_45f907e1](https://github.com/user-attachments/assets/c87f2746-0acc-43ec-876c-04a4e13b2591)

![Imagen de WhatsApp 2025-03-18 a las 16 53 09_955fab73](https://github.com/user-attachments/assets/869dacce-c0cc-4898-999e-0d8ae1a324ed)

- ¿Qué ocurre al eliminar armónicos de una señal?
  
![Imagen de WhatsApp 2025-03-18 a las 16 54 15_66f7cb33](https://github.com/user-attachments/assets/90c0601d-789a-4446-8bae-f89e571ab549)

![Imagen de WhatsApp 2025-03-18 a las 16 54 25_0dcc0369](https://github.com/user-attachments/assets/bdf78fd0-284b-40da-bf0d-1207a6351472)

![Imagen de WhatsApp 2025-03-18 a las 16 54 32_78fcc9bb](https://github.com/user-attachments/assets/20a7e28d-de2f-43c8-be90-ab11d2f3e171)


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

- ¿Cómo cuantificar la degradación de la señal al aumentar los niveles de ruido?

CONSTANTE

![Imagen de WhatsApp 2025-03-18 a las 16 56 03_efab8ba2](https://github.com/user-attachments/assets/e49de3ca-cae4-47a3-aae2-0f61b4a3a4e8)

![Imagen de WhatsApp 2025-03-18 a las 16 56 12_1d97f865](https://github.com/user-attachments/assets/5e7fcdf1-c624-4e21-bb7b-85b6b4724d23)

DIENTE DE SIERRA

![Imagen de WhatsApp 2025-03-18 a las 16 56 57_bb78de21](https://github.com/user-attachments/assets/2244fbed-b006-4710-afca-5b04eaa089ed)

![Imagen de WhatsApp 2025-03-18 a las 16 57 07_bf34d496](https://github.com/user-attachments/assets/256a5d8b-af8f-45f4-b0fc-2c71b90ca7fc)

- ¿Cómo se puede mejorar la relación señal a ruido en una señal?
  
![Imagen de WhatsApp 2025-03-18 a las 18 47 32_cc03aae3](https://github.com/user-attachments/assets/62f817ae-8a86-4fa1-b229-4c7312ac0fe5)

![Imagen de WhatsApp 2025-03-18 a las 18 47 39_ee3a00ad](https://github.com/user-attachments/assets/10c52b64-ddd1-44f1-aaa5-4a0023bb2694)

![Imagen de WhatsApp 2025-03-18 a las 18 47 46_f6afd004](https://github.com/user-attachments/assets/a5171b52-e5e9-4e2e-bf7f-c90e4419f7bf)

![Imagen de WhatsApp 2025-03-18 a las 18 48 00_b56d62ed](https://github.com/user-attachments/assets/bb05199a-8b46-4a67-97df-177d54e80573)

![Imagen de WhatsApp 2025-03-18 a las 18 48 07_fdd2ccd7](https://github.com/user-attachments/assets/e0998302-4ba7-42bb-9374-e3ec57bd43c8)

- ¿Cómo podría cuantificar la calidad de la señal recibida? Considere el caso de señales analógicas y digitales.


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
- ¿La relación señal a ruido creada intencionalmente en el computador se amplifica o se reduce en la señal observada en el osciloscopio?
- Demuestre ¿cómo se puede mejorar la relación señal a ruido en una señal?
- ¿Cómo se evidencia el fenómeno de desviación de frecuencia en el osciloscopio? Evidenciar al menos con dos formas de onda.
- Determine la afectación de un medio de transmisión coaxial (usar cables largos) sobre una señal periódica operando a las capacidades máximas de muestreo del USRP.
- 
  - **NOTA:** La frecuencia de transmisión no debe superar los 500 MHz para ser observada en el osciloscopio. Para el experimento, considere las relaciones de muestreo correspondientes.
- Usando cables coaxiales de diferentes longitudes, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida?
- Usando antenas, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? ¿Es posible compensar el fenómeno?
![SCR01](https://github.com/user-attachments/assets/d1e9de90-ca2e-4c1a-a528-a459a1a8459d)
![SCR02](https://github.com/user-attachments/assets/4167ad66-49e2-4fec-803e-fa6b495a6eb9)
![SCR03](https://github.com/user-attachments/assets/d55f075e-0d80-40cc-a0a1-e10321aa3d4c)


- ¿Qué modelo de canal básico describe mejor las mediciones obtenidas en la práctica?

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
- ¿La relación señal a ruido creada intencionalmente desde el computador se amplifica o se reduce en la señal observada en el analizador de espectro?
- Adjunte la evidencia de la medición de la relación señal a ruido de dos formas de onda distintas.
- ¿Cómo se evidencia el fenómeno de desviación de frecuencia en el analizador de espectro? Evidenciar al menos con dos formas de onda.
- Determine la afectación de un medio de transmisión coaxial (usar cables largos) sobre una señal periódica operando a las capacidades máximas de muestreo del USRP.
  - **NOTA:** La frecuencia de transmisión no debe superar los 1000 MHz para ser observada en el analizador. Para el experimento, considere las relaciones de muestreo correspondientes.
- Usando cables coaxiales de diferentes longitudes, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida?
- Usando antenas, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? ¿Es posible compensar el fenómeno?
- ¿Qué modelo de canal básico describe mejor las mediciones obtenidas en la práctica?

### Evidencia

*(Adjuntar las evidencias de la práctica en el Aula Virtual: capturas de pantalla, observaciones, cálculos o mediciones preliminares)*

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

- ¿Cómo se evidencian los diferentes fenómenos de canal en la señal recibida?
- ¿Cómo se pueden mitigar los efectos del canal en la señal recibida?

### Evidencia

*(Adjuntar las evidencias de la práctica en el Aula Virtual: capturas de pantalla, observaciones, cálculos o mediciones preliminares)*

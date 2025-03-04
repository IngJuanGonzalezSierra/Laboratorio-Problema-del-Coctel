# Laboratorio-Problema-del-Coctel
El problema de la "fiesta de cóctel" se refiere a la capacidad de un sistema para concentrarse en una sola fuente sonora mientras filtra las demás en un entorno con múltiples emisores de sonido. Este problema es común en sistemas de audición tanto humanos como artificiales, y su resolución es esencial en aplicaciones como la mejora.
#  Beamforming en el Dominio de la Frecuencia 

Este repositorio contiene un sistema de procesamiento de señales de audio, diseñado para implementar **beamforming** en el dominio de la frecuencia. Este método mejora la señal de audio mezclada con ruido. Utilizamos múltiples señales de entrada de audio para reforzar la señal deseada y reducir el impacto del ruido mediante técnicas de transformación de Fourier.

##  Funcionamiento

###  Beamforming - Conceptos Clave
El **beamforming** es una técnica que permite combinar señales provenientes de diferentes fuentes (micrófonos) con diferentes retardos. Su objetivo es **amplificar** la señal deseada mientras **reduce** el ruido de fondo o interferencias no deseadas.

Se utiliza especialmente en sistemas de **procesamiento de audio** y **comunicaciones** para focalizar la captura de sonido desde una dirección específica, mejorando la claridad de la señal. El sistema ajusta los tiempos de retardo aplicados a cada señal en función de la distancia entre los micrófonos y la fuente de sonido, logrando una mayor **precisión espacial**.

###  Cómo Funciona
1. **Captura de Audio**: Los micrófonos captan múltiples versiones de la misma señal de audio (por ejemplo, una conversación en una sala).
2. **Cálculo de Retardos**: Dependiendo de la distancia entre los micrófonos y la fuente, la señal llega con un ligero desfase a cada uno de los micrófonos. Este desfase se corrige calculando los **retardos**.
3. **Transformada de Fourier (FFT)**: Las señales de audio en el dominio del tiempo se convierten al **dominio de la frecuencia** utilizando la FFT.
4. **Ajuste de Retardos en Frecuencia**: En el dominio de la frecuencia, se aplican retardos precisos a cada micrófono para alinear las señales.
5. **Combinación de Señales**: Se promedian las señales ajustadas para obtener una única señal, la cual tiene un mejor **SNR** y menos ruido.
6. **Transformada Inversa (IFFT)**: Finalmente, se aplica la **IFFT** para obtener la señal combinada en el dominio del tiempo, que es la versión mejorada de la señal original.

##  Fórmulas Importantes

### Potencia de la Señal:
La potencia de una señal \( x(n) \) se calcula con la fórmula:

<div align="center">
  <img src="https://github.com/user-attachments/assets/469cbc91-d496-480f-96cf-6203e27ecb28" width="400">
</div>

Donde:

- \( P_x \) es la potencia.
- \( x(n) \) es la señal en el instante \( n \).
- \( N \) es el número total de muestras.

---

### Transformada Rápida de Fourier (FFT):
Para pasar una señal del dominio del tiempo al dominio de la frecuencia, se utiliza la FFT:

<div align="center">
  <img src="https://github.com/user-attachments/assets/bed3d240-8288-4c17-b333-34b90f550fc6" width="500">
</div>

### Beamforming (Retardo de la Señal):
El retardo aplicado a las señales captadas por micrófonos se calcula en función de la distancia \( d \) entre ellos y la velocidad del sonido \( v \):

<div align="center">
  <img src="https://github.com/user-attachments/assets/4fb54c1e-8170-474b-a2ab-9179cabf4c27" width="400">
</div>

### Relación Señal/Ruido (SNR):
La relación señal/ruido SNR se calcula en dB como:

<div align="center">
  <img src="https://github.com/user-attachments/assets/457f5a19-12d1-4020-a981-3234372344a8" width="400">
</div>

###  Configuración del Sistema

##  Interfaz de Audio


### Interfaz de Audio: Behringer UMC202HD
<div align="center">
  <img src="https://github.com/user-attachments/assets/5d9ba424-a3c8-440a-93fe-ce6e960f4862" width="500">
</div>

### Micrófono 1: SM-8B Takstar
<div align="center">
  <img src="https://github.com/user-attachments/assets/b8158f7a-d3c0-43a7-949d-895c40707105" width="500">
</div>

### Micrófono 2: Shure
<div align="center">
  <img src="https://github.com/user-attachments/assets/7a0a38b7-1a2f-461d-9e25-141e2b9bfdb6" width="500">
</div>

###  Distancias y Configuración

- **Distancia entre micrófonos**: 2 metros

- **Distancias entre las fuentes de sonido y micrófonos**:
  - **Fuente 1 (Juan Esteban)**:
    - Distancia a Micrófono 1: 3-4 metros
    - Distancia a Micrófono 2: 2 metros

  - **Fuente 2 (Voz mujer)**:
    - Distancia a Micrófono 1: 2 metros
    - Distancia a Micrófono 2: 0.5 metro

###  Descripción de la Configuración

La configuración del sistema está diseñada con rigurosidad y se detalla de la siguiente manera:

- **Micrófonos**: Se utilizan dos micrófonos, un SM-8B Takstar y un micrófono Shure.
- **Fuentes de Sonido**: Se han ubicado dos fuentes de sonido, cada una a diferentes distancias de los micrófonos para evaluar su impacto.
- **Distancias**: Las distancias entre los micrófonos y las fuentes de sonido se han definido con precisión para permitir una evaluación efectiva del beamforming. Las distancias varían desde 0.5 metros hasta 4 metros, proporcionando un rango completo para el análisis de la señal.

##  Orientación Gráfica de Micrófonos y Fuentes

<div align="center">
  <img src="https://github.com/user-attachments/assets/379a93ff-aa06-4735-a3db-19f142a16a99" width="500">
</div>

### Descripción de la Configuración

La gráfica muestra la disposición de los micrófonos y fuentes de sonido en el entorno de prueba:

- **Micrófono 1 (SM-8B Takstar)** y **Micrófono 2 (Shure)** están ubicados a distancias específicas de las fuentes.
- **Fuente 1 (Juan Esteban)** y **Fuente 2 (Voz femenina)** están situadas en distintas posiciones con respecto a los micrófonos.

Configuración del Sistema de Adquisición
El sistema de adquisición de datos se describe con los siguientes criterios:

## Criterios de Digitalización
## Frecuencia de Muestreo: 44,100 Hz
Esta frecuencia de muestreo es estándar para la mayoría de las grabaciones de audio digital, proporcionando una resolución adecuada para capturar detalles en el rango auditivo.

## Tiempo de Captura: 10 segundos
El tiempo de captura define la duración de la grabación. Se ha establecido un periodo de 10 segundos para asegurar que se capturen suficientes datos para el análisis.

## Número de Canales: Mono (1 canal)
El audio se ha grabado en formato mono, utilizando un único canal de audio.

## Grabación en Audacity
Los audios fueron grabados utilizando Audacity, una aplicación de edición de audio de código abierto. Esta herramienta permitió capturar las señales de los micrófonos en formato mono con los parámetros especificados, asegurando una grabación de alta calidad para el análisis posterior.

##  Archivos en el Proyecto

- `audio1.wav` - Primer archivo de audio de entrada.
- `audio2.wav` - Segundo archivo de audio de entrada.
- `ruido.wav` - Archivo de ruido que será sumado a los audios de entrada.
- `audio_mezclado.wav` - Resultado de mezclar las señales de audio con el ruido.
- `audio_beamformed.wav` - Archivo resultante tras aplicar beamforming.

##  Funcionalidades del Código
- **Mezcla de Audio**: Las señales de audio (audio1 y audio2) se mezclan con ruido para simular una señal contaminada.
- **Beamforming FFT**: Se aplica beamforming en el dominio de la frecuencia utilizando la Transformada Rápida de Fourier (FFT) para aislar la señal deseada.
- **Cálculo de Potencia y SNR**: Se calculan las potencias y la relación señal/ruido (SNR) de cada señal antes y después de aplicar beamforming.
- **Visualización**: Gráficas en escala semilogarítmica del espectro de frecuencia de las señales procesadas.

##  Ejecución del Proyecto

1. Coloca los archivos de audio en la carpeta `audios/` dentro del directorio raíz del proyecto.
2. Asegúrate de tener instaladas las siguientes librerias:
   ```bash
   pip install numpy matplotlib soundfile


###  Mejora del SNR
Tras aplicar el beamforming, se mide la mejora de la relación señal-ruido (SNR) para cada una de las señales procesadas.

### Ejemplo de salida del código:
```plaintext
Potencia de audio1: 0.003391749316358627
Potencia de audio2: 0.001645232435617203
Potencia de ruido: 4.226501938593041e-06
Potencia de audio mezclado: 0.005340377730770212
Potencia de la señal aislada: 0.0013344059571859226
SNR de audio1: 29.04 dB
SNR de audio2: 25.90 dB
SNR de audio mezclado: 31.02 dB
SNR de la señal aislada: 24.99 dB

```
##  Análisis de Potencia y Relación Señal-Ruido (SNR)

### Potencia de las Señales

- **Potencia de audio1**: `0.00339`
  - La potencia de la señal `audio1` es relativamente alta comparada con las otras señales. Esto indica que `audio1` tiene una amplitud significativa en comparación con las otras señales.

- **Potencia de audio2**: `0.00165`
  - La potencia de la señal `audio2` es menor que la de `audio1`, lo que sugiere que `audio2` tiene una menor amplitud en comparación con `audio1`. Esto puede ser debido a diferencias en la distancia o la sensibilidad del micrófono.

- **Potencia de ruido**: `4.23 × 10⁻⁶`
  - La potencia del ruido es considerablemente baja en comparación con las señales de audio. Esto es esperado, ya que el ruido debe tener menos impacto en la señal final en comparación con las señales de audio principales.

- **Potencia de audio mezclado**: `0.00534`
  - La potencia de la señal mezclada, que es la combinación de `audio1`, `audio2`, y el ruido, es la mayor entre las medidas. Esto se debe a que la mezcla incluye tanto las señales de audio como el ruido, lo que incrementa la potencia total.

- **Potencia de la señal aislada**: `0.00133`
  - La potencia de la señal aislada, que es el resultado del beamforming, es menor que la de la señal mezclada pero similar a la de `audio2`. Esto sugiere que el beamforming ha logrado reducir la potencia general al eliminar componentes no deseados, pero aún conserva una parte significativa de la señal deseada.

### Relación Señal-Ruido (SNR)

- **SNR de audio1**: `29.04 dB`
  - Un SNR de `29.04 dB` para `audio1` indica una buena calidad de señal con un ruido relativamente bajo en comparación con la señal de audio. Este valor sugiere que la señal de `audio1` es clara y con un buen nivel de detalle.

- **SNR de audio2**: `25.90 dB`
  - El SNR de `25.90 dB` para `audio2` es algo menor que el de `audio1`, lo que puede indicar que hay un poco más de ruido en `audio2`
- **SNR de audio mezclado**: `31.02 dB`
  - El SNR de `31.02 dB` para la señal mezclada es el más alto de todos, y puede ser resultado de la combinación específica de las señales de audio y el ruido. Normalmente, el SNR aumenta al combinar varias señales.

- **SNR de la señal aislada**: `24.99 dB`
  - El SNR de la señal aislada es el más bajo entre las medidas, lo cual indica que, aunque el beamforming ha reducido el ruido, la señal final aún tiene una cantidad notable de ruido residual. Esto puede ser una indicación de que el beamforming no eliminó todo el ruido presente en la señal.


 Detalles Técnicos del Script
1. Cálculo de Potencia:
El cálculo de la potencia de cada señal (audio1, audio2, ruido) se realiza mediante la función calcular_potencia().

2. Transformada de Fourier (FFT):
Se aplica la FFT para convertir las señales del dominio temporal al dominio frecuencial, lo cual es clave para el beamforming basado en frecuencias.

3. Beamforming FFT:
La función beamforming_fft() aplica el beamforming en el dominio de la frecuencia, calculando retardos y combinando señales de diferentes micrófonos para mejorar la señal deseada.

 Resultados
 Gráficas Generadas

## Dominio del Tiempo

Se generan gráficos para visualizar las señales en el dominio del tiempo. Estos incluyen:
- **Audio 1**: La señal original captada por el primer micrófono.
- **Audio 2**: La señal original captada por el segundo micrófono.
- **Audio Mezclado**: La señal resultante de la combinación de audio1, audio2 y ruido.
- **Ruido**: La señal de ruido independiente.
- **Señal Beamformed**: La señal aislada tras aplicar el beamforming.

Estas gráficas muestran la amplitud de las señales a lo largo del tiempo, permitiendo comparar la señal original, la mezclada con ruido y la procesada.



Estos gráficos permiten observar las diferencias en la amplitud de las frecuencias para cada señal, mostrando con claridad cómo el contenido frecuencial se ve afectado por el ruido y el procesamiento.
Se generan gráficos para las señales originales, el ruido, la señal mezclada con ruido y la señal procesada con beamforming.
![tiempo](https://github.com/user-attachments/assets/45385978-91c3-47aa-9caa-bc8db643435a)

El dominio del tiempo muestra cómo cambia la amplitud de la señal a lo largo del tiempo. Cada gráfico tiene en su eje horizontal el tiempo (segundos) y en el eje vertical la amplitud (voltios). El análisis de estas gráficas en el dominio del tiempo es útil para visualizar la dinámica de la señal: cómo crece, disminuye, se estabiliza o varía en términos de volumen y características temporales.

En la señal azul y verde encontramos los audios 1 y 2 respectivamente, estos tiene varias fluctuaciones debido a que tiene contenido sonoro. 

La señal gris es el ruido que se caracteriza por una amplitud constante sin grandes variaciones a lo largo del tiempo. 

La señal morada es la mezcla se la señal del audio 1, 2 y ruido, podemos observar un comportamiento más complejo, con picos más pronunciados al inicio y después cierta estabilización.

La mezcla de los audios parece generar una señal más energética y densa, lo que es común cuando se suman señales de diferentes fuentes.

Finalmente, la señal Beamformed que es la señal aislada, notamos que tiene ciertas similitudes con el Audio Mezclado, pero parece más limpia y más estructurada, lo cual indica que el proceso de beamforming ha eliminado parte del ruido y de las interferencias.
La señal muestra amplitudes más moderadas y menos distorsión, lo que sugiere que la técnica ha mejorado la calidad de la señal al dirigirla hacia una fuente de sonido específica.

#### Espectro de Frecuencia (FFT)
Se generan gráficos en escala semilogarítmica para representar el espectro de frecuencia de cada señal:
- **Audio 1**: El espectro de frecuencia de la primera señal.
- **Audio 2**: El espectro de frecuencia de la segunda señal.
- **Ruido**: El espectro de frecuencia del ruido.

## Gráficos en escala semilogarítmica de las señales y del ruido

Los gráficos de las señales y el ruido se representan en escala semilogarítmica para resaltar la amplitud de las distintas frecuencias. Esto permite observar con mayor claridad las diferencias en los espectros de cada señal procesada.
A continuacón encontraremos las gráficas del espectro de frecuencias para la señal del audio 1, audio 2 y el ruido.
![espectro](https://github.com/user-attachments/assets/d6604641-6126-4bbc-a0aa-b99788fa12a7)

La escala semilogarítmica en el eje es ideal para representar espectros de frecuencia porque distribuye las frecuencias de manera más equitativa. Con una escala semilogarítmica, tanto las bajas como las altas frecuencias son más visibles y comparables. Esto facilita identificar detalles importantes en todo el rango de frecuencias, como los picos dominantes, que serían menos perceptibles en las altas frecuencias usando una escala lineal.

La escala semilogarítmica permite observar cómo se distribuye la energía en diferentes rangos de frecuencia. En las tres gráficas, se puede apreciar cómo la energía está concentrada en ciertos rangos de frecuencia, con un detalle importante en los picos a bajas y medias frecuencias, mientras que las altas frecuencias muestran una caída más suave y progresiva. 

 Por ejemplo, los picos de los audios en las bajas y medias frecuencias son mucho más claros, mientras que el ruido presenta un espectro más distribuido. La escala semilogarítmica ayuda a visualizar estas diferencias de manera más equitativa, destacando tanto las frecuencias bajas como las altas en un solo gráfico.
 
En la siguiente imagén encontraremos las gráficas del espectro de frecuencias para la señal mezclada y la señal final o aislada.

![espectro mezcla y aislada](https://github.com/user-attachments/assets/7904d6bd-9ef3-4ab5-8abf-32d23e363087)

La señal mezclada y la señal aislada tienen un espectro muy similar pero magnitudes muy diferentes. La razón por la cual la magnitud de la señal aislada es menor (llegando a aproximadamente 800 m^2/Hz en el gráfico) que la de la señal mezclada (que llega a 1750) tiene que ver con varios factores. 

Al aplicar beamforming, parte del ruido y otras señales fuera de la dirección focalizada se atenúan. Esto reduce la potencia total de la señal, lo que explica la disminución en la magnitud del espectro de frecuencia. 

En el proceso de beamforming, las fases de las señales se ajustan para que las señales provenientes de la dirección objetivo se sumen constructivamente, mientras que las señales que provienen de otras direcciones pueden sumarse destructivamente. Esto contribuye reducción en la magnitud total de la señal.

Cuando las señales de los micrófonos están en fase después de aplicar el retardo adecuado (delays), las componentes de frecuencia se alinean correctamente, y la magnitud de la señal resultante será mayor. Este es el proceso de suma constructiva que refuerza la señal de interés. Pero cuando las señales de los micrófonos no están en fase correcta después de aplicar los retardos, entonces se cancelarán entre sí en ciertos puntos, reduciendo la magnitud de la señal resultante. Este es el proceso de suma destructiva.

En cuanto al espectro de frecuencia las señales son muy similares pues la señal aislada sigue capturando las frecuencias dominantes de los audios originales (audio 1 y 2), ya que el beamforming está diseñado para resaltar las señales deseadas y reducir el ruido.
Las frecuencias dominantes en los audios originales están presentes en ambas señales (mezclada y beamformed) porque el beamforming no elimina esas frecuencias, sino que las mantiene al intentar focalizarlas.

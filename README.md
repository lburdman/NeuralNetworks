# **Redes Neuronales**
## **Descripción General**
Este repositorio contiene el código fuente de varios tipos de redes neuronales, implementadas como parte de mi curso en Ingeniería Electrónica en la Universidad de Buenos Aires. Estos modelos cubren desde el perceptrón simple hasta redes neuronales complejas como las redes de Hopfield y redes de Kohonen, ofreciendo ejemplos prácticos y resultados de experimentos que buscan ilustrar cómo funcionan estas redes y cuál es su aplicación en el aprendizaje automático.


## 1. Perceptrón simple y multicapa
El Perceptrón es uno de los primeros modelos de redes neuronales y el punto de partida para entender conceptos básicos del aprendizaje supervisado. 

La topología de red de una neurona muesta que cada entrada se multiplica por su peso sináptico y luego se calcula _h_ como
$h = \sum_{j=1}^M w_jx_j$. Así, se evalúa el signo de _h_ a través de la función de activación, que evaluará
el signo de h. Si es positivo la salida será 1 y si es negativo -1.

<image
src="/images/simplePerceptron.png"
alt="Perceptron Simple"
caption="**Figura 1**: Perceptron Simple">

Para actualizar los pesos sinápticos, se resta el valor de salida obtenido con la salida
deseada del patrón de entrada que esta siendo evaluado. Si el error del patrón no es nulo,
cada coeficiente wi se actualiza como:

$\Delta w_j(k) = \eta · x_j · (y_{deseada} − y_{obtenida}) $

$w_j(k) = w_j(k − 1) + \Delta w_j(k)$

El parámetro $\eta$ es la tasa de aprendizaje. Mientras sea menor, toma más iteraciones en converger a una solución posible, dado que determina que tanto se modifica el valor de los pesos sinápticos (es decir, cuánto se rota el plano de la recta discriminadora).

Es importante notar que esta topología encuentra solución solo para problemas linealmente separables, de no ser así el perceptrón simple será incapaz de encontrar una solución con error total nulo.

<details>
    
  <summary>1.1. Perceptrón simple</summary>
    
  Se entrenaron perceptrones para resolver funciones lógicas AND y OR con 2 y 4 entradas.
  En la implementación, se analizaron las tasas de aprendizaje y cómo estas influyen en la convergencia hacia la solución. Se puede ver la evolución del error a medida que la red ajusta sus pesos sinápticos.

  <image
  src="/images/output_AND_2inputs.png"
  alt="Resultado del entrenamiento AND 2 entradas"
  caption="**Figura 1.1.1**: Resultado del entrenamiento para AND 2 entradas">

  <image
  src="/images/error_AND_2inputs.png"
  alt="Evolución del error global para AND de 2 entradas"
  caption="**Figura 1.1.2**: Evolución del error del Perceptrón durante el entrenamiento">

  <image
  src="/images/weights_OR_4in.png"
  alt="Evolución de los pesos sinápticos OR 4 entradas"
  caption="**Figura 1.1.3**: Evolución de los pesos sinápticos OR 4 entradas">

  **Capacidad**
  
  La capacidad da idea de que cantidad de patrones aleatorios se puede esperar que aprenda el perceptrón en una red neuronal de cierto tamaño.
  Entrenando un modelo simple con patrones de diferentes tamaños, se evalúa si el perceptrón pudo aprender sin errores. A medida que se aumenta el número de patrones, se observa cómo cambia la capacidad, reflejando la efectividad del perceptrón para clasificar los patrones. Los resultados muestran la relación entre el tamaño de los patrones y el rendimiento del perceptrón.
  
  <image
  src="/images/capacity_perceptron.png"
  alt="Capacidad del perceptron simple"
  caption="**Figura 1.1.4**: Capacidad del perceptron simple para N = 40">

  Es importante destacar que en todos los casos, entrenando una red de _N_ entradas, el perceptron simple es capaz de aprender hasta _2N_ patrones.

<details>
  
  <summary>1.2. Perceptrón Multicapa</summary>
    
  Para problemas que **no** son linealmente separables, como la función lógica XOR, se entrenó un perceptrón multicapa.
    
  Utilizando el algoritmo de backpropagation, se demuestra cómo esta red puede aprender relaciones más complejas. El perceptrón multicapa cuenta con capas ocultas que permiten que los datos sean transformados de una manera que permita la clasificación correcta.

  <image
  src="/images/multilayerTopology.png"
  alt="Topología de red de perceptron multicapa"
  caption="**Figura 1.2.1**: Topología de red de perceptron multicapa">

  Para visualizar el efecto del cambio de los pesos sinápticos, se eligieron dos pesos aleatorios y se realiza el gráfico variando levemente sus valores para explorar el espacio de soluciones, y obtener los mínimos y en que región esos pesos sinápticos pueden variar sin afectar al error global.
  
  <image
  src="/images/error_XOR_3D.png"
  alt="Mapa de error al variar el valor de dos pesos sinápticos"
  caption="**Figura 1.2.2**: Mapa de error al variar el valor de dos pesos sinápticos">

  
  <image
  src="/images/error_XOR.png"
  alt="Mapa de error al variar el valor de dos pesos sinápticos"
  caption="**Figura 1.2.3**: Mapa de error al variar el valor de dos pesos sinápticos en 2D">

  Este desarrollo y más puede encontrarse en el archivo `perceptron.ipynb` donde con otros ejemplos prácticos también se analiza:
  - Implementación de red con backpropagation para aprender una función continua. Análisis de minibatch.
  - Optimización por algoritmo genético. Análisis de mutación, crossover y tamaño de población.

</details>

## 2. Redes de Hopfield

Las Redes de Hopfield se destacan por su capacidad para actuar como una memoria asociativa, un concepto que puede entenderse como una "memoria de contenido direccionable".



Características Principales
Aprendizaje de Patrones: Se entrenó una red de Hopfield para almacenar patrones binarios y recuperarlos incluso cuando están incompletos o con ruido.

(Figura 3: Recuperación de un patrón almacenado con ruido aplicado)

Estados Espurios: Durante los experimentos, se observó la presencia de estados espurios. Estos son estados no deseados que la red puede alcanzar, y son el resultado de la combinación no lineal de los patrones aprendidos. Estos estados afectan la capacidad de la red para converger siempre a los patrones deseados, especialmente si la información de entrada es incompleta o ruidosa.

Capacidad de la Red: Se evaluó la capacidad de la red para almacenar múltiples patrones y cómo esta capacidad cambia cuando se eliminan sinapsis al azar.

Archivos relevantes:

hopfieldNetwork.ipynb — Implementación de la red de Hopfield, incluyendo ejemplos de recuperación de patrones distorsionados y análisis de estados espurios.
Redes de Kohonen
Las Redes de Kohonen, también conocidas como Mapas Autoorganizados (SOM), se utilizan para la reducción de dimensionalidad y la visualización de datos.

Ejemplos Implementados
Preservación de Topología:

Las redes de Kohonen se entrenaron con datos distribuidos uniformemente en distintas figuras geométricas, como el círculo unitario, el anillo y el triángulo equilátero.
Se pudo observar cómo la red ajusta sus pesos para representar correctamente la topología de los datos de entrada, formando mapas que respetan la estructura original de los datos.

(Figura 4: Evolución de la Red de Kohonen con datos distribuidos en un círculo)

Problema del Viajante (Traveling Salesman Problem):

Una red de Kohonen se utilizó para aproximar una solución al Problema del Viajante con un conjunto de ciudades. La red ajusta sus conexiones para encontrar un recorrido eficiente que minimice la distancia total recorrida.

(Figura 5: Red de Kohonen aplicada al Traveling Salesman Problem)

Archivos relevantes:

kohonenNetwork.ipynb — Código que muestra cómo entrenar redes de Kohonen para la preservación de topología y la resolución del problema del viajante.
Referencias y Papers Fundamentales
Este repositorio se basa en los siguientes papers que proporcionan las bases teóricas de los modelos implementados:

J.J. Hopfield (1982). Neural Networks and Physical Systems with Emergent Collective Computational Abilities. Acceder al PDF
T. Kohonen (1982). Self-Organized Formation of Topologically Correct Feature Maps. Acceder al PDF
Ambos trabajos son pilares en el desarrollo de las redes neuronales, proporcionando tanto una visión matemática como experimental de sus capacidades.

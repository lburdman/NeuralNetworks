# **Redes Neuronales**
## **Descripción General**
Este repositorio contiene el código fuente de varios tipos de redes neuronales, implementadas como parte de mi curso en Ingeniería Electrónica en la Universidad de Buenos Aires. Estos modelos cubren desde el perceptrón simple hasta redes neuronales complejas como las redes de Hopfield y redes de Kohonen, ofreciendo ejemplos prácticos y resultados de experimentos que buscan ilustrar cómo funcionan estas redes y cuál es su aplicación en el aprendizaje automático.

- [Perceptron simple y multicapa](docs/perceptron.md)
- [Perceptron simple y multicapa](docs/hopfield.md)

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

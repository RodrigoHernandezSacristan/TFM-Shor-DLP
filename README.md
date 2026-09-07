# TFM-Shor-DLP
## Trabajo de Fin de Máster: *Implementación del algoritmo de Shor para resolver el problema del logaritmo discreto.*

### Portada
- **Nombre:** Rodrigo Hernández Sacristán
- **Máster:** Computación Cuántica
- **Universidad:** Universidad Internacional de la Rioja (UNIR)
- **Tutor:** Rodrigo Gil-Merino y Rubio
- **Cotutor:** Luis Hernández Encinas
- **Curso:** 2025/2026

### Descripción

El problema del logaritmo discreto (DLP) es uno de los principales problemas utilizados en criptografía y consiste en lo siguiente: 
"Dado un número primo $p$, un generador $g$ de $\mathbb{Z}_p^{\star}$ y un elemento $h$ de $\{Z}_p^{\star}$, encontrar un entero $x$ tal que $0\leq x \leq p-2$ tal que $g^{x}=h\pmod{p}$."

La seguridad de criptosistemas muy importantes y utilizados como Diffie-Hellman, ElGamal o el Algoritmo estándar de firma digital basan su seguridad en la enorme complejidad de resolver este problema, tal es la dificultad de hacerlo que no existen algoritmos implementables en ordenadores clásicos que lo resuelvan en tiempo polinómico; sin embargo, Peter Shor en la última década del Siglo XX desarrolló a nivel teórico un algoritmo cuántico (el algoritmo de Shor para resolver el DLP) que resolvía este problema en tiempo polinómico gracias al poder computacional que rigen las leyes de la computación cuántica.

Este TFM trata la implementación de dicho algoritmo para ejemplos de salón, puesto que aún no es posible resolver este problema con parámetros reales debido a limitaciones tecnológicas, y en este repositorio se exponen los programas realizados para ello cuyo fundamento teórico y explicación de los resultados obtenidos se desarrollan al detalle en la memoria del Trabajo. 

### Versión de Python y librerías utilizadas.

Para la programación de los Jupyter Notebook se ha usado la versión 3.14.6 de Python y las siguientes librerías, aunque vendrán explicitadas en cada archivo .ipynb: 

```python
import numpy as np
import math
import matplotlib.pyplot as plt
from qiskit import QuantumCircuit, QuantumRegister, ClassicalRegister
from qiskit.circuit.library import UnitaryGate
from qiskit.circuit.library import QFTGate
from qiskit_aer import AerSimulator
from qiskit import transpile
from qiskit.visualization import plot_histogram
from IPython.display import display
from qiskit.quantum_info import Operator
from qiskit.circuit.library import QFT
import warnings
import random
from collections import Counter
import sys
```

### Estructura del repositorio

Tal y como adelantamos, la justificación y explicación de cada notebook, junto con los resultados obtenidos, se desarrollan en detalle en la memoria del TFM. Aun así, recordemos brevemente en qué consiste cada archivo del repositorio:

- **oraculo_matrices**, **oraculo_beauregard** y **oraculo_montgomery** contienen la programación de los oráculos encargados de realizar la exponenciación modular del algoritmo de Shor.
- **comparativa_oraculos** presenta una comparación entre los tres oráculos implementados en términos del número de cúbits, la profundidad del circuito y las puertas cuánticas que requiere cada uno.
- **Implementacion_Shor_Especial_DLP** implementa en simulador el caso especial del algoritmo de Shor para resolver un problema de salón sobre $p=17$.
- **Shor_general_simulacion_primo_mas_grande** resuelve en simulador el caso general del DLP para los parámetros más grandes posibles con cada oráculo.
- **Shor_simulacion_real** resuelve en simulador los mismos problemas que el archivo anterior, pero mostrando una gráfica de los resultados para poder compararlos con los obtenidos al ejecutar en hardware real.
- **Shor_ejecucion_real** resuelve estos mismos ejemplos de salón utilizando un ordenador cuántico real, mediante el servicio gratuito mensual de IBM.
- **Shor_ejecucion_variando_h** resuelve en simulador diferentes problemas sustentados sobre el mismo grupo, con el fin de analizar cómo se obtienen las soluciones: si por despeje directo o mediante el Teorema chino de los restos.
- Por último, **Shor_conjetura_primos_seguros** recoge los experimentos que nos han permitido enunciar la Conjetura sobre los primos seguros.

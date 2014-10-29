# Python Científico: migrando de Matlab a Python 

## Brief Outline
El uso de Python dentro del campo de la Computación Científica ha progresado durante los últimos años hasta permitir el reemplazo casi total de las herramientas utilizadas hasta el momento. Sin embargo, la migración a un entorno Python en este campo suele presentar algunas dificultades. En esta charla analizaremos algunas de ellas, presentando algunas soluciones que se encontraron para mitigarlas.

## Abstract
### Aplicaciones de Computación Científica

Computación Científica es la ciencia aplicada que se encarga de desarrollar los modelos matemáticos y computacionales de los procesos vinculados a problemas científicos o tecnológicos.

Desde esta perspectiva la computación se transforma en una herramienta para el científico que le permite modelar y simular los problemas que está estudiando. El científico utiliza esta herramienta para:

- Obtener o generar datos de prueba
- Manipular y procesar estos datos
- Visualizarlos de forma amigable

Todo esto, con la intención de lograr una mejor comprensión y entendimiento del problema.
Estas características determinan que el desarrollo de una aplicación científica presente otros requerimientos u objetivos que lo diferencian, por ejemplo, del desarrollo de una aplicación web o desktop.

### Diferencias entre Matlab y Python

Históricamente, la herramienta que logró una mayor aceptación dentro del ambiente científico para este tipo de tareas fue Matlab (o su “versión” open-source: Octave). En los últimos años, la comunidad Python ha desarrollado un conjunto de librerías que abarcan casi totalmente las funcionalidades de Matlab y sus extensiones. Sin embargo, por su naturaleza y propósitos, Python presenta varias diferencias con respecto a Matlab:

- Intérprete
- Interfaz Gráfica
- Librerías
- Sintaxis del lenguaje

### Por qué Python?

Entre muchas de las ventajas que posee Python podemos enumerar las siguientes:

- Libre y gratis
- Portable
- Lenguaje:
    1. De propósito general
    1. Fácil de aprender, alto nivel
    1. Multiparadigma
    1. Interpretado
    1. Interactivo
- Biblioteca para áreas específicas
- Comunidad

### Migración de Código

La migración de código Matlab a código Python no es un proceso trivial. Si bien las librerías científicas de Python (Numpy, Scipy Matplotlib) están implementadas de manera tal que las funciones respeten una signatura (parámetros de entrada y de salida) similar a las funciones de Matlab, se presentan algunas diferencias que impiden la migración automática.

En este aspecto, se evaluaron varias herramientas que hubieran permitido hacer la migración en forma automática pero todas presentaron algún inconveniente o requerían de alguna configuración manual.

Debido a que la cantidad de scripts a migrar no era elevada y para lograr un mayor entendimiento de los mismos, se eligió migrarlos manualmente. La tarea no resultó complicada debido a las similitudes de sintaxis a las que nos referimos anteriormente.

Para comprobar la correctitud de los scripts se implementó una batería de tests, que permitió contrastar los resultados con los generados por matlab.

## Notas

- La exposición será acompañada de ejemplos y problemas reales con los que nos fuimos encontrando al querer migrar de un entorno Matlab a un entorno Python, dentro de un proyecto de modelado y simulación de una red de fibra óptica (ARSAT-FOP).
- Esta es la primera presentación que realizo dentro de una conferencia Python. Suelo dar charlas sobre diversos temas de mi interés dentro de mi ambiente laboral, como así también para los clientes. Además fui docente de la Facultad de Ciencias Exactas y Naturales de la UBA.
- Les paso los links de los notebooks de una capacitación similar que dimos para el cliente. La misma, estuvo enfocada en presentar las diferencias del entorno Python con respecto a Matlab y justificar la elección de Python (duración aproximada 3 horas). En la presentación para SciPyCon voy a ser mucho más breve, enfocándome principalmente en los problemas de más alto nivel y no tanto en las diferencias propias de los lenguajes.

    [https://github.com/hexacta/python-para-cientificos](https://github.com/hexacta/python-para-cientificos "Python para Científicos (IPython Notebook)")

- Planeo mostrar algunos ejemplos de los códigos migrados, para ejemplificar la similitud de los mismos. Además, si cuento con el tiempo suficiente podría mostrar algunas métricas y opciones para optimizar la performance que evaluamos en nuestro proyecto en particular.

#### Cronograma de la charla (duración total: 45 min)
1. Introducción (5 min)
    1. Quien soy?
    1. Problemática y contexto
1. Computación científica (5 min)
    1. Definición
    1. Necesidades de un científico
1. Diferencias y similitudes entre Matlab y Python (10 min)
    1. Diferencias básicas
    1. Entorno de trabajo
1. Por qué elegimos Python (10 min)
    1. Ventajas
    1. Desventajas
1. Migración de código (10 min)
    1. Migración automática o manual
    1. Testing
1. Ejemplos (5 min)
    1. Ejemplos de scripts migrados
    1. Gráficos de performance
    1. Otras optimizaciones analizadas


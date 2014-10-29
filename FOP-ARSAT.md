FOP-ARSAT: Simulando la Red Federal de Fibra Óptica usando Python
=================================================================

Audience Level: Intermediate

Brief Outline
-------------

La  Red Federal de Fibra Óptica (ReFeFO) es una red multipropósito, que permite la conexión de instituciones públicas. En esta charla se presentará una aplicación, completamente implementada en Python,  para diseñar y simular esta red. Se analizarán los problemas de escalabilidad y performance que afrontamos, las soluciones propuestas para resolverlos y las herramientas utilizadas.


Abstract
--------

### Contexto y Problemática

El proyecto ARSAT-FOP está siendo desarrollado por la empresa Hexacta para el cliente ARSAT. El objetivo es generar una herramienta para la simulación de la propagación de la luz en fibras de silicio, que permitirá simular la Red Federal de Fibra Óptica. Se espera que pueda ser utilizado por todas aquellas personas involucradas en el desarrollo y mantenimiento de la Red, por investigadores y para fines educativos.

La aplicación permite

- Diseñar mediante una herramienta gráfica tipo _"case"_ una topología de componentes, donde el usuario puede conectarlos de manera visual.

- Simular la propagación en guías unidimensionales bajo diversos regímenes de potencias y duraciones de pulso. Está simulación se realiza mediante una familia de algoritmos que ejecutan cálculos matemáticos, principalmente, operaciones matriciales y transformadas de Fourier. Estos  algoritmos se encuentran desarrollados en Matlab y el presente proyecto también prevé su migración a Python.

### Arquitectura

Inicialmente se pensó la arquitectura para una aplicación desktop pero analizando la naturaleza de algunos requerimientos se optó por una arquitectura web.

La solución está ideada priorizando:

- Escalabilidad: fundamentalmente para el modo _"Software as a Service"_ donde se podrá maximizar el poder de cómputo utilizando el entorno de ARSAT.

- Accesibilidad: se espera que la herramienta pueda ser utilizada en forma colaborativa entre diferentes usuarios.

- Extensibilidad: la herramienta será open-source, por lo cual es importante detectar cada uno de los componentes involucrados, asignarles responsabilidades concretas y vincularlos en forma clara.

### Diseño


La aplicación se divide en tres módulos principales:

- FOP: su responsabilidad es brindarle al usuario una interfaz web amigable para el diseño de una red de componentes. Presenta y administra de manera sencilla los componentes que el usuario puede utilizar, permite su modificación y la creación de nuevos componentes. Persiste los diagramas y los componentes generados por los usuarios. Finalmente, es la encargada de exponer el estado de una simulación en progreso.

- Simulator: su responsabilidad es organizar un plan de ejecución (simulación) a partir de un diagrama de componentes, intentando maximizar el paralelismo en la ejecución de los mismos. Funciona de forma asincrónica recibiendo pedidos de simulación mediante una interfaz REST. Mantiene el estado de las ejecuciones solicitadas.

- Engines: son los encargados de ejecutar los componentes. Reciben pedidos de ejecución por parte del simulador, los ejecutan y devuelven los resultados. Permiten la ejecución en paralelo de diversos componentes, dentro de un ambiente controlado. 

### Por qué Python?

El proyecto fue completamente desarrollado en Python utilizando únicamente software open-source.
Se decidió utilizar Python por varias razones:

1. es un lenguaje sumamente flexible, lo que permite usarlo como lenguaje base para diferentes tipos de aplicaciones (web, desktop, científicas)

2. es de fácil aprendizaje, permite generar código simple y legible, lo que favorece la colaboración en proyectos open-source.

3. cuenta con librerías para cálculo científico (numpy, scipy, matplotlib, etc) que permiten migrar fácilmente los scripts de Matlab 

#### Librerías utilizadas

- FOP: se utilizaron diferentes librerías de javascript para lograr una interfaz simple e intuitiva. La administración de usuarios, diagramas y componentes se desarrolló en una aplicación Django.

- Simulator: se optó por el framework Bottle para implementar una interfaz REST sencilla y liviana. Para administrar los pedidos de ejecuciones se usaron colas de tareas de Celery. Finalmente se aprovecharon las capacidades de IPython Parallel para ejecutar componentes en paralelo.

- Engines: son instancias de engines de IPython que reciben pedidos de ejecuciones. Tienen precargadas y permiten hacer uso de librerías de cálculo científico y graficación tales como: numpy, scipy, matplotlib.

Additional Notes
----------------

Consideraciones:

- Si bien en un principio el proyecto ARSAT-FOP será utilizado en un entorno cerrado dentro de ARSAT se planea lanzarlo como open-source y abrirlo a la comunidad.

- Esta es la primera presentación que realizo dentro de una conferencia Python. Suelo dar charlas sobre diversos temas de mi interés dentro de mi ambiente laboral, como así también para los clientes. Además fui docente de la Facultad de Ciencias Exactas y Naturales de la UBA.

- Les adjunto las slides de una exposición similar que dimos para el cliente. La misma estaba enfocada en la explicación de la arquitectura. En esta charla pretendo enfocarme mayormente en los usos de ARSAT-FOP y la utilización de Python para su implementación.

- Planeo mostrar algunas imágenes de la interfaz gráfica de la aplicación para que los usuarios se hagan una mejor idea de cómo es el funcionamiento de la misma, pero no pretendo hacer una demostración para evitar demoras en la charla.

Cronograma (duración total: 45 min)

1. Introducción (5 min)
    1. Quien soy?
    2. Qué es Hexacta? Que es ARSAT? 
    3. Qué es la ReFeFO?
2. Contexto y Problemática? (10 min)
    1. Por qué simular la Red de Fibra Óptica?
    2. Cómo se hacía hasta ahora?
    3. Cuales son los objetivos de nuestro proyecto?
3. Arquitectura: requerimientos (10 min)
    1. Cuáles son los requerimientos de nuestra arquitectura?
    2. Por qué se eligió una arquitectura web?
4. Diseño: módulos de la aplicación (10 min)
    1. FOP
    2. Simulator
    3. Engines
5. Por qué Python? (10 min)
    1. Razones por las que usamos Python
    2. Librerías utilizadas en cada módulo

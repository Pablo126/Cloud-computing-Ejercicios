# Cloud Computing
## Ejercicios tema 1

### Ejercicio 1

#### Buscar una aplicación de ejemplo, preferiblemente propia, y deducir que patrón es el que usa. ¿Qué habría que hacer para evolucionar a un patrón tipo microservicios?

[PyScrabble](https://github.com/Pablo126/PyScrabble) es una aplicación personal desarrollada como parte de un proyecto de una asignatura llamada Social Networks, impartida en University of Piraeus durante mi erasmus.

En ella se proponia realizar un juego en red multijugador.

Para ello realicé una aplicación monolítica en la que existia un gestor de modulos, en los que se encontraban el modúlo de jugadores, el módulo principal del juego en cuestión y un módulo de seguimiento de partida.

Si se desea evolucionar a un patrón tipo microservicios, lo más normal sería desarrollar un módulo para la gestión de usuarios, encargado de mantener estados y que se comunicara con la interfaz del juego por medio de API u otro tipo de medio.
Tambíen hubiese sido útil tener un módulo con la lógica del juego. Es decir, las reglas, restricciones y funciones necesarias durante el desarrollo de las partidas.

En cualquier caso, se podrian haber creado más microservicios, como el caso de un chat adjunto al juego o raking total de puntuaciones.

### Ejercicio 2

#### En la aplicacion que se ha usado como ejemplo en el ejercicio anterior, ¿podría usar diferentes lenguajes? ¿Qué almacenes de datos serían los más convenientes?

Perfectamente se podrían utilizar distintos lenguajes, por ejemplo si hubiesemos creado un módulo de estadísticas, este hubiera sido programado como hubiese querido y luego para notificar las estadísticas se hubiese realizado por medio de la API REST.
En cuanto a almacenes de datos, depende del tipo de servicio que queramos crear. Si hubiesemos creado un servicio de log, un almacen de datos orientado a fechas hubiese mejorado el rendimiento.
Si se hubiese querido desarrollar un sistema de logros flexible en el que puede haber muchos tipos, quizá lo mejor sería una base de datos No-SQL.

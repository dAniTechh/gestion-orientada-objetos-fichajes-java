# gestion-orientada-objetos-fichajes-java

Este proyecto implementa un motor de gestión deportiva desarrollado en Java, diseñado bajo un modelo de arquitectura modular que separa la gestión de entidades (Staff/Jugadores) de la lógica transaccional de mercado. El sistema no solo almacena datos, sino que simula el flujo de toma de decisiones de un club profesional mediante un núcleo de ejecución centralizado.

Arquitectura y Modelo de Objetos (POO)
El diseño se fundamenta en una jerarquía de clases que aprovecha al máximo la herencia y el encapsulamiento. La entidad base Trabajador (paquete Personas) centraliza la lógica común, de la cual derivan roles especializados con responsabilidades únicas:

Presidente: Encargado de la validación institucional de contratos y vinculación con el objeto Equipo.

Entrenador: Motor de la estrategia, vinculado a un enumerado Alineacion (4-3-3, 5-4-1, etc.) que define el esquema táctico y la compatibilidad con los jugadores.

Jugadores: Entidades técnicas con atributos específicos como Posiciones, dorsal y nacionalidad.

La consistencia de los datos se garantiza mediante bidireccionalidad en las relaciones: un equipo conoce a su presidente, y el presidente mantiene una referencia activa a su equipo, evitando objetos huérfanos en memoria.

Lógica de Ejecución y Mercado (Main & Managers)
La clase Main actúa como el orquestador del sistema. Su función principal es la instanciación masiva de objetos y la configuración de dependencias en tiempo de ejecución. Puntos clave de la implementación técnica:

Gestión de Colecciones: Uso de ArrayList<Jugadores> para el manejo dinámico de plantillas, permitiendo operaciones de inserción y filtrado por equipo.

Miembros Estáticos y Contadores: Implementación de métodos static en las clases Equipo y Jugadores para llevar un control de auditoría sobre el número total de instancias creadas, permitiendo monitorizar la carga del sistema desde el Main.

Motor de Traspasos (TraspasoManager): Se ha desacoplado la lógica de mercado de las clases de datos. El TraspasoManager utiliza métodos estáticos que reciben objetos por parámetro para validar operaciones mediante lógica booleana. Un fichaje solo se consolida si el Entrenador (criterio técnico) y el Presidente (criterio económico) devuelven un estado de aprobación positivo, simulando un entorno de negociación real.

Especificaciones de Desarrollo
El proyecto sigue una estructura de directorios profesional (src/ para fuentes y bin/ para el bytecode compilado). El flujo de datos se procesa de forma síncrona, gestionando excepciones y asegurando que cada operación de salida por consola refleje fielmente el estado actual de los objetos tras cada interacción en el mercado de fichajes.

# CoffeeHouse — La bitácora de la bitácora

*Crónica del primer proyecto del plan de práctica de vibecoding de Germán. Julio 2026.*

## Qué es

CoffeeHouse es una aplicación web de una sola pantalla (un archivo HTML autocontenido) que funciona como bitácora de calibración de café. Registra pruebas por variedad y por método de extracción (espresso y prensa francesa), guarda el calibre elegido de la rueda de molienda Oster (0–30) para cada combinación, calcula ratios automáticamente a partir de dosis y rendimiento, y ofrece dos secciones de referencia: los estándares técnicos de cada método con una guía de ajuste al paladar, y un recetario visual de doce preparaciones con tazas ilustradas que muestran las proporciones de cada capa. Su destino final es un Moto G100 restaurado de fábrica, montado en la pared de la barra de café como display dedicado.

## Cómo surgió

El proyecto no nació como una app: nació como un plan. El objetivo de fondo era establecer un ritmo de práctica de vibecoding — la habilidad de dirigir a una IA para construir soluciones sin escribir código a mano — con una cadencia sostenible de dos sesiones semanales de noventa minutos y proyectos quincenales terminables. La regla central del plan: cada proyecto debe resolver algo real y usable por quien lo construye, porque terminar genera confianza y usar genera motivación.

Como primer proyecto de nivel 1 se eligió el registro de extracciones de espresso, por tres razones deliberadas: dominio conocido a fondo (lo que convierte al autor en control de calidad del contenido), alcance terminable en pocas sesiones, y uso diario garantizado. La sesión arrancó con diez minutos de especificación escrita en lenguaje natural — el ejercicio que, según el plan, es el verdadero entrenamiento.

## Qué fue surgiendo en el camino

La especificación inicial pedía registro de molienda por variedad, gramos, tiempo, notas de cata, estándares y recetas. La primera revisión destapó dos huecos clásicos. El primero: la palabra "obviamente" aplicada a los gramos escondía una ambigüedad real — ¿gramos de café molido o de bebida extraída? La respuesta terminó siendo "ambos", porque la dosis y el rendimiento juntos habilitan el cálculo del ratio, un dato que no estaba pedido pero que la distinción hizo posible. El segundo: la molienda depende del método de extracción, así que "el calibre perfecto de esta variedad" no existe como dato único; existe por variedad y por método. La app terminó con dos diales de calibre por café.

Durante la construcción apareció una idea nueva que no estaba en ningún plan: un celular Android en desuso podía convertirse en display permanente de la barra. La idea se capturó con contexto en el banco de ideas de Notion — sin ejecutarla — y esa decisión de no expandir el alcance en caliente definió el resto del proyecto. Más tarde, esa misma idea reformuló requisitos de la app existente: la pantalla apaisada del G100 motivó tarjetas más anchas, carruseles horizontales deslizables y un modo compacto para pantallas bajas.

Hubo cuatro versiones. La v1 estableció la estructura de tres pestañas y la persistencia de datos. La v2 fue un rediseño integral: perfil de cata por variedad (acidez, amargor, cuerpo), la rueda de molienda como deslizador 0–30 que replica el dial físico de la Oster, tipografía robusta y paleta cálida en diálogo con la pared verde de la barra, y las preparaciones como carrusel deslizable. La v2.1 respondió al primer QA real: las pruebas pasaron a segundo plano detrás de un botón discreto (el kiosk muestra, no edita), todo se volvió carrusel, y se agregó arrastre con mouse para poder probar en PC lo que está diseñado para dedos. La v2.2 emparejó las alturas de todas las tarjetas, ensanchó las de café con una línea de última prueba, y sumó las tazas ilustradas de proporciones junto con tres preparaciones nuevas: irish coffee, affogato y un caramel macchiato genérico adaptable por syrup.

En el camino también se detectó y corrigió un error de contenido generado por la IA: la nota del americano describía en realidad un long black. Lo destapó un pedido del usuario (agregar el long black), y lo confirmó su conocimiento de dominio.

## Conceptos clave aprendidos

**Vibecodear es dirigir, no programar.** La habilidad que crece no es escribir código sino descomponer una idea, especificar con precisión, leer un error sin pánico y desarrollar criterio para evaluar lo construido. Es más cercano a ser product manager de un equipo (donde el equipo es la IA) que a ser programador.

**En una spec, lo obvio no existe.** Cada "obviamente" es una suposición sin verificar. Explicitar qué significa cada dato (dosis versus rendimiento, tiempo de extracción versus de infusión) no es burocracia: es lo que evita construir la cosa equivocada.

**Jerarquizar es oro.** Decir "esto es lo más importante" en una especificación le indica al constructor dónde no puede fallar y dónde hay margen para decidir. Fue la mejor característica de la spec inicial.

**Scope creep versus evolución por capas.** El proyecto terminó siendo mucho más que la spec original, pero creció por agregados validados en el uso — nunca por "ya que estamos". La disciplina complementaria es el banco de ideas: capturar cada ocurrencia con contexto y motivación, sin ejecutarla en el momento.

**El contexto de uso es parte de la spec.** "Se usa en un Moto G100 horizontal montado en la pared" no es una preferencia estética: convierte decisiones de estilo en decisiones funcionales. El carrusel deslizable no es un capricho visual; es la interacción correcta para dedos sobre pantalla apaisada.

**Pointer parity.** Lo que en el teléfono es gratis (deslizar con el dedo) en desktop hay que construirlo (arrastre con mouse y barra visible), y viceversa. Es un problema clásico con nombre propio y solución estándar.

**Dónde vive una app determina cómo guarda sus datos.** La versión actual usa el almacenamiento de artifacts de Claude, que solo persiste dentro de Claude. La versión kiosk necesitará una capa de persistencia propia del navegador. La lección general: la infraestructura de datos no es portable por defecto; migrar de entorno es un proyecto en sí mismo.

**El experto de dominio es el control de calidad.** La IA escribió mal la diferencia entre americano y long black; el usuario la conocía. Cuando la IA genera contenido especializado, la revisión experta no es opcional — y las revisiones de spec no solo agregan features: auditan lo ya construido.

**Las referencias visuales comunican, no se calcan.** Un print de "quiero algo de este tipo" ahorra mil palabras de especificación. Lo correcto es reinterpretar el concepto con identidad propia, nunca copiar el material ajeno.

## Estado y próximo paso

CoffeeHouse v1 está congelada y marcada como terminada en el banco de ideas, pendiente solo de su validación definitiva: la primera calibración real de un café con la app en la mano. El siguiente proyecto ya tiene nombre y espera su sesión de especificación propia: CoffeeHouse kiosk — la versión autónoma instalada en el G100 dedicado (cuenta de Gmail propia, sin datos personales), a pantalla completa y sin distracciones, con temporizador de preparación, funcionando a batería con el teléfono suspendido entre usos, y conviviendo con el asistente de voz y el control de luces de la casa.

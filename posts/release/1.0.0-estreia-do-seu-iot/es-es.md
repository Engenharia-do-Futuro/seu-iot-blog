![Portada](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# Seu IoT 1.0: el estreno de la plataforma como siempre fue pensada

**Seu IoT fue evolucionando paso a paso, según la necesidad de cada proyecto, pero la idea original siempre fue llegar hasta aquí. Rediseñamos todo el sistema operativo de la plataforma para sostener esa visión.**

**Versión:** 1.0.0 | **Fecha:** 2026-08-16

---

Llegamos a la versión **1.0.0**, y con ella el verdadero estreno de Seu IoT tal como fue pensado desde el inicio. A lo largo del camino, la plataforma fue evolucionando según la necesidad de cada cliente y de cada proyecto, una función aquí, una pantalla allá. Pero la idea original siempre fue otra: ponerte a **diseñar el funcionamiento de tu sistema**, no solo registrar dispositivos y completar formularios. Para llegar ahí, rediseñamos todo el **sistema operativo** de Seu IoT, y es ese trabajo el que presenta este texto.

El centro de todo es la nueva página de **Proyectos**, un tablero visual estilo "plano técnico" donde creas **procesos**, los conectas entre sí con **triggers** y ves la lectura de cada sensor en tiempo real, directo en la tarjeta. Es la parte de la que más nos enorgullecemos en esta versión: armar un proyecto se volvió mucho más dinámico, más libre para organizar a tu manera, sin perder la practicidad del día a día.

![Vista general del lienzo Blueprint de un proyecto, con procesos conectados por triggers](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_overview.gif)

---

## Proyectos: una nueva forma de organizar tus dispositivos

Los **Proyectos** llegan para reemplazar y complementar los antiguos Repositorios. Cada proyecto tiene **nombre**, **descripción**, **etiquetas libres** (con sugerencia automática de las etiquetas que ya usaste) y un **icono** elegido entre **78 opciones** organizadas por tema.

**Lo que ganas:**

- **Búsqueda y filtros:** encuentra proyectos por nombre, descripción o etiqueta, y filtra por la combinación de etiquetas que quieras.
- **Ordenamiento:** por nombre, fecha de creación/edición o número de dispositivos.
- **Dos vistas:** tarjetas o tabla en el computador; en el celular, siempre en tarjetas.
- **Ayuda contextual:** una explicación de "¿Qué es un proyecto?" disponible tanto en la pantalla vacía como mediante un botón de ayuda, para quien recién empieza.

![Página de Proyectos con búsqueda, filtro por etiquetas y alternancia entre tarjetas y tabla](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/projects_page_overview.gif)

**Por qué importa:** el menú lateral se reorganizó y "Repositorios" pasó a ser una sección heredada, mostrada solo a quien todavía tiene repositorios, que ahora también aparecen listados justo debajo de los proyectos. Nadie pierde nada, pero el camino recomendado de ahora en adelante es el Proyecto.

Vincular y desvincular dispositivos también quedó más claro: un modal separa **"En este proyecto"** de **"Otros dispositivos"** (con búsqueda), y el contador de dispositivos en la tarjeta o en la tabla ahora es **clicable**, y abre ese modal directamente.

![Modal de vínculo de dispositivos a un proyecto, separando "En este proyecto" de "Otros dispositivos"](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/project_device_link_modal.gif)

Otras novedades de la página de proyecto: la dirección ahora usa un **nombre amigable** basado en el título (en vez de un código largo), y hay una nueva **página de configuración** del proyecto, con microcontrolador, tipo de red, contadores de procesos por tipo, papelera y enlaces de aprovisionamiento/calibración. Todo traducido al **portugués, inglés y español**.

---

## El lienzo Blueprint: el corazón de este estreno

Aquí está la mayor novedad de la versión. La página del proyecto se convirtió en un **tablero visual estilo "plano técnico",** con efecto cianotipo, donde **arrastras**, haces **zoom** y organizas los elementos como más sentido le encuentres a tu proceso, sin cuadrícula fija, sin jerarquía forzada.

![Lienzo Blueprint con zoom y organización libre de los procesos](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_canvas_pan_zoom.gif)

**Por qué importa:** armar un proyecto dejó de ser completar formularios en secuencia y pasó a ser diseñar el funcionamiento de tu sistema, lo que hace que tanto crear como leer el proyecto sean mucho más intuitivos, sobre todo cuando hay varios procesos relacionados entre sí.

### Qué compone el tablero

- **Tarjeta fija de identificación:** una tarjeta en la esquina muestra icono, nombre, fechas de creación/edición, número de dispositivos y dueño del proyecto, siempre visible aunque navegues por el tablero.
- **Comentarios:** crea, edita con formato simple (**negrita**, *cursiva*, ~~tachado~~), mueve, redimensiona y elimina comentarios directo en el tablero. El texto se guarda solo al hacer clic fuera, con opción de deshacer.

![Creación y edición de un comentario en el Blueprint, con formato y guardado automático](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_comments.gif)

- **Gráficos como tarjetas:** los gráficos también se adaptaron a los proyectos, ahora son un tipo más de tarjeta, que colocas libremente en el Blueprint. Elige los procesos, el período de tiempo, la agrupación del eje y el tipo de gráfico (línea, barra, escalón, área, dispersión o pastel), con vista previa en vivo mientras lo configuras.
- **Minimapa coloreado por categoría:** ve el proyecto entero en miniatura, con cada proceso coloreado según su categoría y las líneas de conexión entre ellos también representadas.
- **Búsqueda en el tablero:** busca por nombre, filtra por tipo de elemento, y la vista se **centra automáticamente** en el resultado, útil en proyectos con muchos procesos.

![Minimapa coloreado por categoría y búsqueda dentro del lienzo centrando la vista](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_minimap_search.gif)

- **Carga con personalidad:** una pantalla de carga animada evita la pantalla en blanco al abrir un proyecto.
- **Vincular Dispositivo:** un botón en el encabezado del proyecto muestra los dispositivos vinculados, con búsqueda, estado en línea/desconectado y ubicación aproximada.

![Botón "Vincular Dispositivo" en el encabezado, mostrando dispositivos con estado y ubicación](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_link_device.gif)

### ¿Y en el celular?

El Blueprint ganó una versión adaptada para pantallas pequeñas: barra superior simplificada, alternancia entre información del proyecto y minimapa, y controles más grandes para facilitar el toque.

![Versión del lienzo Blueprint adaptada para celular](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/blueprint_mobile.gif)

---

## Tipos de Proceso: crear ya explica cómo funciona

Cada tipo de proceso ahora tiene una **pantalla propia de creación**, con **diagramas animados** que muestran cómo se comporta ese parámetro, ya no es un formulario genérico de campos sueltos. Esta es la otra parte que más nos gusta de esta versión: puedes entender lo que estás configurando mientras lo configuras.

![Pantalla de creación de un proceso con diagramas animados explicando el parámetro](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_creation_animated_diagram.gif)

Procesos disponibles en esta versión:

- **ADC (lectura analógica):** pin, resolución, atenuación y número de muestras, con diagramas que muestran la conversión de la señal y el efecto de cada parámetro en la lectura.
- **Lectura Digital / Escritura Digital:** encendido/apagado de pines, con diagramas que explican el ruido en la lectura y la necesidad de amplificar la señal (transistor/relé) al escribir.
- **Conteo de Pulsos:** cuenta pulsos eléctricos, con opción de contar por flanco de subida/bajada y filtro de ruido.
- **PWM:** controla la intensidad (ciclo de trabajo) y la frecuencia, con desvanecimiento suave configurable.
- **Bit Banging Serial:** lectura de sensores con protocolo serial simple (dato + reloj).
- **PID:** control Proporcional-Integral-Derivativo, con un **gráfico en vivo** que muestra cómo cada ganancia afecta la respuesta del sistema controlado.

![Pantalla de configuración de PID con gráfico en vivo mostrando el efecto de las ganancias](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_pid_live_chart.gif)

- **Linealización:** convierte la lectura bruta de otro proceso en una unidad real (ej.: voltaje → temperatura), calculando automáticamente la recta y la ecuación a partir de puntos de calibración que tú indicas.
- **Cualificación:** clasifica la lectura de otro proceso en rangos que tú nombras (ej.: "bajo/medio/alto").

Tres procesos de esta versión son novedad al punto de merecer una sección propia, justo a continuación: **I2C**, **Máscara de Bits** y **Timer / Timeout**.

### Catálogo, ejecución y lectura en tiempo real

Todos los tipos están organizados en un **catálogo por categoría** (Periféricos, Eventos, Procesamiento de Datos), con búsqueda y filtro. Los tipos aún no implementados aparecen con el sello **"próximamente"**.

![Catálogo de tipos de proceso organizado por categoría, con búsqueda, filtro y sello "próximamente"](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_catalog.png)

- Cada proceso tiene un **nombre personalizable** (con sugerencia automática "Proceso N").
- Un botón **"Ejecutar"** en la tarjeta fuerza una nueva ejecución sin necesidad de reconfigurar nada.
- La tarjeta del proceso en el lienzo muestra la **lectura más reciente en tiempo real**, y puede alternar a un **minigráfico de historial**, con color e icono según la categoría.

![Tarjeta de proceso en el lienzo alternando entre lectura en tiempo real y minigráfico de historial](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_realtime_card.gif)

- **Detección automática de conflictos:** la plataforma identifica pines/canales ya ocupados por otros procesos, evitando errores de configuración.
- **Confirmación visual:** el sistema ahora muestra cuando el dispositivo realmente aplicó el proceso creado o editado, en vez de dejarte sin respuesta.

En el celular, la pantalla de creación de proceso queda **simplificada**, solo la tabla de parámetros, sin los diagramas animados.

---

## I2C: un protocolo de comunicación totalmente nuevo

**I2C** es el proceso más original de esta versión: un protocolo de comunicación nuevo en Seu IoT, creado desde cero para conversar con sensores y periféricos que usan este bus, muy común en sensores de temperatura, humedad y presión, acelerómetros, pantallas y una infinidad de otros módulos.

La implementación llega en cuatro procesos: **Canal** (define el bus y los pines de datos/reloj), **Lectura**, **Escritura** y **Barrido**. Como los demás procesos de esta versión, la pantalla de configuración viene con diagramas que explican cómo funciona el bus.

![Configuración del canal I2C con diagrama del bus](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_i2c_channel.gif)

El **Barrido** funciona como un "scanner": recorre el bus y muestra, en una cuadrícula de direcciones, qué dispositivos I2C están respondiendo, útil tanto para verificar el cableado como para descubrir la dirección de un sensor nuevo antes de configurar la Lectura.

![Barrido I2C mostrando la cuadrícula de direcciones de los dispositivos conectados al bus](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_i2c_scan.gif)

**Por qué importa:** el I2C abre la puerta a una familia mucho más amplia de sensores compatibles con Seu IoT, incluidos los que combinan varios datos en un solo chip, lo que cobra sentido junto con la próxima novedad.

### Máscara de Bits: separando lo que viene junto en el mismo dato

Muchos sensores I2C devuelven, en un único valor leído, **más de una información junta**, por ejemplo, algunos bits del dato representan la lectura en sí, y otros bits representan una bandera de estado o una segunda magnitud. La **Máscara de Bits** se creó especialmente para tratar este escenario: un proceso que **extrae una parte específica** de un valor leído por otro proceso, aislando solo los bits que interesan.

![Configuración de una Máscara de Bits extrayendo parte de un valor leído vía I2C](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_bitmask.gif)

**Por qué importa:** sin este proceso, necesitarías tratar el dato bruto fuera de la plataforma para separar lo que viene mezclado en un único valor. Con la Máscara de Bits, esa separación ocurre dentro del propio Blueprint.

> **Ejemplo:** un sensor I2C devuelve un valor de 16 bits en el que los 12 bits más bajos son la lectura de temperatura y los 4 bits más altos son un código de estado. Configura dos Máscaras de Bits sobre la misma Lectura I2C, una aislando los 12 bits de la temperatura, otra aislando los 4 bits del estado, y trata cada una como un proceso independiente en tu proyecto.

---

## Timer / Timeout: el muestreo se convirtió en un proceso

En Repositorios, la tasa de muestreo, cada cuánto tiempo se lee un sensor, se configuraba **dentro de cada proceso**: ADC, Conteo de Pulsos, Lectura Digital y Bit Banging Serial, cada uno con su propio campo de intervalo, aislado de los demás.

Ahora existe un proceso dedicado para esto: el **Timer / Timeout**. Configuras el intervalo una sola vez (días, horas, minutos o segundos) y **conectas ese Timer, vía trigger, a uno o más procesos** que deben activarse por él. La tarjeta del Timer muestra una **cuenta regresiva visual** hasta el próximo disparo.

![Proceso Timer configurado con cuenta regresiva y conectado a otros procesos por triggers](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/process_timer_triggers.gif)

**Por qué importa:** el mismo ritmo de muestreo se vuelve **reutilizable** entre varios procesos, en vez de repetirse en cada uno, y queda visible en el Blueprint quién se activa por cuál Timer.

> **Ejemplo:** un Timer de 30 segundos conectado a tres procesos distintos, un ADC de temperatura, una Lectura Digital de un sensor de puerta y un Barrido I2C. Los tres se ejecutan juntos, al mismo ritmo, sin repetir la configuración de tiempo en cada uno.

---

## ESP32-S3: la primera variante de dispositivo soportada

Hasta ahora, todo proyecto en Seu IoT partía de un único hardware de referencia: el ESP32 original. Esta versión trae la **primera variante de dispositivo soportada** por la plataforma: el **ESP32-S3**.

En la página de configuración del proyecto, defines **para qué modelo de dispositivo** es ese proyecto, ESP32 o ESP32-S3. A partir de esa elección, las pantallas de configuración de proceso pasan a respetar los **límites de pines correctos de ese modelo**, evitando que configures un pin que no existe o que ya tiene una función reservada en la placa.

![Configuración del proyecto definiendo el modelo de dispositivo, ESP32 o ESP32-S3](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/esp32_s3_project_config.png)

Y no es solo configuración: también ya es posible **grabar el firmware en dispositivos ESP32-S3** mediante el flujo de instalación de la plataforma, de la misma forma en que ya se hacía con el ESP32.

![Grabación de firmware en un dispositivo ESP32-S3 mediante el flujo de instalación](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/esp32_s3_flashing.gif)

**Por qué importa:** es el primer paso de un camino más grande, ofrecer soporte a distintas variantes de hardware dentro del mismo proyecto y del mismo flujo, sin que tengas que aprender una plataforma diferente para cada placa.

---

## Triggers: conecta procesos con un trazo

Es posible **conectar procesos entre sí** dibujando una línea desde la salida de una tarjeta hasta la entrada de otra, por ejemplo, un **conteo de pulsos** activa un **PWM**.

![Conexión siendo dibujada entre dos procesos en el lienzo, creando un trigger](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.0.0-estreia-do-seu-iot/images/triggers_connecting.gif)

- Una **flecha** indica el sentido del flujo; la línea usa un **degradado de color** entre las categorías de origen y destino.
- El sistema avisa cuando intentas **hacer clic** en vez de **arrastrar** para crear la conexión.
- Al eliminar un proceso, las conexiones asociadas a él **desaparecen automáticamente**.

**Por qué importa:** es la pieza que convierte un conjunto de procesos aislados en una automatización de verdad, todo dibujado, todo visible, sin necesidad de abrir un formulario aparte para configurar "si esto, entonces aquello".

> **Ejemplo:** conecta un **Conteo de Pulsos** de un sensor de flujo a un **PWM** que controla una bomba, para que la intensidad de la bomba responda automáticamente al flujo medido, todo visible como una línea entre las dos tarjetas en el Blueprint.

---

## Navegación y usabilidad general

Una serie de ajustes hacen la plataforma más fluida en el día a día:

- Varios botones y tarjetas que antes solo navegaban al hacer clic se convirtieron en **enlaces de verdad**, que puedes abrir en una pestaña nueva con clic derecho o Ctrl/Cmd+clic.
- **Menú lateral reorganizado** en grupos (Vista general, Organización, Monitoreo, Dispositivos, Sistema), con iconos actualizados.

- Nueva pantalla **"hub" de vínculo de dispositivo**, que reúne Instalar / Conectar / Enlaces de Aprovisionamiento en un único lugar, con vista previa animada de cada etapa.
- **Página de inicio (Welcome) rediseñada:** tarjetas de proyectos y dashboards recientes, guía rápida paso a paso numerada, mini blog con las últimas publicaciones y tarjeta de almacenamiento clicable.

- Nuevo **favicon** (icono de la pestaña del navegador).
- Botón **"Volver al sitio"** en el encabezado de la plataforma.
- Opción de vincular un dispositivo **"sin proyecto ni repositorio"** al instalarlo o editarlo.

---

## Otras novedades de esta versión

Algunas mejoras que llegaron junto, en áreas separadas de lo que presentamos hasta aquí:

- **Aislamiento de credenciales en MQTT:** cada dispositivo ahora tiene su propio inicio de sesión en el broker MQTT, el canal por donde intercambia datos con la plataforma, restringido por una **ACL** (lista de control de acceso) solo a los tópicos de ese dispositivo específico. Esa credencial sigue renovándose automáticamente todos los días, como ya ocurría antes, pero ahora es única por dispositivo. En la práctica, esto aísla el riesgo de una violación física: si alguien extrae las credenciales de un dispositivo, solo obtiene acceso a los datos de ese dispositivo, y los canales de comunicación de todos los demás permanecen protegidos.
- **SSL en HTTP y MQTT WebSocket:** la comunicación pasa a estar cifrada en esos canales, sin cambio visible en pantalla, pero con más seguridad.
- **Canal de feedback:** nuevo formulario para que envíes comentarios directamente desde la plataforma.

- **Blog con portada:** las tarjetas del listado del blog ahora muestran la imagen de portada del artículo, con una imagen predeterminada cuando no hay portada definida.

---

## Resumen de las novedades

| Área | Qué cambia para ti |
|---|---|
| Proyectos | Nuevo concepto con nombre, descripción, etiquetas, icono, búsqueda, filtros y ordenamiento |
| Lienzo Blueprint | El proyecto se vuelve un tablero visual: arrastra, haz zoom, comenta, usa el minimapa, busca y agrega gráficos como tarjetas |
| Tipos de Proceso | Pantallas propias con diagramas animados y catálogo por categoría |
| I2C y Máscara de Bits | Nuevo protocolo de comunicación, con Canal, Lectura, Escritura y Barrido; extrae partes de un valor leído |
| Timer / Timeout | El muestreo se volvió un proceso dedicado, que activa otros procesos por trigger |
| ESP32-S3 | Primera variante de dispositivo soportada, con límites de pines y grabación propios |
| Triggers | Conecta procesos dibujando una línea, con flecha y degradado de color |
| Seguridad | Credenciales MQTT exclusivas por dispositivo (ACL) y SSL en HTTP y MQTT WebSocket |
| Feedback | Formulario de feedback directo en la plataforma |

---

**Ya está todo en línea.** Abre un proyecto y mira el Blueprint por primera vez, crea un proceso, observa las animaciones que explican cada parámetro y conecta dos procesos con un trigger. Es la versión que siempre quisimos entregar, y ahora por fin existe. Cuéntanos qué te pareció: **tu feedback guía las próximas versiones.**

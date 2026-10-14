![Portada](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# Seu IoT 1.1: tus datos en cualquier pantalla, y conectados con el resto del mundo

**Un nuevo centro de visualización de datos, tablas y mapas que cruzan proyectos, estado en línea/fuera de línea de cada dispositivo, una API abierta con widgets para pegar en tu sitio y conexión con asistentes de IA. Todo bajo tu control.**

**Versión:** Plataforma 1.1.0 | Firmware 2.0.1 | **Fecha:** 2026-10-13

---

La versión 1.0 anterior trajo Blueprint y la forma de **armar** el funcionamiento de tu sistema. La **1.1** trata de lo que viene después: **ver lo que tu sistema está produciendo** y **llevar esos datos adonde los necesites**.

Fueron tres frentes de trabajo:

1. **Visualización de datos:** nuevos tipos de gráfico, indicadores (KPIs), medidores, tablas y mapas, y una pantalla de creación de gráficos completamente rediseñada.
2. **Estado de conexión de los dispositivos:** ahora la plataforma registra cuándo cada dispositivo se conectó y se desconectó, y eso se convierte en dato para gráficos.
3. **Integraciones:** una API abierta para sistemas de terceros, widgets que pegas en cualquier página y el acceso de asistentes de IA (Claude, Cursor, Gemini CLI y otros) mediante MCP.

Junto con la plataforma, el **firmware 2.0.1** corrige la edición de procesos directamente en el dispositivo y permite encadenar una lectura I2C con una escritura I2C.

![Vista general de un panel con los nuevos tipos de gráfico lado a lado](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/dashboard_overview.gif)

---

## Una nueva pantalla para crear gráficos

Antes de hablar de los gráficos en sí, el cambio que los sostiene: la creación de gráficos ganó una **pantalla propia**, con la elección del tipo (**Gráfico lineal, Composición, Indicador, Medidor, Recipiente, Mapa de calor, Tabla y Mapa**) y una **vista previa en vivo** durante la configuración. Es la misma pantalla, con las mismas opciones, tanto dentro de un **proyecto (Blueprint)** como en el **panel**.

![Elección del tipo de gráfico con la vista previa en vivo](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/chart_creator_catalog.gif)

**Por qué importa:** en el panel, un gráfico ahora puede reunir **señales de varios proyectos y dispositivos** en el mismo lugar. Antes, cada gráfico del panel quedaba atado a un único origen. Un panel de operación ya no necesita un gráfico por proyecto: puede comparar lo que está pasando en todos.

El panel también ganó el modo **Pantalla completa**, pensado para quedar abierto en un televisor o en un monitor de sala de control.

![Panel en pantalla completa](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/dashboard_fullscreen.png)

---

## Nuevos tipos de gráfico

### Indicadores (KPIs): del último valor a estadísticas de verdad

El **Indicador** de **Último valor** ahora muestra la **unidad de medida** (ej.: "23,5 °C"), y ganó compañía: son **14 tipos de indicador (KPI)**, organizados en grupos (Lectura, Tendencia y comparación, Estadística de período, Rango normal, Flota y acumulados), cada uno con una explicación y un ejemplo en el catálogo de tipos.

![Catálogo de tipos de indicador, con un ejemplo de cada uno](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/kpi_type_catalog.gif)

| Tipo de indicador | Qué muestra |
|---|---|
| Último valor | La última lectura recibida |
| Estadística de período | Media, mínimo, máximo o conteo de lecturas en el período de la tarjeta |
| Comparación con meta/objetivo | La última lectura frente a un valor objetivo que tú defines |
| Flecha de tendencia simple | Si el valor está subiendo o bajando |
| Con tiempo de la última lectura | La lectura con "hace 3 min" al lado |
| % de muestras dentro del rango normal | Cuánto del período estuvo dentro de lo esperado |
| Comparación con período anterior | El período actual frente al anterior (hora, día, semana, mes o año) |
| Percentil (p90/p95) | El valor que ignora picos raros |
| Desviación estándar/variabilidad | Cuánto oscila la lectura |
| Conteo de valores fuera de rango | Cuántas veces el valor salió del rango normal |
| Conteo de ciclos/ejecuciones | Cuántas veces el proceso publicó una lectura |
| Proyección simple (extrapolación lineal) | Extrapola la tendencia y estima cuándo se alcanzará el límite |
| Ranking dentro de la flota | La posición del dispositivo frente a los demás del proyecto |
| Consumo acumulado calculado | Suma acumulada a lo largo del tiempo (ej.: kWh) |

Tú eliges qué mostrar junto con el valor: hora, dispositivo, ubicación, proceso, operador y cliente.

> **Ejemplo:** el indicador "% de muestras dentro del rango normal" de un congelador de laboratorio muestra "92% dentro del rango (7 días)". De un vistazo sabes si el equipo se está comportando, sin abrir ningún gráfico.

### Medidor y recipiente: ver el nivel, no solo el número

Dos nuevas formas de mostrar **un valor dentro de una escala** (mínimo y máximo), con **franjas de color** que cambian a medida que el valor cruza cada límite:

- **Medidor:** en los estilos **Velocímetro, Anillo completo, Medio anillo y Cuarto de anillo**.
- **Recipiente:** el nivel se llena de verdad, en nueve formas: **Tanque, Silo, Tanque horizontal, Caja abierta, Tolva, Cilindro de gas, Barril, Barra de carga y Batería**.

El color puede ser en **bloques** (cambia al cruzar cada límite) o en **degradé continuo** entre las franjas.

![Medidor y recipiente con franjas de color, cambiando de color al cruzar los límites](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/gauge_and_container.gif)

![Galería de las formas de recipiente](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/container_shapes.gif)

> **Ejemplo:** el nivel de un depósito como Tanque, verde por encima del 40%, amarillo entre el 20% y el 40%, rojo por debajo del 20%. Quien pasa frente a la pantalla entiende el estado sin leer ningún número.

### Mapa de calor (calendario)

Un **valor por día** pintado en un calendario, al estilo de las contribuciones de GitHub. Elige la **agregación** (**Promedio, Suma, Conteo, Máximo o Mínimo**) y el **período del calendario** (**Mes o Año**). Los días más intensos se ven más oscuros, y el globo muestra la fecha, el valor y cuántas muestras entraron en el día. Hay botones para ir al período anterior, al siguiente y volver a hoy.

![Mapa de calor alternando entre Promedio y Conteo](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/calendar_heatmap.gif)

**Por qué importa:** patrones que pasan desapercibidos en un gráfico de línea de meses (como "todos los lunes el consumo se dispara") quedan a la vista en un calendario.

### Histograma

Entre los estilos del tipo **Composición** (Pastel, Mapa de árbol, Barra horizontal e Histograma), el **Histograma** muestra la **distribución** de los valores de un proceso en un período: cuántas lecturas cayeron en cada rango. El **Número de baldes** puede ser **Automático (regla de Sturges)** o fijo, y hay degradé del primer al último balde. Cambiar el período recalcula todo.

![Estilos del tipo Composición](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/composition_types.gif)

![Histograma cambiando el número de baldes y el período](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/histogram.gif)

### Línea y área coloreadas por franja de valor

El trazo del gráfico de línea o de área **cambia de color** a medida que el valor cruza las franjas que definiste (verde, amarillo, rojo), en bloques o en degradé. Basta mirar la línea para saber cuándo y por cuánto el valor salió de lo esperado.

![Gráfico de línea cambiando de color al cruzar las franjas configuradas](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/colored_line_by_band.gif)

### Líneas de referencia

Anotaciones fijas sobre el gráfico, independientes de los datos: una línea **horizontal** (un límite de operación), **vertical** (una hora de corte) o **inclinada**, entre dos puntos. Cada una tiene **etiqueta, color y estilo** (continua, discontinua, punteada o raya-punto).

![Líneas de referencia horizontales en un gráfico](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/reference_lines.gif)

### Ajustes en los gráficos existentes

- **Gráfico de barras:** el ancho de la barra ahora se adapta a tarjetas angostas y a muchos puntos, sin desbordar fuera del gráfico, y la primera y la última barra ya no quedan cortadas en los bordes.
- **Gráficos de calibración:** ahora muestran los últimos **15 puntos** en lugar de 80, lo que acabó con el "mar de puntos" ilegible. Arrastrar para seleccionar y calcular el promedio sigue funcionando incluso si el mouse sale del área del gráfico. La lectura en foco en la lista se resalta en el gráfico de regresión, y los valores nunca aparecen en notación científica.
- **Globos de información y ejes** con colores más legibles en los temas claro y oscuro, y el eje Y se ajusta al ancho real de los números.

---

## Tablas y mapas que cruzan proyectos

Este es el cambio que más amplía lo que el panel puede hacer. Hasta ahora, un gráfico o widget de datos apuntaba a **un** proyecto. Ahora defines una **regla de dispositivos** (con el botón **Agregar regla**) y la plataforma resuelve, en cada carga, qué dispositivos entran, sean del proyecto que sean.

La regla puede filtrar por:

- **Proyecto** y **repositorio**
- **Persona** (operador y cliente)
- **Modelos** (ej.: solo ESP32-S3)
- **Solo en línea:** dispositivos con lectura en las últimas 24 horas
- **Área geográfica:** un círculo en el mapa, con centro y **Radio (km)** que arrastras

### Tabla configurable

Una fila por dispositivo, y **tú eliges las columnas** (**Agregar columna**). La primera es siempre el dispositivo; las otras pueden ser de cinco tipos:

- **Identidad:** IP local, IP pública, Proyecto, Estado, Modelo, Operador, Cliente y Ubicación.
- **KPI:** cualquiera de los 14 tipos de indicador, calculado para cada dispositivo.
- **Medidor:** el medidor dentro de la celda.
- **Gráfico:** la tendencia reciente en un minigráfico sin ejes.
- **Acción:** un botón, interruptor, control deslizante o campo de texto que **ejecuta el proceso en ese dispositivo**, directamente desde la fila de la tabla. El botón de una lectura es **Leer ahora**.

![Tabla de dispositivos con columnas de identidad, KPI, medidor, gráfico y acción](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/table_widget.gif)

Al hacer clic en el operador, el cliente o la ubicación de una fila, un globo muestra los **datos de contacto**, con atajos para copiar, enviar un correo, abrir WhatsApp o abrir en Google Maps.

> **Ejemplo:** una tabla "Cámaras frías" que reúne todos los dispositivos del cliente X en 5 proyectos diferentes: estado en línea, temperatura actual con medidor, tendencia de las últimas horas y un botón para forzar una nueva lectura. Todo en una pantalla, sin entrar en ningún proyecto.

### Mapa con valores en los marcadores

El **Mapa** usa la misma regla de dispositivos. Cada pin muestra **datos informativos** que tú configuras (indicadores, medidores y gráficos). **El color del pin viene del dato informativo principal**, que debe ser un medidor y se marca con la estrella (por ejemplo, rojo en los dispositivos por encima del límite de temperatura), y el globo muestra los demás datos al hacer clic en el dispositivo. Encima de cada pin también puedes alternar el nombre del dispositivo, el operador, el cliente y la hora.

![Mapa de dispositivos con pines coloreados por el dato principal y globo con los datos informativos](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/geo_map_values.gif)

Tabla y mapa también funcionan **dentro del Blueprint** de un proyecto, ahora como un tipo más de tarjeta. El mapa pasó a usar **OpenStreetMap**, sin depender de un proveedor de tiles que pasó a exigir clave de API.

---

## En línea y fuera de línea: el historial de conexión de cada dispositivo

Hasta ahora la plataforma sabía **si** un dispositivo estaba en línea. Ahora también sabe **cuándo** se conectó y se desconectó. El broker MQTT pasó a avisar cada evento, y Seu IoT guarda el historial.

El estado se actualiza **en tiempo real** en las listas de dispositivos y en los modales, sin necesidad de recargar la página.

![Lista de dispositivos con el estado en línea/fuera de línea cambiando en tiempo real](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/device_live_status.gif)

Y lo más importante: la conectividad se vuelve una **señal como cualquier otra** en tus gráficos, tablas y mapas, en el grupo **Conectividad** al elegir la señal. Existen cuatro variaciones:

| Señal | Qué muestra |
|---|---|
| Estado de la conexión | 1 cuando está conectado, 0 cuando está desconectado, un punto por evento |
| Nº de desconexiones | Cuántas veces el dispositivo se cayó |
| Tiempo conectado | Segundos acumulados en línea |
| Tiempo desconectado | Segundos acumulados fuera de línea |

![Gráfico del estado de conexión de un dispositivo a lo largo del día](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/connection_state_chart.gif)

**Por qué importa:** responder "¿este sensor se está cayendo mucho?" pasa a ser cuestión de leer un gráfico o una columna de tabla (el conteo de desconexiones de la semana, o el porcentaje de tiempo en línea), y no de investigar logs.

---

## Almacenamiento: papelera por proyecto

La **papelera** ahora vale también para los datos de los **proyectos**. Puedes mover los datos de un dispositivo de un proyecto a la papelera, restaurarlos o eliminarlos de forma definitiva, y la regla de limpieza automática de tu plan pasa a ocuparse tanto de los datos de los repositorios como de los de los proyectos. Los eventos de conexión también entran en esa limpieza.

La tarjeta de uso de almacenamiento muestra el consumo **sumando repositorios y proyectos**, y lo que está en la papelera deja de aparecer en los gráficos, en las lecturas en vivo y en el "último mensaje" del dispositivo.


---

## Publicación automática de los procesos

Para que un proceso aparezca en gráficos, necesita **publicar** el resultado en cada ejecución. Ahora eso está a un clic de distancia:

- Un **ícono de sobre** en la tarjeta del proceso activa y desactiva la **Publicación automática** (el ícono avisa "clic para desactivar" o "clic para activar").
- En la **configuración del proyecto**, la opción **Publicación automática por defecto** define si los **procesos nuevos nacen publicando** (por defecto, sí). Los procesos creados realmente pasan a heredar ese valor por defecto.
- El botón que alterna entre el valor y el minigráfico queda **deshabilitado, con una explicación**, cuando el proceso todavía no tiene ningún dato para graficar.

![Ícono de sobre en la tarjeta del proceso y la opción Publicación automática por defecto en la configuración del proyecto](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/publish_on_execute.gif)

---

## API abierta: tus datos en sistemas de terceros

Tus datos ahora pueden ser leídos por **sistemas que no tienen cuenta en Seu IoT**, sin exponer tu inicio de sesión y sin abrir el proyecto entero.

Eso se hace mediante **Contratos de API**, creados en la configuración del proyecto. Un contrato es una **vista limitada** del proyecto: eliges **qué procesos** (y, si quieres, qué dispositivos) puede ver. Cada contrato entrega:

- **Clave HTTPS:** para consultar el historial y el valor actual.
- **Credencial MQTT/WS (tiempo real):** para recibir los valores **en tiempo real**, apenas el dispositivo publica, sin necesidad de estar preguntando.
- **Widgets incorporables** (ver a continuación).

![Creación de un contrato de API eligiendo procesos y dispositivos del alcance](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/api_contract_creation.gif)

**Seguridad y control:**

- Puedes **revocar, reactivar, regenerar las credenciales, definir cuándo expira el contrato y editar el alcance** en cualquier momento.
- La clave y la contraseña se muestran **una sola vez**, en el momento en que se generan.

**Seguimiento de uso:** la lista de contratos muestra las columnas **API (30 días)** y **Widgets (30 días)**, y el botón **Ver uso** abre el detalle **por día** (días en UTC-0) de las solicitudes de la API y de las lecturas de widgets. El límite es de 60 solicitudes por minuto por contrato. Los datos en tiempo real (MQTT) no cuentan para el límite, y por eso son el camino recomendado para quien quiere datos "en vivo".

![Uso diario de un contrato de API](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/api_contract_usage.png)

El **Centro de ayuda** ganó una página de **documentación de la API**, con la descripción de las rutas, el formato de los datos, ejemplos de código y orientaciones de buenas prácticas, y los ejemplos y las imágenes están en un repositorio público de ejemplos.

![Página de documentación de la API en el Centro de ayuda](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/api_docs_page.png)

### Widgets para pegar en tu sitio

¿Quieres mostrar la temperatura de tu invernadero en la página de tu empresa, sin escribir una línea de integración? A partir de un contrato, creas un **widget**: eliges la señal (dentro de lo que el contrato permite), el tipo de gráfico y el aspecto, ves el resultado en una **vista previa** y copias el **Código de incorporación**, un `<script>` listo para pegar en el sitio.

El widget **se actualiza solo** en tiempo real y acepta los tipos de gráfico más usados: gráficos lineales, medidores, recipientes, indicadores, mapa de calor, histograma y otros.

![Widget de Seu IoT funcionando en una página HTML externa](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/widget_embedded_external_page.gif)

**Por qué es seguro pegarlo:** la página pública **nunca recibe la clave del contrato**. Cada widget tiene una credencial **propia**, limitada exactamente a las señales que muestra, y que puedes **revocar individualmente** sin afectar al resto. ¿Lo revocaste? La página que ya tenía el código pasa a mostrar "widget desactivado por su dueño", sin que tengas que tocar el sitio. También se puede regenerar el código de incorporación, lo que hace que el `<script>` antiguo deje de funcionar.

---

## Conecta una IA a Seu IoT (MCP)

Seu IoT ahora puede ser operado por **asistentes de IA** (Claude, Cursor, Gemini CLI y cualquier cliente compatible con el protocolo **MCP**). La IA se vuelve una interfaz más sobre tu cuenta: **ve solo los proyectos que liberes** y **hace solo lo que permitas**.

Pides, en lenguaje natural, cosas como "lista los dispositivos fuera de línea del proyecto Invernadero", "crea un gráfico de calendario de la temperatura del último mes" o "arma la lectura I2C de este sensor", y la IA hace el trabajo.

### Tú decides qué puede hacer la IA

Al conectar, Seu IoT abre la pantalla **Autorizar acceso a tu cuenta**: eliges los **proyectos** y, en una tabla de permisos, qué puede hacer la app. Cada permiso tiene dos opciones: **Permitir** y **Pedir mi confirmación**. Al final, **Autorizar** o **Denegar**.

| Permiso | La IA puede |
|---|---|
| Ver proyectos | Listar proyectos, dispositivos (en línea/fuera de línea), procesos, triggers y gráficos |
| Leer datos | Consultar muestras y resúmenes (mínimo, máximo, promedio, p95, por hora/día/semana/mes) |
| Editar proyectos permitidos | Crear y editar procesos, triggers, gráficos y la posición de las tarjetas |
| Crear proyectos nuevos | Crear proyectos nuevos |
| Eliminar procesos y vínculos | **Pedir** eliminar procesos, triggers y gráficos |
| Crear códigos de acceso | **Pedir** contratos de API, widgets incorporables y la primera clave de acceso |
| Ejecutar procesos (play) | Ejecutar un proceso ahora, como el botón de play |

![Pantalla Autorizar acceso a tu cuenta, con la tabla de permisos y la elección de los proyectos](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/ai_consent_screen.gif)

**Lo que la IA nunca hace:** eliminar proyectos o dispositivos, eliminar datos recolectados, rotar claves ni tocar la facturación y la administración. Eso queda siempre contigo, en la plataforma.

### Aprobaciones y transparencia

- Cuando una acción exige confirmación, **no se cambia nada** hasta que apruebes. La pendiente aparece en la campana de **Notificaciones**, con el **antes y después** de lo que se haría.
- **Las claves y los tokens siempre exigen tu aprobación.** Y tú eliges si la credencial va **directo a la IA** (que la retira una única vez, en hasta 15 minutos) o si **solo tú la ves**.
- En **Configuración > Apps conectadas** haces el seguimiento de cada app, **amplías o reduces** los permisos al instante y **revocas** con un clic.
- El botón **"Qué hizo esta app"** muestra el historial de todo lo que la app leyó y escribió (incluso lo que fue rechazado), sin mostrar nunca credenciales.

![Cola de aprobaciones en Notificaciones, con el antes y después de un cambio propuesto por la IA](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/ai_proposal_review.gif)

![Pantalla de Apps conectadas con el historial "Qué hizo esta app"](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/1.1.0-visualizacao-de-dados-e-integracoes/images/ai_connected_apps.gif)

### Una IA que no necesita adivinar

La IA recibe **documentación dentro del propio protocolo**: para cada tipo de proceso (ADC, PWM, I2C, PID y los demás) y cada tipo de gráfico, consulta los **parámetros válidos, el formato de los datos y ejemplos listos**, incluso los pines y canales correctos para la placa del proyecto (ESP32 o ESP32-S3). También puede hacer un **ensayo** (validación sin crear nada) antes de proponer un cambio, y consultar **qué pines están libres**.

**Por qué importa:** menos prueba y error, menos aprobaciones inútiles en tu cola, y resultados correctos desde la primera propuesta.

> **Ejemplo:** pides "crea un proceso que escriba en el display I2C el valor leído por el sensor". La IA consulta las fichas de las operaciones, verifica los pines libres, valida el ensayo y solo entonces envía **una** propuesta para que la apruebes, con todos los parámetros correctos.

---

## Firmware 2.0.1

Dos cambios en el dispositivo (los procesos y la plataforma funcionan con el firmware anterior, pero estas funciones dependen de la actualización):

- **Editar un proceso ahora sí actualiza el dispositivo.** Antes, al modificar los parámetros de un proceso ya creado, el dispositivo reejecutaba el proceso pero seguía usando la configuración antigua. Ahora pasa a usar los nuevos parámetros de inmediato.
- **Escritura I2C accionada por trigger.** Cuando una **Escritura I2C** es accionada por otro proceso (por ejemplo, una Lectura I2C o un valor calculado), el dato recibido **se convierte en el contenido enviado al chip**. Los números se convierten en bytes con el ancho que configuraste (ej.: 65281 → `FF01`), y los textos en hexadecimal se envían tal cual. El valor del trigger vale **solo para esa ejecución** y nunca sobrescribe lo que está guardado en el proceso.

> **Ejemplo:** un proceso de PID calcula la potencia y, mediante un trigger, alimenta una Escritura I2C que ajusta un convertidor digital-analógico, todo diseñado en Blueprint.

---

## Otras mejoras

- **Bit Banging Serial:** el pin de datos (DT) no se enviaba correctamente al dispositivo, que terminaba leyendo siempre en el pin 0. Corregido, y la tarjeta ahora muestra los pines **DT/SCK** en el mismo estilo que los pines SDA/SCL del I2C.
- **Más estabilidad en Blueprint:** al volver a la pestaña del navegador, la pantalla ya no sobrescribe un cambio que acabas de hacer en comentarios, gráficos, procesos y triggers.
- **Diseño de calibración en el celular:** las áreas de Linealización y Calificación dejaron de "colapsar" en pantallas pequeñas.
- **Notificaciones:** ahora es posible abrir el **detalle** de cada notificación en una ventana.
- **Soporte:** nuevo flujo para **abrir un ticket de soporte** directamente desde la plataforma.
- **Inicio de sesión:** después de entrar, vuelves a la página a la que intentabas acceder.
- **Blog:** cada publicación ahora muestra el **autor**, y el índice de temas aparece también en las versiones para buscadores y redes sociales.

---

## Resumen de las novedades

| Área | Qué cambia para ti |
|---|---|
| Creación de gráficos | Pantalla propia con elección del tipo y vista previa; paneles con señales de varios proyectos; modo Pantalla completa |
| Nuevos gráficos | 14 tipos de indicador, medidor, recipiente, mapa de calor, histograma, línea/área por franja y líneas de referencia |
| Tablas y mapas | Regla de dispositivos entre proyectos; columnas de identidad, KPI, medidor, gráfico y acción; mapa con datos informativos |
| Conexión | Historial en línea/fuera de línea, estado en tiempo real y cuatro señales de conectividad para gráficos |
| Almacenamiento | Papelera por proyecto y uso combinado de repositorios y proyectos |
| Publicación automática | Ícono de sobre en el proceso y valor por defecto por proyecto |
| API abierta | Contratos de API con clave, MQTT en tiempo real, control de uso y documentación |
| Widgets | Código de incorporación para pegar en cualquier sitio, con credencial propia y revocación |
| IA vía MCP | Asistentes de IA con permisos, aprobaciones, auditoría y documentación integrada |
| Firmware 2.0.1 | Edición de proceso aplicada en el dispositivo y Escritura I2C accionada por trigger |

---

**Ya está todo en línea.** Crea un indicador, un medidor o un mapa de calor, arma una tabla con los dispositivos de varios proyectos, abre un contrato de API y pega un widget en tu sitio, o conecta tu IA favorita y pídele que arme algo por ti. Actualiza también el firmware de tus dispositivos a la **2.0.1**. Cuéntanos qué te pareció: **tu feedback guía las próximas versiones.**

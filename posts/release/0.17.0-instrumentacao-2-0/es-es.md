![Portada](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# Instrumentación 2.0: calibra sensores viendo el resultado en tiempo real

**Calibración más rápida y menos propensa a errores, enlaces de calibración (manuales y automáticos), nueva página de Enlaces y la plataforma ahora en Español.**

**Versión:** 0.17.0 | **Fecha:** 2026-06-19

---

Esta actualización trae el mayor avance en la configuración de sensores desde el lanzamiento de la plataforma: la **Instrumentación 2.0**. Si calibras o linealizas sensores, la nueva pantalla muestra el resultado de tu configuración mientras escribes — sin adivinanzas. Y hay más: enlaces de calibración para usar en campo (incluso automáticos al aprovisionar), una nueva página de Enlaces, el Blog renovado y soporte completo en Español.

![Vista general de la nueva pantalla de Instrumentación 2.0](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/instrumentation_overview.png)

---

## Instrumentación 2.0: configura viendo el resultado

Rediseñamos por completo la pantalla de instrumentación. El nuevo formulario organiza todo en **dos métodos**, cada uno en su pestaña: **Cualificación** (clasificar lecturas en estados) y **Linealización** (ajustar la lectura bruta al valor real). Todo con **entrada numérica localizada** (el campo respeta el separador decimal de tu idioma) y gráficos que muestran, en tiempo real, cómo va a responder el sensor.

---

### Cualificación: convierte lecturas en clasificaciones

La función antes llamada *Cuantización* ahora se llama **Cualificación** — y quedó más clara de usar.

**Qué cambió:** la Cualificación permite **clasificar las lecturas** por **rangos de umbral**. Creas una lista de rangos, y cada rango tiene un **nombre** y un **valor de umbral**. La regla es simple y única: *si la lectura es **mayor o igual** (`≥`) al umbral, recibe el nombre de ese rango*.

Cómo funciona en la práctica:

- Los rangos se **ordenan automáticamente** (del umbral más alto al más bajo) y se evalúan de arriba hacia abajo.
- La lectura recibe el nombre del **primer rango** cuyo umbral alcanza.
- Existe un rango **"Predeterminado"** (capturar todo) que clasifica cualquier lectura que no alcance ningún umbral.
- Una **línea de tiempo lateral** muestra los rangos visualmente mientras los configuras.

"Cualificar" una lectura es, en pocas palabras, **darle un significado al número bruto**. En lugar de mostrar solo `82`, defines rangos que traducen ese valor en un estado legible.

**Por qué importa:** las lecturas se convierten en estados/clasificaciones útiles para paneles y reglas, de forma mucho más clara que mirar números sueltos.

> **Ejemplo:** crea el rango **"Crítico"** con umbral `80`, el rango **"Alerta"** con umbral `60` y deja el rango **"Predeterminado"** como "Normal". Así, una lectura de `82` se convierte en **"Crítico"**, `65` en **"Alerta"** y `40` en **"Normal"**.

> **Otro ejemplo — temperatura:** imagina clasificar la lectura de un termistor en estados de calor. Creas los rangos **"Muy caliente"** (`≥ 4000`), **"Caliente"** (`≥ 3000`), **"Templado"** (`≥ 2000`) y **"Frío"** (`≥ 1000`), y dejas el rango **"Predeterminado"** como **"Muy frío"** (capturando todo lo que esté por debajo). Con esto, una lectura de `3128` se clasifica como **"Caliente"**, `2400` como **"Templado"** y `500` como **"Muy frío"**. La línea de tiempo lateral muestra estos rangos apilados, del más caliente al más frío, a medida que los configuras.

![Pestaña de Cualificación con rangos, umbrales y línea de tiempo lateral](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/qualification_calibration.gif)

---

### Linealización asistida por el dispositivo

La **Linealización** es el método de la plataforma para convertir la lectura bruta del sensor en el valor real, ajustando una recta a puntos de referencia. Ahora defines esos puntos con **datos reales del sensor**, capturados al momento.

**Qué cambió:** al linealizar, un **minigráfico "Lecturas del dispositivo"** muestra los valores del dispositivo seleccionado. Además obtienes:

- **Botón "Solicitar lectura"**: pide al dispositivo que capture un dato **en vivo**, al instante, sin esperar un envío programado.
- **Selección de puntos en el gráfico**: selecciona **uno o más puntos** (arrastrando para marcar un intervalo). Al elegir varios, el sistema calcula su **promedio** y **rellena automáticamente** el valor del comparador en el punto de linealización.

**Por qué importa:** linealizar se vuelve más rápido y preciso — usas lecturas reales del sensor, y el promedio **reduce el efecto del ruido** de las mediciones individuales.

**Cómo usarlo:**

1. Selecciona el **dispositivo** en la pantalla de instrumentación.
2. Haz clic en **"Solicitar lectura"** para capturar un dato en vivo.
3. **Arrastra** sobre los puntos deseados en el minigráfico.
4. El **valor comparativo se rellena solo** (promedio de los puntos seleccionados).

![Selección de varios puntos en el minigráfico rellenando el valor del comparador](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/linearization_selection_of_points.gif)

---

### Retroalimentación de linealización: sabe si el ajuste quedó bien

Al añadir los puntos de linealización, la plataforma **ajusta una recta** y muestra un panel con **métricas de calidad del ajuste**. Cada campo significa:

- **Intervalo calibrado** — el rango de valores cubierto por tus puntos de linealización. Las lecturas fuera de él requieren extrapolación y pueden tener una precisión reducida.
- **Ecuación (`y = ax + b`)** — la recta ajustada por mínimos cuadrados; `a` es la ganancia y `b` es el desplazamiento aplicados a la lectura.
- **R²** — el coeficiente de determinación, de 0 a 1: cuanto más cerca de 1, mejor el ajuste. Valores por debajo de ~0,99 pueden indicar no linealidad o ruido.
- **σ (desviación estándar)** — la dispersión media entre los puntos y la recta ajustada; cuanto menor, mejor.
- **Margen de error (±2σ)** — el error máximo esperado en las lecturas calibradas, equivalente al doble de la desviación estándar.

**Por qué importa:** sabes **al instante** si la linealización quedó bien, con una estimación **objetiva** del error — en lugar de "suponer" que está correcta.

![Curva de linealización con panel de retroalimentación: Ecuación, R², σ y Margen de error](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/linearization_calibration_curve.gif)

---

### Linealización distinta por dispositivo

La misma instrumentación base ahora puede tener **linealizaciones distintas por dispositivo** (variantes).

**Por qué importa:** los sensores del mismo tipo suelen tener características únicas y responden de forma diferente al **mismo entorno**. Linealizar individualmente garantiza lecturas correctas y **comparables** entre dispositivos.

> **Ejemplo:** dos sensores de humedad idénticos, instalados uno al lado del otro, marcan valores distintos en el mismo lugar. Con una linealización propia para cada uno, ambos pasan a reportar el valor correcto.

![Linealizaciones distintas por dispositivo en la misma instrumentación](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/differents_calibrations_per_device.png)

---

## Calibración en campo: el enlace de aprovisionamiento

No siempre quien calibra el sensor es quien está en la plataforma. Por eso creamos un flujo de **calibración mediante "magic link"**: generas un enlace y el trabajo se realiza a través de una **página pública dedicada**, sin recorrer todo el flujo de la plataforma.

Importante: esta página pública **abre las mismas herramientas de instrumentación** — **Linealización** y **Cualificación**. Es decir, la persona en campo ejecuta la operación de verdad (típicamente la **Linealización**, ajustando los puntos con lecturas reales del sensor) y el resultado se convierte en una **variante de ese dispositivo**.

Un **modal** en la pantalla del dispositivo permite generar el enlace y dar seguimiento a las sesiones en curso.

**Por qué importa:** facilita la linealización en campo y permite **delegar la tarea** a quien está físicamente con el dispositivo — un técnico, un socio o el propio cliente.

**Cómo usarlo:**

1. En la pantalla del dispositivo, abre el **modal de generación del enlace de calibración**.
2. Comparte el enlace con quien hará la linealización.
3. Da seguimiento a las **sesiones de calibración** desde el mismo modal.

![Creación del enlace de calibración y calibración mediante la página pública por enlace](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/creating_calibration_link_and_calibration_by_link.png)

---

## Nueva página de Enlaces, con texto e imágenes

Añadimos una **página de Enlaces** a la plataforma. Ahora puedes configurar los **enlaces automáticos de calibración** de un repositorio.

**Por qué importa:** compartir recursos, instrucciones y materiales con tu equipo o tus clientes quedó más claro y presentable.

![Nueva página de Enlaces del repositorio con texto e imágenes](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/pagina_de_links_do_repositorio.png)

---

## Enlaces de calibración automáticos al aprovisionar

¿Y si cada nuevo dispositivo ya naciera con los enlaces de calibración listos? Ahora nace. Configuras **una sola vez por repositorio** y, con cada nuevo dispositivo aprovisionado mediante el enlace de aprovisionamiento, la plataforma **crea por sí sola las sesiones de calibración** de las instrumentaciones que elegiste.

**Para qué sirve:** cuando aprovisionas muchos dispositivos — sobre todo en campo —, generar un enlace manual para cada uno es repetitivo. Con los enlaces automáticos, quien está instalando ya recibe todo listo y **calibra al momento**, sin que nadie tenga que abrir la plataforma.

**Cómo funciona:**

- Defines qué **instrumentaciones** reciben calibración automática y la **duración predeterminada** de los enlaces.
- Con cada nuevo dispositivo aprovisionado mediante el enlace de aprovisionamiento, la plataforma crea **una sesión de calibración por instrumentación seleccionada** y genera los enlaces correspondientes (cada uno con su validez).
- No hace falta generar nada manualmente para cada dispositivo.

**Cómo configurarlo:**

1. Accede a la página de **Enlaces**.
2. Haz clic en **"Enlaces automáticos"**.
3. En el modal **"Enlaces automáticos al aprovisionar"**, selecciona las **instrumentaciones** que deben recibir calibración automática.
4. Define la **duración predeterminada de los enlaces**, en horas (mínimo 1; el valor predeterminado es **2 horas**).
5. **Guarda la configuración**.

A partir de ahí, todo dispositivo nuevo aprovisionado mediante el enlace de aprovisionamiento ya nace con los enlaces de calibración listos.

![Edición del enlace de calibración automático al aprovisionar](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/editing_automatic_calibration_link.gif)

---

## La plataforma ahora habla Español

SEU IoT ahora tiene **soporte completo en Español (es-ES)**, incluyendo **documentación** y **Términos de Uso**. Un nuevo **selector de idioma con banderas** deja el cambio a un solo clic.

**Por qué importa:** abrimos la plataforma a los usuarios de habla hispana — más alcance para ti y para tu producto.

![Cambio del idioma a Español mediante el selector con banderas](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/changing_language_to_spanish.gif)

---

## Blog renovado

El Blog recibió un buen rediseño:

- **Multiidioma:** cada publicación puede tener versiones en **Portugués, Inglés y Español**, y la lees en el idioma seleccionado en la plataforma.
- **Contenido dinámico:** las publicaciones se publican desde un repositorio de contenido, así que **las nuevas publicaciones salen al aire sin necesidad de un nuevo despliegue** de la plataforma.
- **Compartir con un clic:** copia el enlace de la publicación o compártela directamente en **LinkedIn**.
- **Búsqueda y filtros** por categoría, etiquetas y fecha para encontrar rápido lo que te interesa.

![Publicación del blog con etiquetas, botón de compartir y botón de regreso](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.17.0-instrumentacao-2-0/images/blog_post_with_tags_share_and_return_button.png)

---

## SEO y compartición: tus enlaces bien presentados

Entre bastidores, mejoramos cómo aparecen por ahí los enlaces de la plataforma y del blog:

- **Vista previa bonita al compartir:** al pegar el enlace de una publicación en redes sociales o apps de mensajería, aparece con el **título, la descripción y la imagen correctos** — las etiquetas Open Graph ahora se generan **en el servidor**, incluso para los rastreadores de los buscadores.
- **Versiones por idioma para Google:** cada publicación señala sus versiones PT/EN/ES mediante **hreflang**, así la persona encuentra el contenido en su idioma.
- **Sitemap dinámico:** el `sitemap.xml` ahora se genera automáticamente e **incluye las publicaciones del blog**, ayudando a la indexación.

**Por qué importa:** más gente encuentra y comparte el contenido — y aparece de la forma correcta.

---

## Resumen de las novedades

| Funcionalidad | Qué cambia para ti |
|---|---|
| Instrumentación 2.0 | Linealiza con datos reales del sensor, ve la calidad del ajuste (R², σ, error) y cualifica lecturas en estados |
| Linealización por dispositivo | Linealización propia para cada dispositivo, incluso en la misma instrumentación base |
| Calibración por enlace | Genera un enlace y delega la linealización/calibración en campo |
| Enlaces automáticos al aprovisionar | Los nuevos dispositivos ya nacen con los enlaces de calibración listos |
| Página de Enlaces | Comparte contenido con texto e imágenes |
| Plataforma en Español | Idioma es-ES completo, con documentación y Términos de Uso |
| Blog renovado | Publicaciones en PT/EN/ES, contenido dinámico y compartición |
| SEO y compartición | Vista previa correcta de los enlaces, hreflang y sitemap dinámico |

---

**Ya está todo al aire.** Entra en la plataforma y abre la nueva pantalla de instrumentación para sentir la diferencia al calibrar tu próximo sensor. Luego, cuéntanos: ¿qué mejoró y qué te gustaría ver todavía? **Tu feedback guía las próximas versiones.**

![Portada](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/images/seuiot_common/Capa.png)

# Novedades: Configuración por Bluetooth, Personnas y Enlaces de Aprovisionamiento

**Fecha:** Mayo de 2026 | **Versión:** v0.16.2

---

Esta actualización trae cambios importantes en la forma en que configuras y distribuyes dispositivos. Si usas Seu IoT para gestionar sensores en campo, instalar dispositivos para clientes o escalar tu operación — esta versión fue hecha para ti.

---

## Configuración vía Bluetooth directamente desde el navegador

Antes, para conectar un nuevo dispositivo a la plataforma, era necesario entrar en modo AP: conectarse al Wi-Fi del propio dispositivo, abrir una página de configuración, escribir los datos de la red — un proceso más tedioso, especialmente en campo.

**Ahora configuras cualquier dispositivo por Bluetooth, directamente desde tu navegador**, sin necesidad de cambiar de red Wi-Fi ni instalar ninguna aplicación.

### Cómo funciona en la práctica

1. Abre la página de configuración del dispositivo en Seu IoT
2. Haz clic en **Conectar vía Bluetooth**
3. Selecciona el dispositivo en la lista que aparece en el navegador
4. El sistema detecta automáticamente el firmware, la dirección MAC y el estado actual
5. Eliges la red Wi-Fi, el repositorio al que pertenecerá el dispositivo, y listo

![Configuración vía Bluetooth](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.16.2-ble-personnas-provisionamento/images/ble-provisioning.png)

La conexión está **cifrada** — el firmware del dispositivo y el servidor intercambian claves de seguridad antes de que se envíe cualquier configuración, de modo que los datos de tu red Wi-Fi viajan de forma protegida.

> Ejemplo: llegaste a un cliente con 5 dispositivos nuevos. En lugar de conectarte al AP de cada uno por separado, lo haces todo de una vez desde la pantalla del portátil, por Bluetooth, sin salir de la plataforma.

---

## Personnas: asocia dispositivos a clientes y operadores

Surgió una necesidad práctica para quien gestiona dispositivos de múltiples clientes: **¿quién es el responsable de ese dispositivo? ¿Qué cliente está asociado a él?**

La nueva sección de **Personnas** resuelve esto. Una Personna es un registro de persona o empresa que vinculas a tus dispositivos.

### Qué puedes registrar en una Personna

- Nombre completo o razón social
- CPF, CNPJ o Tax ID (para clientes internacionales)
- Dirección completa (calle, número, barrio, ciudad, estado, código postal)
- Contactos: correo electrónico, teléfono o WhatsApp
- Rol: **cliente** (quien usa el dispositivo) u **operador** (quien lo mantiene)

### Para qué sirve

- Instalas un sensor de temperatura en la fábrica de un cliente → registras al cliente como Personna y lo vinculas al dispositivo
- Si necesitas llamar para avisar de un mantenimiento, los contactos ya están ahí
- Ves, directamente en la tabla de dispositivos, qué cliente está asociado

---

## Enlaces de Aprovisionamiento: deja que tu cliente configure su propio dispositivo

Esta es una de las funcionalidades más potentes de esta versión. Puedes **generar un enlace o código QR** y enviárselo a tu cliente. Cuando él abre el enlace, aparece un flujo guiado para que él mismo conecte el dispositivo a la plataforma — **sin necesidad de tener una cuenta en Seu IoT**.

### Por qué esto importa

Piensa en una distribuidora que vende 200 sensores por mes. Antes, alguien del equipo técnico necesitaría configurar cada uno. Ahora, el propio cliente recibe un enlace, lo abre en el celular o el portátil, y completa la configuración por Bluetooth en minutos.

### Controles que tienes al crear el enlace

- **Nombre del enlace** — para que identifiques de qué campaña o cliente es
- **Repositorio de destino** — a qué proyecto entrarán los dispositivos
- **Límite de usos** — cuántos dispositivos pueden configurarse mediante el enlace
- **Validez** — el enlace puede expirar en una fecha específica
- **Asociación automática a una Personna** — el cliente rellena sus datos durante el flujo, y queda registrado al instante

![Enlaces de Aprovisionamiento](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.16.2-ble-personnas-provisionamento/images/provisioning-links.png)

El enlace genera automáticamente un **código QR** que puedes imprimir, colocar en la caja del producto o enviar por correo electrónico.

> Ejemplo: cierras un contrato con 50 unidades. Creas un enlace de aprovisionamiento con un límite de 50 usos y una validez de 30 días. Envías el enlace a tu cliente. Él configura los dispositivos a su propio ritmo, y todo cae en el repositorio correcto de tu cuenta.

![Aprovisionamiento vía Enlace](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.16.2-ble-personnas-provisionamento/images/ble-provisioning-from-provisioning-link.png)

---

## Mapa de ubicación de los dispositivos

Durante la configuración por Bluetooth, el navegador ahora **captura la ubicación geográfica** (con permiso del usuario) y guarda las coordenadas del dispositivo.

En la página de dispositivos, puedes **cambiar a la vista de mapa** y ver dónde está instalado cada dispositivo. Los dispositivos cercanos se agrupan automáticamente en el mapa para facilitar la visualización.

![Mapa de dispositivos](https://raw.githubusercontent.com/Engenharia-do-Futuro/seu-iot-blog/main/posts/release/0.16.2-ble-personnas-provisionamento/images/device-list-in-map.png)

> Útil para quien tiene dispositivos repartidos en varias ciudades o regiones — es posible ver de un vistazo si alguna zona tiene más dispositivos offline, por ejemplo.

---

## Grabación de firmware más confiable

Una corrección importante: antes de grabar el firmware en el dispositivo, la memoria flash se **limpia por completo primero**. Esto resuelve casos en los que el dispositivo quedaba en un estado inconsistente tras una actualización, especialmente cuando la grabación anterior había sido interrumpida.

---

## Documentación completa de la plataforma

La plataforma ahora cuenta con una **documentación oficial** disponible en portugués e inglés, accesible desde el menú Ayuda. Cubre desde cómo conectar el primer dispositivo hasta cómo usar paneles, calibrar sensores y entender las reglas de almacenamiento de datos.

---

## Resumen de las novedades

| Funcionalidad | Qué cambia para ti |
|---|---|
| Configuración vía Bluetooth | Configura dispositivos desde el navegador, sin modo AP |
| Comunicación cifrada | Los datos de tu red Wi-Fi se transmiten de forma segura |
| Personnas | Asocia clientes y operadores a cada dispositivo |
| Enlaces de Aprovisionamiento | Envía un enlace/código QR para que los clientes configuren solos |
| Mapa de dispositivos | Mira dónde están instalados tus dispositivos |
| Flash limpia antes de grabar | Grabación de firmware más confiable |
| Documentación | Guía completa de la plataforma en PT e EN |

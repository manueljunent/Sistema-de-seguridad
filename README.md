# SISTEMA DE SEGURIDAD

## Funcionamiento, composición e intercomunicación entre los componentes:
El sensor PIR tiene un rango de detección y emite una señal cuando detecta movimiento emite una señal cuando detecta movimiento. Cuando esto ocurre, el ESP32 recibe la señal y publica un mensaje en un tópico específico de MQTT. Luego,  el sensor magnético detecta si la puerta o ventana está abierta o cerrada.
Al abrir, envía una señal al ESP32, que publica un mensaje en otro tópico. Si el ESP32 recibe un mensaje de movimiento o apertura de puerta, activa el módulo de relé que enciende el buzzer y el LED. Cuando se activa la alarma, el ESP32 también publica un mensaje de alerta en otro tópico de MQTT.
La aplicación móvil o web suscrita a este tópico recibe la notificación. 

### COMPONENTES:

### Actuadores:

- Buzzer: En su interior se encuentra un disco con cristales piezoeléctricos. Al aplicar una tensión eléctrica, los cristales del disco generan vibraciones y se produce el sonido.
- Módulo Relé: funciona como interruptor electrónico, activando o desactivando al buzzer y al LED cuando este recibe un impulso eléctrico.

### Sensores:

- Sensor de movimiento PIR:  HC-SR501. Lo elegimos debido a su bajo costo y consumo, y su capacidad de detectar presencia humana basada en la radiación infraroja.
- Sensor de vibración: KY-002. Lo elegimos debido a su alta sensibilidad, su respuesta a cambios de vibración y su facilidad para usarse con microcontroladores.

### Otros:

- LED

### Tipo de Comunicación

- MQTT:  es un protocolo de comunicación basado en la publicación y suscripción de tópicos entre un usuario y un broker (servidor). En nuestro caso, el Esp32, crearía un tópico cuyo contenido tendrá información acerca de las detecciones de los sensores. Este tópico será recibido por un broker, y luego enviado a un cliente para que se suscriba y publique dicho tópico.
Nosotros lo elegimos por los siguientes motivos:
  -Sirve para el uso de dispositvos con poco poder computacional y de memoria.
  -Funciona bien para redes con poco ancho de banda y baja latencia.
  -"Comunicación desacoplada": debido a su funcionamiento de publicación y suscripción, en vez del tradicional solicitud-respuesta (ej: HTTP). Los dispositivos no "necesitan saber de la existencia del otro", reduciendo la complejidad.

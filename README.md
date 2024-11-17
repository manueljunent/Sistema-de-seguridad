# Introduccion

## Funcionamiento y composición e intercomunicación entre los componentes:
El sensor PIR tiene un rango de detección y emite una señal cuando detecta movimiento emite una señal cuando detecta movimiento. Cuando esto ocurre, el ESP32 recibe la señal y publica un mensaje en un tópico específico de MQTT. Luego,  el sensor magnético detecta si la puerta o ventana está abierta o cerrada.
Al abrir, envía una señal al ESP32, que publica un mensaje en otro tópico. Si el ESP32 recibe un mensaje de movimiento o apertura de puerta, activa el módulo de relé que enciende el buzzer y el LED. Cuando se activa la alarma, el ESP32 también publica un mensaje de alerta en otro tópico de MQTT.
La aplicación móvil o web suscrita a este tópico recibe la notificación. 

### Actuadores

- Buzzer: En su interior se encuentra un disco con cristales piezoeléctricos. Al aplicar una tensión eléctrica, los cristales del disco generan vibraciones y se produce el sonido.
- Módulo Relé: funciona como interruptor electrónico, activando o desactivando al buzzer y al LED cuando este recibe un impulso eléctrico.

### Sensores

- Sensor de movimiento PIR:  HC-SR501
- Sensor de puerta/ventana: KY-002

### Otros:

- LED

### Tipo de Comunicación

- MQTT:  es un protocolo de comunicación basado en la publicación y suscripción de tópicos entre un usuario y un broker (servidor). En nuestro caso, el Esp32, crearía un tópico cuyo contenido tendrá información acerca de las detecciones de los sensores. Este tópico será recibido por un broker, y luego enviado a un cliente para que se suscriba y publique dicho tópico.

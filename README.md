# Introduccion

## Funcionamiento y composición e intercomunicación entre los componentes:
El sensor PIR tiene un rango de detección y emite una señal cuando detecta movimiento emite una señal cuando detecta movimiento. Cuando esto ocurre, el ESP32 recibe la señal y publica un mensaje en un tópico específico de MQTT. Luego,  el sensor magnético detecta si la puerta o ventana está abierta o cerrada.
Al abrir, envía una señal al ESP32, que publica un mensaje en otro tópico. Si el ESP32 recibe un mensaje de movimiento o apertura de puerta, activa el módulo de relé que enciende el buzzer y el LED. Cuando se activa la alarma, el ESP32 también publica un mensaje de alerta en otro tópico de MQTT.
La aplicación móvil o web suscrita a este tópico recibe la notificación. 

## Componentes

- Relé: KY-019
		
### Actuadores

- Buzzer: uno piezoeléctrico que emite sonido al activar la alarma.
- LED intermitente: para indicar visualmente la alerta

### Sensores

- Sensor de movimiento PIR:  HC-SR501
- Sensor de puerta/ventana: KY-002

### Tipo de Comunicación

- MQTT:  permite enviar mensajes en el broker y luego permite suscribirse a temas específicos para recibir notificaciones.

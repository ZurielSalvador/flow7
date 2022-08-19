# flow7
En esta actividad se realiza la gráfica de los datos de humedad y temperatura con el sensor DHT11 a través de MQTT


Autor del respositorio: Victor Zuriel Dominguez Salvador


Autor: Hugo escalpelo 


Enlaces del autor:


https://github.com/codigo-iot/publicar-strings-json-mqtt-nodemcu-wifi/blob/main/nodemcu-mqtt-json/nodemcu-mqtt-json.ino


Enlaces sugeridos:


Biblioteca sugerida de Adafruit para el DHT11: https://www.arduino.cc/pro/hardware/product/portenta-machine-control




##Requisitos:


-ESP32-CAM


-FTDI TTL-USB


-Sensor de Temperatura Humedad DHT11



--------------------------------------------------------------------
## Descripcion de funcionamiento.


Ejercicios

Como primer ejercicio realizaremos lo siguiente:


1. Dashboard de MQTT Basic


- Importar el flow del repositorio MQTT basic, posteriormente configuraremos los temas mqtt y por ultimo iremos a dashboard.






2. Ejercicio del MQTT JSON

    https://github.com/codigo-iot/publicar-strings-json-mqtt-nodemcu-wifi/blob/main/nodemcu-mqtt-json/nodemcu-mqtt-json.ino

    En este caso, haremos uso de un codigo realizado en el ejercicio "Conexión básica por mqtt"

    *Nota: en este ejercicio solo se cambio una parte del codigo ya que puede funcionar adecuadamente.*



3. Flow 7: Reportar de forma local los valores de temperatura y humedad relativa del sensor DHT11 con el ESP32CAM posteriormente se graficára.


- Se crea un programa en arduino para el ESP32CAM que haga lo siguiente
	- Leer el sensor DHT11


	- Conexion a WiFi


	- Conexxion al broker


	- Envio de dos variables en un JSON


- Tener funcionando el Broker


- Hacer un dashboard que haga lo siguiente


	- Que se suscriba al tema donde el ESP32CAM publica


	- Que separe las variables


	- Que se muestre en dashboard el valor actual de temperatura


	- Que se muestre en dashboard el valor actual de humedad relativa


	- Gráfica en el tiempo de temperatura y humedad 


	- Que se prenda el led para señalar temperatura alta prendiendo el led flash








## Evidencias.


Ejercicio 1


[![Ejericio-flow6.png](https://i.postimg.cc/YSm4ZWd7/Ejericio-flow6.png)](https://postimg.cc/06P2JbgX)



Ejercicio 2


[![Ejercicio-2-160822.png](https://i.postimg.cc/ydMDrsc5/Ejercicio-2-160822.png)](https://postimg.cc/wykx1KWc)



Ejercicio 3 - FLOW 7


[![Ejercicio-3-160822.png](https://i.postimg.cc/JzpGCbjj/Ejercicio-3-160822.png)](https://postimg.cc/tsVXhnSg)


[![Ejercicio-3-led-encendido.png](https://i.postimg.cc/FRLRS88x/Ejercicio-3-led-encendido.png)](https://postimg.cc/cgd0y9sK)



De manera física podemos ver que el Led esta prendido:


[![Ejercicio-3-Led-encendido-fisico.jpg](https://i.postimg.cc/J4nhcsfn/Ejercicio-3-Led-encendido-fisico.jpg)](https://postimg.cc/bd78qwNc)



Para el ejercicio 3 que es denominado FLOW 7 se le agreron mas cosas, es por ello que se encuentra en el siguiente repositorio nombrado: flow7.1
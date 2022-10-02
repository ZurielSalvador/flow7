# flow7
En esta actividad se realiza la gráfica de los datos de humedad y temperatura con el sensor DHT11 a través de MQTT


**Autor del respositorio: Victor Zuriel Dominguez Salvador**


**Autor: Hugo Escalpelo**


**Enlaces del autor:**


https://github.com/codigo-iot/publicar-strings-json-mqtt-nodemcu-wifi/blob/main/nodemcu-mqtt-json/nodemcu-mqtt-json.ino


Enlaces sugeridos:


Biblioteca sugerida de Adafruit para el DHT11: https://www.arduino.cc/pro/hardware/product/portenta-machine-control




**Requisitos:**


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




-------------------------------------------------------------------------------------------------------------------------------------------------------

# Modificación del Flow7 con Grafana



Se instala y se inicia GRAFANA:



- sudo apt-get install -y adduser libfontconfig1
- wget https://dl.grafana.com/enterprise/release/grafana-enterprise_9.1.3_amd64.deb
- sudo dpkg -i grafana-enterprise_9.1.3_amd64.deb



Ejecución automática al iniciar el sistema. Estos comandos sólo tienen que ejecutarse una vez



- sudo /bin/systemctl daemon-reload
- sudo /bin/systemctl enable grafana-server

Para iniciar GRAFANA se realiza el siguiente comando:


- sudo /bin/systemctl start grafana-server




1. Agregar fuente de información


- Configuracón > Data Sources
- Hacer clic en el boton Add data Source


2. Crear un data source de MySQL

- Host: localhost:3306
- Database: Nobre de la base de datos creada para el flow Detector de Síntomas COVID
- User & Password: Nombre de usuario y contraseña creados para esa base de datos
- Hacer clic en Test & Save



Es importante Configurar privacidad de Grafana



https://grafana.com/docs/grafana/latest/setup-grafana/configure-security/configure-authentication/grafana/

- Dirigirse a /etc/grafana y editar el archivo grafana.ini
- Cambiar lo siguiente
	- En la sección security
	- allow_embedding = true



Posteriormente realizaremos lo siguiente:


- Crear una nueva base de datos llamada codigoIoT
- Crear una nueva tabla llamda clima
- id, fecha, nombre, temperatura y humedad


Una vez realizado en el se pone un Nodo function Query

En el cual se tendra el siguiente comando:


msg.topic = "INSERT INTO clima (nombre,temperatura,humedad) VALUES ('" + msg.payload.id + "'," + msg.payload.temp+ "," + msg.payload.hum + ");";
return msg;


## Base de Datos para el Flow 7.


1. Instalar mysql server
    - sudo apt update
    - sudo apt install mysql-server


2. Entrar a mysql
    - sudo mysql


3. Crear una nueva base de datos
    - CREATE DATABASE codigoIoT;


4. Seleccionar base de datos
    - use codigoIoT;


5. Crear una tabla llamada registro que contenga todos los campos necesarios


    - CREATE TABLE registro (id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY, fecha
TIMESTAMP DEFAULT CURRENT_TIMESTAMP, nombre CHAR (248) NOT NULL, temp FLOAT(4,2) NOT NULL, temp FLOAT(4,2) NOT NULL);



Para este ejercicio necesesitamos lo siguiente
- Base de datos


	- ID
	- Fecha
	- Nombre
	- Temperatura
	- Humedad




## Evidencias de la implementación de Grafana


Configuración de la Gráfica de Grafana.


[![flow7-grafana.png](https://i.postimg.cc/QM6JTQXX/flow7-grafana.png)](https://postimg.cc/8F6v8rJ3)



Flow 7 con la gráfica de Grafana:


[![Grafana-gr-ifca.png](https://i.postimg.cc/YqkLt4H8/Grafana-gr-ifca.png)](https://postimg.cc/RqsZRZqn)


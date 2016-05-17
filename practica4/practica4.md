# **_Práctica 4_**

Esta práctica consiste en comprobar el rendimiento de nuestro servidor web con _Apache Benchmark_ y _Siege_. Opcionalmente se puede realizar con otra herramienta, la cual he usado _openload_. Se realizan tres medidas, una en uno de los servidores y las otras dos en el balanceador usando como software de balanceo nginx y haproxy.
## **Apache benchmark**
Para realizar las medidas he usado el siguiente comando:

	para la máquina servidora:
		ab -n 100000 -c 100 http://192.168.140.129/test.html
	 para el balanceador:
		ab -n 100000 -c 100 http://192.168.140.132/test.html

Las medias y desviación estandar de las diferentes medidas obtenidas son:

![img](https://github.com/GinesNC/SWAP/blob/master/practica4/archivos/grafica_media_apache.PNG)
![img](https://github.com/GinesNC/SWAP/blob/master/practica4/archivos/DVest_apache_1.PNG)
![img](https://github.com/GinesNC/SWAP/blob/master/practica4/archivos/DVest_apache_2.PNG)

**Conclusión:**
Con la herramienta de apache el mejor balanceador es haproxy, ya que obtiene mejores resultados.

## **Siege**
Para realizar las medidas he usado el siguiente comando:

	para máquina servidora:
		siege -b -t60S -v http://192.168.140.129/test.html
 	para balanceador:
		/siege -b -t60S -v http://192.168.140.132/test.html

Obteniendo las siguientes medidas:

![img](https://github.com/GinesNC/SWAP/blob/master/practica4/archivos/media_siege_1.PNG)
![img](https://github.com/GinesNC/SWAP/blob/master/practica4/archivos/media_siege_2.PNG)
![img](https://github.com/GinesNC/SWAP/blob/master/practica4/archivos/DVest_siege_1.PNG)
![img](https://github.com/GinesNC/SWAP/blob/master/practica4/archivos/DVest_siege_2.PNG)

**Conclusión:**
En este caso el balanceador montando haproxy es el que mejor resultados ha obtenido.

## **Openload**
Para realizar las medidas he usado el siguiente comando:

	para máquina servidora:
		openload 192.168.140.129/test.html 100
 	para balanceador:
		openload 192.168.140.132/test.html 100

Obteniendo las siguientes medidas:

![img](https://github.com/GinesNC/SWAP/blob/master/practica4/archivos/mediaOpenload.PNG)
![img](https://github.com/GinesNC/SWAP/blob/master/practica4/archivos/DVest_openload.PNG)

**Conclusión:**
En cambio con esta herramienta el balanceador que mejor puntuación obtiene es nginx.
****
Todos los datos obtenidos se pueden consultar en el pdf de las [tablas](https://github.com/GinesNC/SWAP/blob/master/practica4/archivos/tabla.pdf)
****
**información sobre la realización de las pruebas**	
Estos test han sido realizados sobre las máquinas virtuales creadas durante las diferentes sesiones de prácticas. Para llevar a cabo esas medidas he creado un script en el cual se realizaba una operación matemática y asignaciones durante unos 1000 ciclos.
La máquina donde se ha montado todo es un intel core i7 de 3ª generación con 6 gb de RAM.

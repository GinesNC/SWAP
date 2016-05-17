# **_Práctica 4_**

Esta práctica consiste en comprobar el rendimiento de nuestro servidor web con _Apache Benchmark_ y _Siege_. Opcionalmente se puede realizar con otra herramienta, la cual he usado _httperf_. Para realizar las medidas se realizan en una de los dos servidores y las otras dos en el balanceador usando como software de balanceo nginx y haproxy.
## **Apache benchmark**
Para realizar las medidas he usado el siguiente comando:

	para maquina servidora:
		ab -n 100000 -c 100 http://192.168.140.129/test.html
	 para balanceador:
		ab -n 100000 -c 100 http://192.168.140.132/test.html

Las medias y desviación estandar de las diferentes medidas obtenidas son:

![img]()
![img]()


## **Siege**
Para realizar las medidas he usado el siguiente comando:

	para maquina servidora:
		siege -b -t60S -v http://192.168.140.129/test.html
 	para balanceador:
		/siege -b -t60S -v http://192.168.140.132/test.html

Obteniendo las siguientes medidas:

![img]()
![img]()
![img]()
![img]()

## **Openload**
Para realizar las medidas he usado el siguiente comando:

	para maquina servidora:
		openload 192.168.140.129/test.html 100
 	para balanceador:
		openload 192.168.140.132/test.html 100

Obteniendo las siguientes medidas:

![img]()
![img]()
![img]()
![img]()

## _Conclusión_

****
Todos los datos obtenidos se pueden consultar en la [tabla]()
****

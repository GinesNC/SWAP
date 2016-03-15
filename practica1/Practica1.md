# Práctica 1

La ejecución de (apache2 -v) muestra lo siguiente: [apache.txt](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/apache.txt)

*Ambas máquinas tienen la misma versión* 
		
		Server version: Apache/2.2.22 (Ubuntu)
		Server built:   Jul 22 2014 14:37:02
		
	
La ejecución de (ps aux | grep apache) muestra lo siguiente:
en la máquina 1: [apache2M1.txt](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/apache2M1.txt)
		
		root      1119  0.0  0.6  34044  6904 ?        Ss   12:01   0:00 /usr/sbin/apache2 -k start	
		www-data  1312  0.0  0.3  34068  3772 ?        S    12:01   0:00 /usr/sbin/apache2 -k start	
		www-data  1313  0.0  0.3  34068  3772 ?        S    12:01   0:00 /usr/sbin/apache2 -k start	
		www-data  1314  0.0  0.3  34068  3772 ?        S    12:01   0:00 /usr/sbin/apache2 -k start	
		www-data  1315  0.0  0.3  34068  3772 ?        S    12:01   0:00 /usr/sbin/apache2 -k start	
		www-data  1316  0.0  0.3  34068  3772 ?        S    12:01   0:00 /usr/sbin/apache2 -k start	
		gines     1694  0.0  0.0   4408   828 tty1     R+   12:38   0:00 grep --color=auto apache	
		
en la máquina 2: [apache2.txt](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/apache2.txt)
	
		root      1039  0.0  0.6  34044  6896 ?        Ss   11:57   0:00 /usr/sbin/apache2 -k start	
		www-data  1236  0.0  0.3  34068  3764 ?        S    11:57   0:00 /usr/sbin/apache2 -k start	
		www-data  1237  0.0  0.3  34068  3764 ?        S    11:57   0:00 /usr/sbin/apache2 -k start	
		www-data  1238  0.0  0.3  34068  3764 ?        S    11:57   0:00 /usr/sbin/apache2 -k start	
		www-data  1239  0.0  0.3  34068  3764 ?        S    11:57   0:00 /usr/sbin/apache2 -k start	
		www-data  1240  0.0  0.3  34068  3764 ?        S    11:57   0:00 /usr/sbin/apache2 -k start	
		gines     1574  0.0  0.0   4412   824 tty1     S+   12:08   0:00 grep --color=auto apache	
	

## Comprobación
Para comprobar que las máquinas virtuales y mi máquina se comunican he hecho un ping entre ellas. Como se muestra a continuación se puede ver que sí se comunican.	
***las ip de las máquinas***		
![img](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/ip_maquinas.PNG)
***ping entre las máquinas***		
![img](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/ping_entre_maquinas.PNG)
***ping de las máquinas hacía windows ***		
![img](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/ping_maquina_windows.PNG)

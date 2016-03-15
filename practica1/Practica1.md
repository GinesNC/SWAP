# Pr�ctica 1

*La ejecuci�n de **apache2 -v** muestra lo siguiente:*
Ambas m�quinas tienen la misma versi�n. [apache.txt](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/apache.txt)
	Server version: Apache/2.2.22 (Ubuntu)
	Server built:   Jul 22 2014 14:37:02
	
*La ejecuci�n de **ps aux | grep apache** muestra lo siguiente:*
	- en la m�quina 1: [apache2M1.txt](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/apache2M1.txt)
		---------------------------------------------------------------------------------------------
		root      1119  0.0  0.6  34044  6904 ?        Ss   12:01   0:00 /usr/sbin/apache2 -k start	|
		www-data  1312  0.0  0.3  34068  3772 ?        S    12:01   0:00 /usr/sbin/apache2 -k start	|
		www-data  1313  0.0  0.3  34068  3772 ?        S    12:01   0:00 /usr/sbin/apache2 -k start	|
		www-data  1314  0.0  0.3  34068  3772 ?        S    12:01   0:00 /usr/sbin/apache2 -k start	|
		www-data  1315  0.0  0.3  34068  3772 ?        S    12:01   0:00 /usr/sbin/apache2 -k start	|
		www-data  1316  0.0  0.3  34068  3772 ?        S    12:01   0:00 /usr/sbin/apache2 -k start	|
		gines     1694  0.0  0.0   4408   828 tty1     R+   12:38   0:00 grep --color=auto apache	|
		---------------------------------------------------------------------------------------------
	- en la m�quina 2: [apache2.txt](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/apache2.txt)
		---------------------------------------------------------------------------------------------
		root      1039  0.0  0.6  34044  6896 ?        Ss   11:57   0:00 /usr/sbin/apache2 -k start	|
		www-data  1236  0.0  0.3  34068  3764 ?        S    11:57   0:00 /usr/sbin/apache2 -k start	|
		www-data  1237  0.0  0.3  34068  3764 ?        S    11:57   0:00 /usr/sbin/apache2 -k start	|
		www-data  1238  0.0  0.3  34068  3764 ?        S    11:57   0:00 /usr/sbin/apache2 -k start	|
		www-data  1239  0.0  0.3  34068  3764 ?        S    11:57   0:00 /usr/sbin/apache2 -k start	|
		www-data  1240  0.0  0.3  34068  3764 ?        S    11:57   0:00 /usr/sbin/apache2 -k start	|
		gines     1574  0.0  0.0   4412   824 tty1     S+   12:08   0:00 grep --color=auto apache	|	
		---------------------------------------------------------------------------------------------

## Comprobaci�n
Para comprobar que las m�quinas virtuales y mi m�quina se comunican he hecho un ping entre ellas. Como se muestra a continuaci�n se puede ver que s� se comunican.	
***las ip de las m�quinas***		
![img](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/ip_maquinas.PNG)
***ping entre las m�quinas***		
![img](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/ping_entre_maquinas.PNG)
***ping de las m�quinas hac�a windows ***		
![img](https://github.com/GinesNC/SWAP/blob/master/practica1/archivos/ping_maquina_windows.PNG)
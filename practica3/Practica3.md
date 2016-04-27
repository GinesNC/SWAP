#Práctica 3

 **Configurar _nginx_ y _haproxy_**
Para configurar dichos balanceadores simplemente se sigue el guión de la práctica 3. Esta configuración se realiza sobre el software instalado en la máquina 3.
Para la comprobación de que funciona he realizado varias veces _curl_ _http://192.168.140.132_. Al realizar dicha comprobación los dos balanceadores tienen el mismo comportamiento, distribuyen la carga por igual en las dos máquinas.


 **Comprobación con ponderacion (máquina 1 doble que la 2)**
Para realizar esta comprobación hay que modificar la configuración de nginx. En nginx hay que añadir _weight=nº_, con el número mayor indica que la máquina es más potente.
De 6 peticiones 4 las hace por la máquina1 y 2 por la máquina2.
  _nginx y haproxy producen el mismo resultado_

  ![img](https://github.com/GinesNC/SWAP/blob/master/practica3/archivos/nginx.PNG)

 **(Opcional) Otro software de balanceo**
Para llevar a cabo este apartado se ha instalado en la máquina 3 el software de pound. Para llevar a cabo la instalación se ha realizado lo siguiente:


    wget http://security.ubuntu.com/ubuntu/pool/universe/p/pound/pound_2.6-6.1_i386.deb
    dpkg -i pound_2.6-6.1_i386.deb

Se ha realizado de esta forma ya que con _apt-get install pound_ no dejaba instalarlo.
Una vez instalado se ha configurado como se muestra en la imagen para que haga la función de balanceador de carga entre las dos máquinas servidoras.

_Configuración de Pound_  
![img](https://github.com/GinesNC/SWAP/blob/master/practica3/archivos/pound.PNG)

_Comprobación funcionamiento Pound_
![img](https://github.com/GinesNC/SWAP/blob/master/practica3/archivos/comprobacion_funcionamiento_pound.PNG)

***************************************

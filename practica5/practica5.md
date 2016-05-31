# Práctica 5

Esta práctica consiste en replicar una base de datos de MySQL. Para lleva a cabo dicha tarea lo primero que tenemos que hacer es crear esa base de datos en una de las máquinas.

Una vez creada e insertados algunos datos se realiza una replica de la base de datos con _mysqldump_. Esta orden se ejecuta fuera del mysql.

En primer lugar:

    mysqldump contactos -u root -p > /root/contactos.sql

Posteriormente en la máquina que actuará como esclava realizamos la copia del archivo anteriormente creado.

    scp root@192.168.140.135:/root/cotcontactos.sql /root/

Cuando se haya completado la copia, procedemos a la importación de dicha base de datos en el MySQL. Lo primero es crear esa base de datos en la máquina esclava y después restaurar los datos.

    mysqldump contactos -u root -p < /root/contactos.sql


Para no estar todo el rato realizando esta operación podemos realizar una replicación de la base de datos mediante la configuración de _maestro-esclavo_ o _maestro-maestro_. En mi caso he optado por el segundo caso donde tanto en la maquina1 como en la 2 actúan como maestro.

Para que se pueda realizar esto hay que modificar el archivo de configuración de mysql (*etc/mysql/my.cnf*):

- Para la máquina1:

    #bind-address 127.0.0.1
    log_error = /var/log/mysql/error.log
    server-id = 1
    log_bin = /var/log/mysql/bin.log

- Para la máquina2: es la misma configuración pero con server-id=2;

_*una vez realizada la configuración se reinicia mysql*_

Ahora, dentro de mysql, debemos crear un usuario para que se pueda realizar la replicación. En la máquina1 creo el que se muestra a continuación:


    CREATE USER esclavo IDENTIFIED BY 'esclavo';
    GRANT REPLICATION SLAVE ON *.* TO 'esclavo'@'%'
    IDENTIFIED BY 'esclavo';
    FLUSH PRIVILEGES;
    FLUSH TABLES;
    FLUSH TABLES WITH READ LOCK;

En la máquina2 son las mismas ordenes, pero en este caso he reemplazado _escalvo por eM1_.

Debemos obtener los datos de la base de datos que vamos a replicar. Para esto usamos _show master status;_.
En ambas máquinas nos da la misma información, por lo que la siguiente orden sería idéntica para ambas máquinas, excepto en la *ip* y en los *usuarios*.

- para la máquina1

      CHANGE MASTER TO MASTER_HOST='192.168.140.134', MASTER_USER='eM1', MASTER_PASSWORD='eM1', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=501, MASTER_PORT=3306;

- para la máquina2

      CHANGE MASTER TO MASTER_HOST='192.168.140.135', MASTER_USER='escalvo', MASTER_PASSWORD='esclavo', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=501, MASTER_PORT=3306;

Con todo lo realizado anteriormente ya funcionaría correctamente el replicamiento de la base de datos entre ambas máquinas. Esto se puede observar en la siguiente imagen.

El orden de las sentencias sería el siguiente:

  1- desde la maquina1 inserto el dato de prueba, 4.  
  2- desde la maquina2 compruebo que el dato ha sido replicado.   
  3- desde la maquina2 vuelvo a insertar otro dato, en este caso prueba, 3.   
  4- Por último en la maquina1 compruebo que se replica correctamente.    
![img](https://github.com/GinesNC/SWAP/blob/master/practica5/prueba.PNG)


*************************************

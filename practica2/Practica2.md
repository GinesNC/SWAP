#Práctica 2
**Copia de archivos por ssh**
Para probar la copia de archivos por ssh he creado un archivo y lo he copiado desde la máquina2 a la máquina1 mediante _scp_. En las siguientes imagenes se puede comprobar como esto funciona.
_Captura desde la máquina2_
![img](https://github.com/GinesNC/SWAP/blob/master/practica2/archivos/maq2.PNG)
_Captura desde la máquina1_
![img](https://github.com/GinesNC/SWAP/blob/master/practica2/archivos/maq1_ls-la.PNG)

**Clonado de una carpeta entre las dos máquinas**
En la siguiente captura se puede comprobar como el clonado de la carpeta www se ha llevado a cabo.
_Clonado de la carpeta www_
![img](https://github.com/GinesNC/SWAP/blob/master/practica2/archivos/Clonado.PNG)

**configuración de ssh para acceder sin que solicite contraseña**
Tras realizar las pasos que se indican en el guión de prácticas para la creación de la clave ssh, se puede ver como se puede acceder a la máquina 1 desde la 2 sin necesidad de claves.
_Acceso a la máquina 1 desde ssh sin necesidad de contraseñas_
![img](https://github.com/GinesNC/SWAP/blob/master/practica2/archivos/acceso_maq1_ssh.PNG)

**establecer una tarea en cron que se ejecute cada hora para mantener actualizado el contenido del directorio /var/www entre las dos máquinas**
Para probar el correcto funcionamiento he programado la tarea para que cada hora en el minuto 16 se realice el clonado de la carpeta que se pide.
_/etc/crontab_
![img](https://github.com/GinesNC/SWAP/blob/master/practica2/archivos/crontab.PNG)

_funcionamiento del crontab_
![img](https://github.com/GinesNC/SWAP/blob/master/practica2/archivos/funcionamiento_crontab.PNG)
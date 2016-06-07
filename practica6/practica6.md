# Práctica 6

Esta práctica consiste en configurar dos discos en RAID por software. El primer paso es crear dos discos mediante la herramienta que nos permite simular el sistema operativo.

![img](https://github.com/GinesNC/SWAP/blob/master/practica6/archivos/creacion_discos.PNG)

Una vez creados procedemos a la configuración del RAID por software. Para ello debemos de instalar _mdadm_.

Una vez instalado buscamos la información correspondiente, de los dos discos creados, con la herramienta _fdisk -l_.

Creamos el RAID con:

    sudo mdadm -C /dev/md0 --level=raid1 --raid-devices=2 /dev/sdb /dev/sdc

Le damos formato, y creamos el directorio donde se montará la unidad RAID:

    sudo mkfs /dev/md0
    sudo mkdir /dat
    sudo mount /dev/md0 /dat

El estado del RAID después de estos pasos es:

![img](https://github.com/GinesNC/SWAP/blob/master/practica6/archivos/estado_RAID_1paso.PNG)

Para que el dispositivo RAID se monte al arrancar el sistema añadimos al archivo _/etc/fstab_ la siguiente linea:

![img](https://github.com/GinesNC/SWAP/blob/master/practica6/archivos/etc_fstab.PNG)

También, podemos simular un fallo en uno de los discos y retirarlo "en caliente" con:

    sudo mdadm --manage --set-faulty /dev/md0 /dev/sdb
    sudo mdadm --manage --remove /dev/md0 /dev/sdb

Una vez simulado lo anterior se puede ver en la siguiente imagen como sí se puede acceder a la imformación que hay almacenada en el RAID.

![img](https://github.com/GinesNC/SWAP/blob/master/practica6/archivos/comrpobacionRAID_parada.PNG)

Para terminar esta práctica se vuelve a añadir al RAID, el disco extraido, y se ve como todo se reconstruye correctamente.

    sudo mdadm --manage --add /dev/md0 /dev/sdb

![img](https://github.com/GinesNC/SWAP/blob/master/practica6/archivos/add_RAID.PNG)

*************************************
#Parte opcional del servidor NFS.

Para configurar esto debemos instalar en la máquina que actuara de servidor los siguientes paquetes:
        
        sudo apt-get install nfs-kernel-server portmap nfs-common
        
Posteriormente debemos configurar los archivos que serán accesibles por la máquina cliente, para eso añadimos en /etc/exports la siguiente linea:

        /dat 192.168.0/24(rw,sync,no_subtree_check)

Después reiniciamos el servicio _nfs-kernel-server_ y ejeutamos _exportfs -a_.

Para poder acceder desde la máquina cliente hacemos lo siguiente:
- Primero instalamos _nfs-common_.
- Segundo se hace lo que se muestra en la imagen, donde la ip corresponde a la máquina donde está instalado el servidor NFS.

![img](https://github.com/GinesNC/SWAP/blob/master/practica6/archivos/NFS_cliente.PNG)

**************************************************


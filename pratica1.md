# Logs centralizados
## Introduccion
>El trabajo del administrador de sistemas puede verse simplificado centralizando los logs (registros del sistema) rsyslog.

### Desarollo
>Se necesita un ordenador Cliente y otro Servidor.
Para empezar hay que instalar el servicio **rsyslog**.

>Se instala con los siguentes comandos:

- #sudo apt-get install Rsyslog (Para Ubuntu)

- #sudo yum install Rsyslog (Para CentOS)

>1Pasos que hay que hacer en el servidor despues de instalar el programa.<p>1.Editar el fichero ```etc/rsyslog``` descomentando las siguentes lineas:

 ![rsyslog1](https://github.com/MitkoNachkov/MitkoNachkov.github.io/assets/145337541/e591b417-2a19-4004-affe-6e1c51e96036)

*Las lineas de TCP tambien*

>1.2.Despues de reiniciar el servicio tendremos que activar el firewall y permitir la conexion UDP y TCP por el puerto 514 que es el que hemos especificado en el archivo de configuracion de rsyslog.
- #sudo ufw enable
- #sudo ufw allow 514/udp
- #sudo ufw allow 514/tcp
  
>1.3.Reiniciar el servicio con el comando:
- #systemctl restart rsyslog.service
  
>2.Pasos que hay que hacer en el cliente:
>2.1.En el cliente lo que tendremos que hacer es añadir en el archivo /etc/rsyslog.conf el siguente texto:
- #sudo nano /etc/rsyslog.conf
- *.* @@192.168.1.1:514
  
>Lo que estamos indicando es la ip del servidor y por el puerto el cual se comunica.

>2.2.Reiniciamos el servicio con el comando:
- #systemctl restart rsyslog.service

>2.3.Y por ultimo comprobamos que llegan los mensajes al servidor desde el cliente con el comando logger:
- #logger "Mitko123"
>Ahora desde el servidor ejecutamos el siguente comando
-#tail /var/log/syslog
>Para ver el final del archivo syslog.Si se ha establecido conexion deberiamos ver algo asi:

![image](https://github.com/MitkoNachkov/MitkoNachkov.github.io/assets/145337541/77dbcff9-529b-4fcf-8be5-3cafe551f065)




# Logs centralizados
## Introduccion
>El trabajo del administrador de sistemas puede verse simplificado centralizando los logs (registros del sistema) rsyslog.

### Desarollo
>Se necesita un ordenador Cliente y otro Servidor.
Para empezar hay que instalar el servicio **rsyslog**.

>Se instala con los siguentes comandos:

- #sudo apt-get install Rsyslog (Para Ubuntu)

- #sudo yum install Rsyslog (Para CentOS)

>Pasos que hay que hacer en el cliente despues de instalar el programa.<p>1.Editar el fichero ```etc/rsyslog``` agregandole la siguente linea:
Nachkov.github.io.git
>*. * @192.168.10.254:514<p>Sustituyendo la ip y el puerto por que tengas configurado.

>2.Reiniciar el servicio con el comando:

- #systemctl restart rsyslog.serviceNachkov.github.io.git
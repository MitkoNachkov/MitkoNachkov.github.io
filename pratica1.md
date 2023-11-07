# Logs centralizados
## Introduccion
>El trabajo del administrador de sistemas puede verse simplificado centralizando los logs (registros del sistema) rsyslog.

### Desarollo
>Se necesita un ordenador Cliente y otro Servidor.
Para empezar hay que instalar el servicio **rsyslog**.

>Se instala con los siguentes comandos:

- #sudo apt-get install Rsyslog (Para Ubuntu)

- #sudo yum install Rsyslog (Para CentOS)

>Pasos que hay que hacer en el cliente despues de instalar el programa.<p>1.Editar el fichero ```etc/rsyslog``` descomentando las siguentes lineas: ![rsyslog1](https://github.com/MitkoNachkov/MitkoNachkov.github.io/assets/145337541/e591b417-2a19-4004-affe-6e1c51e96036)


>2.Reiniciar el servicio con el comando:

- #systemctl restart rsyslog.service

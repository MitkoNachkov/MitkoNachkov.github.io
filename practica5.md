# Servidor Apache2 auto-certificado.
## Introduccion
Para esta practica lo que haremos es Instalar apache2 en un servidor y con Easy-RSA y OpenSSL autofirmarlo.

## Desarollo
>Instalar Apache:
``` $ sudo apt-get install apache2```

>Ahora instalaremos Easy-RSA. Es una herramienta de gestión de entidades de certificación que utilizará para generar una clave privada y un certificado root público que, luego, usará para firmar las solicitudes de los clientes y servidores que se basarán en su CA.
``` $ sudo apt-get install easy-rsa ```

>Crearemos una carpeta con la infraestructura de la clave publica (Public Key Infraestructure).Se tiene que hacer desde un usuario non-root.
``` $ mkdir /home/mitko/easy-rsa ```

>Y creamos un enlace simbolico de donde se encuentran los archivos del programa.
```$ ln -s /usr/share/easy-rsa/* ~/easy-rsa/ ```

>Para darle mas seguridad restringiremos el acceso a la carpeta PKI para que pueda acceder solo el propietario:
```$ chmod 700 /home/mitko/easy-rsa ```

>Y por ultimo iniciaremos el PKI:
```$ cd /home/mitko/easy-rsa ```

```$ ./easyrsa init-pki ```

>Ahora para poder crear una clave privada y el certificado CA, crearemos un archivo llamado vars, estando en la carpeta /easy-rsa:
```$ nano vars```

>Con la siguente informacion:

![image](https://github.com/MitkoNachkov/MitkoNachkov.github.io/assets/145337541/bdcd2410-d246-4200-8e06-ca6033bbc63b)

>Para crear el certificado publico y el para de claves privadas ejecutaremos el comando (Estando en el directorio /easy-rsa):
```$ ./easyrsa build-ca```

>Al ejecutarlo nos pedira una passphrase para el archivo resultante:

![image](https://github.com/MitkoNachkov/MitkoNachkov.github.io/assets/145337541/8b5e1d89-a6d6-455c-b334-49d97151804d)

>Ya tenemos los dos archivos /pki/ca.crt y /pki/pirivate/ca.key . CRT es el certificado publico y KEY es la calve privada que usa CA para firmar certificados.

>Una vez que hemos instalado el CA ahora vamos a firmar una peticion CSR
>Para ello tenemos que instalar openssl:
``` $ sudo apt install openssl ```

>Igual que en easy-rsa crearemos un directorio para que tengamos a mano la peticion que crearemos y firmaremos.
```$ mkdir ~/practice-csr```
```$ cd ~/practice-csr```
```$ openssl genrsa -out mitko-server.key```

>Ahora que tenemos la clave privada crearemos un CSR:
```$ openssl req -new -key mitko-server.key -out mitko-server.req```

>La pasamos a easyrsa y la firmamos. Nos creara un certificado mitko-server.crt:
```$ cd ~/easy-rsa```
```$ ./easyrsa import-req /home/mitko/practice-csr/mitko-server.req mitko-server```
```$ ./easyrsa sign-req server mitko-server```

>Pasamos el certificado CRT a nuestro cliente por SCP y lo importamos en nuestro navegador:
```scp pki/issued/mitko-server.crt mitko@192.168.1.2:/Descargas```










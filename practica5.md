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

>Para darle mas seguridad restringiremos el acceso a la carpeta PKI:
```$ chmod 700 /home/mitko/easy-rsa ```

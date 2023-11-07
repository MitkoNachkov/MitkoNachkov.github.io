# Politica de contraseñas
## Introduccion
>El objetivo de la practica es aprender y entender a configurar las directices de seguridad. Utilizaremos el modulo pam pw_password

## Desarollo
>1.Para empezar la practica, debemos comprobar si tenemos instaladas 2 librerias. ```libpam-pwquality``` y ```libpwquality-tools```.Usaremos el siguente comando:
-# sudo apt-get install libpam-pwquality libpwquality-tools
>Con este comando si no lo tenemos instalado se instalará. Y si lo tenemos ya instalado nos lo dirá.

>2.Ahora modificaremos el archivo /etc/security/pwquality.conf .En el fichero hay unos valores comentados como por ejemplo ```minlen```,```diflok```,```minclass```,etc. Dando un valor a esas lineas, les indicamos cuantos creditos le damos a determinada accion. Por ejemplo, ```ucredit = 7``` con esto indicamos que si la contraseña tiene mayusculas, esta valdra mas que si tiene solo simple texto en minusculas.
>Un ejemplo de configuracion podria ser este:

 ![image](https://github.com/MitkoNachkov/MitkoNachkov.github.io/assets/145337541/0061645b-14a2-4173-acff-4a9e8271936a)

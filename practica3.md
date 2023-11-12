# Permisos ACL (Access Control List)
## Introduccion
>Para esta practica vamos a crear usuarios ,grupos y carpetas asignando diferentes permisos y ver como interaccionan entre si. Vamos a crear usuarios Alumnos de direfentes cursos, profesores y una carpeta que tendrá subcarpetas.

>Para crear los usuarios usaremos el comando:
```-# sudo useradd (nombre del usuario)```

>Y lo mismo para grupos
```-# sudo groupadd (nombre del grupo)```

>Como ejemplo usare estas carpetas que he creado.

![image](https://github.com/MitkoNachkov/MitkoNachkov.github.io/assets/145337541/e8eadb4d-7fea-4128-bbf2-de5698846fb2)

## Desarollo
>Comprobamos si tenemos instalado el paquete ACL con el comando:
```-# sudo apt-get install acl```
>Una vez los tenemos instalados vamos a crear dos alumnos, 2 profesores y 2 grupos que contengan los alumnos y profesores.

>Para agregar a cada persona a su grupo correspondiente usaremos el comando:
```-# sudo usermod -aG alumnos alumno1```

>Cambiamos los permisos de las carpetas con el comando:
```-# setfacl -Rm g:profesores:rwx  /home/mitko/Compartido/Profesores/```
>Lo que estamos indicando con este comando es que de manera recursiva (R) modifique (m) el grupo profesores dandole permisos de lectura, escritura y edicion a la carpeta.

>Al alumno1 le daremos permisos de lectura y escritura para ESO1.
```-# setfacl -Rm g:alumnos:rwx,u:alumno1:rw /home/mitko/Compartido/Estudiante/ESO1/```

>Con el comando getfacl Compartido/Estudiante/ESO1/ podemos ver todos los permisos que tiene la carpeta.
![image](https://github.com/MitkoNachkov/MitkoNachkov.github.io/assets/145337541/8740f545-f689-4d45-9137-cbdc65d31253)



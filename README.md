# Parte practica del examen del tercer trimestre de sistemas informáticos

## Daniel Fernandez Valcarce 7 de junio de 2022

## ENUNCIADO

Deberéis crear un repositorio público de github en el que incluiréis un fichero README.MD con la narrativa de todo el ejercicio.

### Introducción.

En este examen vamos a desplegar nuestra aplicación Public Class Hamburguesa a traves de docker.
Para ello necesitaremos dos archivos, un .war con nuestra aplición y la base de datos. Tal y como se muestra en la siguiente imagen.

<img src="https://i.gyazo.com/308628ba184ae7152f0ff3ccefb571da.png">

Los introduciremos todos en una carpeta que en mi caso la llamare Proyecto, creare dos carpetas una llamada mysql-dump en la que introducire el archivo de la base de datos  y crearé otra carpeta llamada target en la que introducire el .war . Tal como en la siguiente imagen.

<img src="https://i.gyazo.com/9f35ddc1d2f1459aaea31b2592962599.png">

## Configuración del archivo docker-compose.yml.

Para ello, crearemos un archivo .yml que es un lenguaje de marcado predefinido, que sus siglas YAML significan Yet Another Marcage Languaje. Que se llamara docker-compose.

<img src="https://i.gyazo.com/2791d539eba8cbedca1dbd4c99d8afd1.png">

En el cual introduciremos los datos para el despliegue de nuestra aplicación. En conjunto el archivo docker compose quedará de la siguiente manera: 

<img src="https://i.gyazo.com/0586ecd4a28f04dbf799d9b89cafea43.png">

En el cual iremos introduciendo los datos que marcarán el despliegue de nuestra aplicación.

Primero configuraremos nuestra base de datos, configurando la entrada a nuestra base de datos poniendo la ruta de nuestro archivo.
Despues configuraremos el acceso a nuestra base de datos configurando el usuario raiz, el nombre de la base de datos, el usuario, y la contraseña del usuario. A continuación configuraremos los puertos de entrada y de salida, para lo cual hemos de tener la anotación de que MySQL usa el puerto 3306 por lo cual si nos conectamos a ello nos dará error, en mi caso, cambio el puerto de la izquierda a 3307.

Seguidamente configuraremos phpmyadmin, que para desplegar nuestra aplicación lo dejaremos tal y como está preconfigurado

Finalmente configuraremos nuestro tomcat, marcandole el archivo al que se debe de dirigir para desplegar la aplicación, marcaremos los mismos parametros de usuarios y contraseñas que para el MySQL.

Asi tendriamos configurado nuestro archivo .yml

## Pasos para el despliegue de la aplicación.

Ejecutamos un terminal en la carpeta donde tenemos el proyecto y accedemos como administrador.

<img src="https://i.gyazo.com/7277b7ded82447db0c1094cd335b5348.png">

A continuación introducimos el siguiente comando docker-compose up -d

<img src="https://i.gyazo.com/1b62948a1a8cbcca166c7d867838d204.png">
<img src="https://i.gyazo.com/1d332e882a999122d5e9069f0899067b.png">
<img src="https://i.gyazo.com/7950226dc9ad74613f05713de53b2db1.png">

Como vemos hace pull de las tres imagenes que hemos preconfigurado anteriormente. Despues de esperar un poco a que se configure todo finalmente nos devuelve un resultado como este.

<img src="https://i.gyazo.com/ca9d219fa36656d3230194d2f4563087.png">

De ahi nos vamos a nuestro navegador e introducimos nuestro localhost, seguido del nombre de nuestro proyecto, y del html al que queremos acceder.
En mi caso es:

http://127.0.0.1:8080/PublicClassHamburguesa/index.html

Y finalmente veremos nuestra aplicacion desplegada.

<img src="https://i.gyazo.com/88dcd7ec9755c5276dc64a821715e927.png">

## Preparación y subida de la imagen a dockerhub.

Para ello accederemos a nuestro usuario desde el terminal e introduciremos nuestro usuario y password con el comando docker login:

<img src="https://i.gyazo.com/17015396c43f7c09d33b33255231afa7.png">

Para subir las imagenes a docker debermos cambiar el nombre de las imagenes y poner nuestro usuario delante, tal y como se muestra en esta imagen

<img src="https://i.gyazo.com/30b83fa04ebf176563be4927db2207cb.png">

Realizamos los push de las imagenes:

<img src="https://i.gyazo.com/0b5e83ffd082f4b5103bd5c36e1dc7b7.png">
<img src="https://i.gyazo.com/20afe522ff04021eaf6f99e2373e01d8.png">
<img src="https://i.gyazo.com/216ae2a26275e772f1bbb22ed2a6ab48.png">

En este momento ya tendriamos subido las imagenes a docker.hub

<img src="https://i.gyazo.com/0646180d464d08ce88e23908f14b0169.png">

## Conclusiones

Pese a la dificultad del despliegue de la aplicación, y los conocimientos tecnicos requeridos, gracias a la tecnologia de docker, en unos sencillos pasos podemos desplegar nuestra aplicacion en contenedores.

Pese a ello solo hemos podido desplegar nuestra aplicacion en tres contenedores diferentes

## Anexos

Links de las imagenes

https://hub.docker.com/r/danielvalcarce/phpmyadmin

https://hub.docker.com/r/danielvalcarce/mysql

https://hub.docker.com/r/danielvalcarce/tomcat

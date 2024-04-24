# Microservicios-con-Docker
Microservicios con Docker, php y mysql

LO PRIMERO es describir el proyecto con lo que hace y los microservicios que se han utilizado en el desarrollo

Debemos crear una cuenta AWS para poder desplegar el proyecto

Instalar docker

Instalar docker-compose (en la version XXX pasar un link con la 3.9)

***Podemos incluir los comandos***

Crear un Topic SNS y suscribirse además de modificar el ARN en el archivo submit.php

Dar roles al EC2 y politica SNSFullAcces

Sudo docker compose up

Debemos abrir los puertos 80, 8080 y 3306






Acceder al Formulario y probar para recibir el mensaje

Para poder clonar este repositorio debemos elegir HTTPS - Clonar repositorio

-----------------------------------------------------------------------------------------
Práctica de Microservicios con Docker en AWS
Este repositorio contiene los pasos necesarios para desplegar una aplicación web en una instancia EC2 de Amazon Web Services (AWS) utilizando Docker. 
La aplicación consta de un servidor web Apache, un servidor MySQL, phpMyAdmin y un formulario de contacto que envía datos a un tópico SNS.

Paso 1: 
Configurar una instancia EC2 en AWS
Inicia sesión en la consola de AWS y navega a EC2.
Haz clic en "Launch Instance" para lanzar una nueva instancia.
Selecciona una AMI de Amazon Linux.
Selecciona el tipo de instancia t2.small.
Asegúrate de configurar adecuadamente los ajustes de seguridad para permitir el tráfico HTTP, SSH, así como los puertos 3036 y 8080.
Crea una nueva clave de par de claves o utiliza una existente para acceder a tu instancia mediante SSH.
Lanza la instancia.

Paso 2: 
Conectar a la instancia EC2 mediante SSH
Utiliza tu cliente SSH para conectarte a tu instancia EC2 utilizando la dirección IP pública proporcionada por AWS y la clave de par de claves.

bash
ssh -i tu_clave.pem ec2-user@tu_ip_publica

Paso 3: 
Instalar y configurar el servidor web Apache y Docker
Una vez conectado a la instancia EC2, ejecuta los siguientes comandos:

bash
sudo yum update -y
sudo yum install -y docker
sudo service docker start
sudo usermod -a -G docker $(whoami)
sudo yum install -y python3-pip
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version

Paso 4: 
Crear un tópico SNS
Crea un tópico SNS en la consola de AWS y suscríbete a él con tu dirección de correo electrónico. Confirma la suscripción haciendo clic en el enlace enviado por correo electrónico.

Paso 5: 
Configuración y despliegue
Crea el archivo docker-compose.yml en la raíz del proyecto con el contenido proporcionado en este README.
Crea el archivo info.php dentro de la carpeta html con el contenido proporcionado en este README.
Crea el archivo index.html dentro de la carpeta html con el contenido proporcionado en este README.
Crea el archivo submit.php dentro de la carpeta html con el contenido proporcionado en este README.
Crea el Dockerfile de nuestro servicio php dentro de la carpeta php con el contenido proporcionado en este README.
Crea el script SQL llamado create_table.sql en la raíz del proyecto con el contenido proporcionado en este README y dale permisos de ejecución con el comando chmod +xr create_table.sql.
Crea el directorio mysql_data en la raíz del proyecto.

Despliega la infraestructura con el siguiente comando desde la raíz del proyecto:

bash
sudo docker-compose up

Acceso a la aplicación
Abre un navegador web y navega a la dirección IP pública de tu instancia EC2 seguida de /info.php para ver la información de PHP.
Accede a phpMyAdmin con la dirección IP pública de la instancia en el puerto 8080 (http://tu_ip_publica:8080).
Una vez seguidos todos los pasos, podrás acceder a la instancia EC2 en tu navegador, completar y enviar el formulario, y recibir un correo electrónico con la información del formulario. Además, podrás ver el registro en la tabla form_data en phpMyAdmin.

¡Listo para comenzar tu práctica de Docker en AWS!

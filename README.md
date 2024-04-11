# Microservicios-con-Docker
Microservicios con Docker, php y mysql
PASO 1:
o	#Actualizar librerias
o	sudo yum update –y
o	
o	#instalar docker
o	sudo yum install -y docker
o	
o	#arrancar docker
o	sudo service docker start
o	
o	#añadir nuestro usuario al grupo docker
o	sudo usermod -a -G docker $(whoami)
o	
o	#instalar pip3
o	sudo yum install -y python3-pip
o	
o	#descargarse el binario para utilizar docker-compose
o	sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
o	
o	#dar permisos de ejecucion al archivo binario
o	sudo chmod +x /usr/local/bin/docker-compose
o	#comprobar que docker compose esta instalado
o	docker-compose --version
PASO 2:
•	Dentro de este directorio /html Ejectuar los siguientes comandos para instalar php
o	sudo yum install php  php-cli php-json  php-mbstring  –y
o	sudo php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
o	sudo php composer-setup.php
o	sudo php -r "unlink('composer-setup.php');"
o	sudo php composer.phar require aws/aws-sdk-php
PASO 3:
Crear un topico SNS y subscribir tu email al topico, confirmar la subscripcion haciendo click al email que has recibido
Paso 4:
•	Despegar la infraestructura con el siguiente commando (/proyecto)
sudo docker-compose up
PASO 5:
•	Accede al archivo PHP de prueba:
Abre un navegador web y navega a la dirección IP pública de tu instancia EC2 seguida de /info.php (por ejemplo, http://tu_ip_publica/info.php). Deberías ver la información de PHP en tu navegador si la configuración se realizó correctamente.
PASO 6:
•	Añadir Rol a la EC2
o	Vamos a la consola de la EC2, vamos a acciones -> seguridad -> Añadir Rol
o	Elegimos el Rol “LabInstanceProfile”
o	Luego vamos al servicio IAM y buscamos este Rol (LabRole), y añadimos la politica “SNSFullAccess”

Una vez hechos todos los pasos, accedemos a IP publica de la instancia en el navegador, y rellenamos el formulario, una vez enviado, debemos recibir un correo en nuestro email con la informacion del formulario.
PASO 6:
Accedemos al phpmyadmin con la ip publica de la ec2 http://tu_ip_publica:8080
Adjunta la captura de pantalla del phpmyadmin mostrando el registro en la tabla del formulario. La tabla se llama “form_data"



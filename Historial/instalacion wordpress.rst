Pasos para la instalacion de worpress (bitacora web)
====================================================

Regresar a directorio home

::

   cd ~

Instalar las dependencias

::

   sudo apt-get install apache2 php5 libapache2-mod-php5 php5-mysql php5-gd libssh2-php

Obtener el paquete, descomprimirlo y moverlo al directorio que usa el servidor apache

::

   wget https://es-mx.wordpress.org/wordpress-4.3.1-es_MX.zip
   unzip wordpress-4.3.1-es_MX.zip 
   sudo mv wordpress/* /var/www/html/
   sudo cd /var/www/html
   sudo cp wp-config-sample.php wp-config.php 
   sudo chown -R mantenimientocl:www-data *
   
Crear la base de datos en el servidor

::

   mysql -u root -p
   
----
   
| CREATE DATABASE wordpress;
| EXIT

----

Editar el archivo de configuracion segun las necesidades

::

   sudo nano wp-config.php
   
----

| define('DB_NAME', 'wordpress');
| define('DB_USER', 'user');
| define('DB_PASSWORD', 'password');   

----

Crear el directorio para los archivos subidos

::

   mkdir /var/www/html/wp-content/uploads
   sudo chown -R :www-data /var/www/html/wp-content/uploads
   
Acceder al sitio desde el navegador

   http://**ip_del_servidor**
   
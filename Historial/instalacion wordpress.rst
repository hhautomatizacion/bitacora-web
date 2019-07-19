Pasos para la instalacion de wordpress (bitacora web)
=====================================================

Regresar a directorio home

::

   cd ~

Instalar las dependencias

::

   sudo apt-get install apache2 php5 libapache2-mod-php5 php5-mysql php5-gd libssh2-php
   sudo apt-get install mysql-server-5.5

Cambiar configuracion de mysql (tamaño maximo de paquete y permitir conexiones desde cualquier host)

::

   sudo nano /etc/mysql/my.cnf
   
----

| bind-address=0.0.0.0

----

| max_allowed_packet=100M

----
   
Cambiar configuracion PHP (tamaño maximo para subir archivos y tiempo maximo de ejecucion del script)

::

   sudo nano /etc/php5/apache2/php.ini
   
----

| upload_max_filesize = 100M

----

| post_max_size = 100M

----

| max_execution_time = 300

----
   
Obtener el paquete, descomprimirlo y moverlo al directorio que usa el servidor apache
Crear directorio para subir archivos

::

   wget https://es-mx.wordpress.org/wordpress-4.3.1-es_MX.zip
   unzip wordpress-4.3.1-es_MX.zip 
   sudo mv wordpress/* /var/www/html/bitacora/
   sudo cd /var/www/html/bitacora/
   sudo cp wp-config-sample.php wp-config.php 
   sudo mkdir wp-content/uploads
   sudo cd /var/www/html/
   sudo chmod -R 775 *
   sudo chown -R mantenimientocl:www-data *
   
Conceder permisos de red al usuario root y crear la base de datos en el servidor

::

   mysql -u root -p
   
----

| GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'manttocl' WITH GRANT OPTION;   
| CREATE DATABASE wordpress;
| EXIT

----

Editar el archivo de configuracion segun las necesidades

::

   sudo nano wp-config.php
   
----

| define('DB_NAME', 'wordpress');
| define('DB_USER', 'root');
| define('DB_PASSWORD', 'manttocl');   

----

   
Acceder al sitio desde el navegador

   http://**ip_del_servidor**
   
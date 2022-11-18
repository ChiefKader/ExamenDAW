# Virtual Host

El primer paso sera crear el fichero en el directorio /etc/apache2/sites-available/ , donde emplearemos el nombre de mipaginaweb.conf con el dominio *daw.ejercicio4.com*. Lo haremos de la siguiente manera:
```
sudo nano /etc/apache2/sites-available/mipaginaweb.conf
```
A continuación procederemos a escribir esto:
 ```
 <VirtualHost *:80>
        ServerAdmin webmaster@localhost
        # Nuestro dominio virtual
        ServerName ejercicio4.com
        ServerAlias daw.ejercicio4.com
        
        # Indicamos la ruta donde se aloja la web 
        DocumentRoot /var/www/html/ejercicio4.com
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
 ```
Una vez hecho lo anterior activaremos el host, con el comando:
```
sudo a2ensite mipaginaweb.conf
```
El siguiente paso sera comprobar que nuestro sitio web este activado, para eso escribiremos:
```
ls /etc/apache2/sites-enabled/
```
A continuación, escribiremos el comando:
```
sudo nano /etc/hosts
```
Una vez dentro habra que escribir nuestra IP y el dominio en el fichero HOST:
```
192.168.0.128 daw.ejercicio4.com
```
Ahora tendremos que recargar apache, lo haremos de la siguiente manera:
```
sudo service apache2 reload
```
Una vez hecho todos los pasos anteriores comprobaremos que este bien, lo primero que haremos sera iniciar Apache con el comando:
```
/etc/init.d/apache2 start
```
Ahora procederemos a introducir por la url ***daw.ejercicio4.com***

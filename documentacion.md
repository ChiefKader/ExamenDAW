# Documentación
Este documento de tipo memoria tratara sobre los ejercicios del examen, más concretamente los pasos que he realizado a modo de tutorial. Los ejercicios que se explicaran seran:
1. Conectarse a la máquina indicada por el profesor y crear una carpeta ubicada en var/www/ , a continuación crear un archivo.
2. A partir de la carpeta creada en el ejercicio anterior descargar una imagen.
3. Crear en nuestra máquina un virtualhost donde introduciendo por url *daw.ejercicio4.com* nos dirija a un apágina creada por nosotros. 
# Introducción
Este markdown ha sido realizado en un centro docente para el aprendizaje y la evaluación del alumno.

## Ejercicio SSH

Lo primero que vamos hacer sera conectarnos a la máquina con el comando:
```
sssh usuario@192.168.0.168
```
Seguido de esto iremos a la carpeta www y usaremos el comando:
```
cd /var/www
```
Una vez hecho el paso anterior crearemos una carpeta dentro de www:
```
sudo mkdir MohamedAbdelkader
```
A continuación iremos a la carpeta creada:
```
cd MohamedAbdelkader
```
Una vez dentro crearemos nuestro archivo:
```
sudo touch ejercicio2.txt
```
## Command line

Lo primero que vamos hacer sera conectarnos a la máquina con el comando:
```
sssh usuario@192.168.0.168
```
Seguido de esto viajaremos al directorio MohamedAbdelkader y usaremos el comando:
```
cd /var/www/MohamedAbdelkader
```
Ahora procederemos a descargar la imagen en su interior:
```
sudo wget https://iesalandalus.org/ ciclos/semipresencial/daw-sp/daw.png
```
## Virtual Host

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

### Webgrafía
* [Lunium.com](https://www.lunium.com/blog/crear-virtual-host-desde-ubuntu/)  
* [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server-es)  
* [Chuletario](https://markdownlivepreview.com/)  
* [Hostinger](https://www.hostinger.es/tutoriales/comando-linux-time)  
* [LinuxEspañol](https://www.linuxenespañol.com/tutoriales/reiniciar-apache-linux-ubuntu/)  
* [Hostinger](https://www.hostinger.es/tutoriales/linux-comandos)  

# despliegue-tema4

### Práctica: Preparar un servidor con apache2 + php + mariadb

Primero configuro una máquina virtual ubuntu 20 con vagrant
```
vagrant init bento/ubuntu-20.04
```
Edito el Vagrantile para hacer el forward del puerto 8080 al puerto 80

```
Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.network "forwarded_port", guest: 80, host: 8080
end
```
Levanto y actualizo el sistema
```
vagrant up
vagrant ssh
sudo apt update
```
Instalo el servidor de base de datos mariadb
```
sudo apt install mariadb-server
```
Instalo apache2 y el módulo que permite que apache2 interprete PHP
```
sudo apt install apache2 libapache2-mod-php php php-mysql
```
Creo el fichero info.php en el documentRoot (/var/www/html ?) con el siguiente contenido:
```
<?php phpinfo(); ?>
```

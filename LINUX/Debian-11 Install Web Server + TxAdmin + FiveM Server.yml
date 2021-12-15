# apt-get install apache2
# apt-get install mariadb-client
# apt-get install mariadb-server
# apt-get install mysql
# apt-get install php7.4
# apt-get install phpmyadmin

# sudo mysql_secure_installation
# mysql -u root -p

>GRANT ALL ON . TO 'phpmyadmin'@'%' IDENTIFIED BY 'password';
>flush privileges;
>exit;
----------------------------------
==Setup TxAdmin==
mkdir -p /home/FXServer/server
cd /home/FXServer/server
https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/
wget https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/4022-2771986f973c6df2844eb907973a4ff1db90bde9/fx.tar.xz;
tar xf fx.tar.xz
./run.sh
./run.sh +set serverProfile dev_server +set txAdminPort 40120

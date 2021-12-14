$ sudo passwd
[sudo] password for linuxconfig: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
==========================================================
$ sudo sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
$ sudo service ssh restart

#############################################################
To enable SSH login for a root user on Debian Linux system you need to first configure SSH server.
 Open /etc/ssh/sshd_config and change the following line:
#############################################################
$ nano /etc/ssh/sshd_config
FROM:
$ PermitRootLogin without-password
TO:
$ PermitRootLogin yes
Once you made the above change restart your SSH server:

$ /etc/init.d/ssh restart
[ ok ] Restarting ssh (via systemctl): ssh.service.
#############################################################

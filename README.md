Chromebook Crouton Help
=======================
Show chroot install options:	
`sh ~/Downloads/crouton -t help`

Install Ubuntu 14 (Trusty) Gnome Desktop Environment chroot:	
`sudo sh ~/Downloads/crouton -n trusty-gnome -r trusty -t audio,cli-extra,keyboard,gnome,xiwi` 

Install minimal Ubuntu 14 (Trusty) CLI chroot:	
`sudo sh ~/Downloads/crouton -n trusty-cli -r trusty -t cli-extra`

Delete a chroot: 	
`sudo edit-chroot -d trusty-cli`

Backup a chroot:	
`sudo edit-chroot -b trusty-cli` 

Restore a chroot:	
`sudo edit-chroot -r trusty-cli`

Start a Gnome session in the background:	
`sudo startgnome -b`

Enter a chroot on the command line:  
`sudo enter-chroot -n trusty-cli`

Run a server in chroot
---
Install the iptables package:  
`sudo apt-get install iptables`

Add a line to /etc/rc.local to open the firewall to accept all inbound traffic:  
> /sbin/iptables -P INPUT ACCEPT

Add lines to /etc/rc.local and leave the exit 0 at the end of the file:  
> mkdir -p -m0755 /var/run/sshd  
> /usr/sbin/sshd  
> /etc/init.d/apache2 start  
> /etc/init.d/tomcat6 start  
> export HOME=/etc/mysql  
> umask 007  
> [ -d /var/run/mysqld ] || install -m 755 -o mysql -g root -d /var/run/mysqld  
> /usr/sbin/mysqld &  
  
Share the Webroot with ChromeOS and other Chroots  
---  
Add lines to /etc/crouton/shares:  
> downloads/mirc /var/www/html/mirc  
> downloads/drupaltutor /var/www/html/drupaltutor  

Install LAMP Stack
---
Update packages:  
`sudo apt-get update`

Install Apache:  
`sudo apt-get install apache2`

Install MySQL and helper apps:  
`sudo apt-get install mysql-server php5-mysql`

Add database structure to MySQL:  
`sudo mysql_install_db`

Plug security gaps in MySQL:  
`sudo mysql_secure_installation`

Install PHP:  
`sudo apt-get install php5 libapache2-mod-php5 php5-mcrypt`

Change `/etc/apache2/mods-enabled/dir.conf` so Apache looks for `index.php` first:  
> `<IfModule mod_dir.c>`  
>   `DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm`  
> `</IfModule>`  

Add info.php file to the webroot to test PHP install success:  
> `<?php`    
>   `phpinfo();`  
> `?>`  



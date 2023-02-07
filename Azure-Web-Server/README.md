# Hosting apache websever on Azure

- Resources 

https://www.youtube.com/watch?v=rvwYzs6IMog
https://www.youtube.com/watch?v=WZZHUWfTAhg&t=971s


On Azure
-

    Create Storage
    Upload webserver object
    Create vm
	    -configure public access
	    -open port 80 (http)


On the Azure VM

    sudo apt install apache2

    cd /var/www/

    wget https://netxbytesazstorage.blob.core.windows.net/webserverobj/Velocity.zip

    sudo apt install unzip

    unzip velocity.zip


Change ownership

    sudo chmod -R 755 /var/www/

Create virtual host

    cd /etc/apache2/sites-available/

    sudo cp 000-default.conf ./velocity.conf

Edit the virtual host file

    sudo nano velocity.conf

Enter
    
    VirtualHost 80

    ServerAlias 20.124.115.17
    DocumentRoot /var/www/velocity

Enable the virtual host

    sudo a2ensite velocity.conf

Disable defualt configuration

    sudo a2dissite 000-default.conf

Start apache service
    
    sudo systemctl restart apache2

Check status
    
    sudo systemctl status apache2


Firewall config
19:20
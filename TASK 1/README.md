# Project 1: Web Stack Implementation (LAMP Stack) on AWS
## Project Overview

## Step-by-Step Implementation
### Step 0: Prerequisites
- Create an AWS account; i already have one

### Creating a virtual server with Ubuntu Server OS
![](image.png)
![alt text](image-1.png)
![alt text](image-2.png)
![alt text](image-3.png)
![alt text](image-4.png)

### Connecting the EC2 terminal
![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)

## Install Apache2 and update the firewall
![alt text](4.png) 
![alt text](1.png) 
![alt text](2.png) 
![alt text](3.png)

## Open inbound connection through port 80 by updating security groups

![alt text](1-1.png) 
![alt text](2-1.png) 
![alt text](3-1.png) 
![alt text](4-1.png) 
![alt text](5.png)

## To view the Apache default page, Go to http://Public-IP-Address:80 in your browser

![alt text](image-4.png)
![alt text](image-5.png)

## Install MySQL
![alt text](1-2.png) 
![alt text](2-2.png) 
![alt text](3-2.png) 
![alt text](4-2.png)

## Logging into MySQL
![alt text](<logging into mysql.png>)

## PHP installation
![alt text](1-3.png)

Once the installation is finished, you can run the following command to confirm your PHP version:
php -v
![alt text](image-6.png)

At this point, your LAMP stack is completely installed and fully operational.
- Linux (Ubuntu)
- Apache HTTP Server
- MySQL
- PHP

STEP 4 — CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE
Create the directory for projectlamp using ‘mkdir’ command as follows:
sudo mkdir /var/www/projectlamp
Next, assign ownership of the directory with your current system user:
 sudo chown -R $USER:$USER /var/www/projectlamp
Then, create and open a new configuration file in Apache’s sites-available directory using your preferred command-line editor.
sudo vi /etc/apache2/sites-available/projectlamp.conf

![alt text](image-7.png)

Now go to your browser and try to open your website URL using IP address:
http://16.16.252.83:80

![alt text](image-8.png)

## ENABLE PHP ON THE WEBSITE
Change the default directory setting on Apache from index.html to index.php:
sudo vim /etc/apache2/mods-enabled/dir.conf

![alt text](image-10.png)

Create a new file named index.php inside your custom web root folder using:
vim /var/www/projectlamp/index.php

![alt text](image-11.png)

When you are finished, save and close the file, refresh the page and you will see:

![alt text](image-12.png)





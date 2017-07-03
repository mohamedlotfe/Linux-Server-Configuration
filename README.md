# Linux-Server-Configuration
**Project Overview**
<br>
A baseline installation of a Linux distribution on a virtual machine and prepare it to host web applications, to include installing updates, securing it from a number of attack vectors and installing/configuring web and database servers
<br><br>

**Why this Project ?**
<br>
A deep understanding of exactly what web applications are doing, how they are hosted, and the interactions between multiple systems are. This project, turns a brand-new, bare bones, Linux server into the secure and efficient web application host that a Data Driven Web Applications Needs.
<br>
<h1> http://lotfy.tk/ </h1>
 IP Address: 35.188.109.4 <br>
  SSH Port: 2200 <br>
<strong>grader@35.188.109.4 -p 2200 -i m(pivate_Key)</strong></li><br>


<h3>Steps For Configure Linux server Project</h3>
<li> <strong>create Linux server instance:-> </strong><br>

<li><strong>Create New User:-> </strong><br>
 $ sudo adduser grader<br> 
 Add the this to  created file:-> $ sudo nano /etc/sudoers.d/grader -->  grader ALL=(ALL:ALL) ALL<br>
 Add the host to hosts file   :->  $ sudo nano /etc/hosts           --> 127.0.1.1 localhost ip-35-188-109-4</li><br>


<li><strong>Change the SSH port from 22 to 2200 :--> </strong><br>
  $ sudo nano /etc/ssh/sshd_config . <br>
Find the Port line and edit it to 2200. <br>
  $ sudo service ssh restart</li> <br>


<li><strong>Change timezone to UTC.</strong><br>
  $ sudo timedatectl set-timezone UTC </li><br>

<li><strong> Update currently installed packages</strong><br> 
  $ sudo apt-get update<br>
  $ sudo apt-get upgrade<br></li><br>

<li><strong> Configure the Firewall (UFW)</strong><br>
  $ sudo ufw default deny incoming<br>
  $ sudo ufw default allow outgoing<br>
  $ sudo ufw allow 2200/tcp<br>
  $ sudo ufw allow www<br>
  $ sudo ufw allow ntp<br>
  $ sudo ufw enable<br></li><br>

<li><strong> Install Apache2 and mod-wsgi and Git</strong><br>
  $ sudo apt-get install apache2 libapache2-mod-wsgi git
<br></li><br>


<li><strong>Install PostgreSQL</strong><br>
  $ sudo apt-get install libpq-dev python-dev<br>
  $ sudo apt-get install postgresql postgresql-contrib<br>
  $ sudo su - postgres <br>
  $ psql<br>
  # CREATE USER catalog WITH PASSWORD 'password';<br>
  # CREATE DATABASE catalog WITH OWNER catalog;<br>
  # REVOKE ALL ON SCHEMA public FROM public;<br>
  # GRANT ALL ON SCHEMA public TO catalog;<br></li><br>
  
<li><strong>Install Flask and sqlalchemy_utils </strong><br>
<br>$ sudo apt-get install python-pip
  $ sudo pip install Flask<br>
  $ sudo pip install httplib2 oauth2client sqlalchemy psycopg2 sqlalchemy_utils<br></li><br>
  
<li><strong>Clone the project 'Catalog' from Github</strong><br>

 $ sudo mkdir /var/www/catalog<br>
$ git clone https://github.com/mohamedlotfe/catalog.git catalog<br>
 </li><br>

</strong>

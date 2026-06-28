# WordPress Website Deployment on AWS EC2 (Amazon Linux with LAMP Stack)

## Introduction

This project demonstrates the deployment of a dynamic WordPress website on an AWS EC2 instance using Amazon Linux OS. The setup uses the LAMP stack (Linux, Apache, MySQL, PHP) to host and run the WordPress application. The goal of this project is to understand real-world cloud deployment, server configuration, and database integration.
## Architecture Diagram
![alt text](<img/architecture diagram.jpeg>)
## Step-by-Step Deployment

### Steps:<br>
1.Launch EC2 Instance

2.Go to AWS Management Console

3.Launch a new EC2 instance

4.Choose Amazon Linux AMI

5.Select instance type (t2.micro - free tier)

6.Configure security group:

7.Allow HTTP (Port 80)

8.Allow SSH (Port 22)

9.Launch instance and download key pair

![alt text](<img/launching ec2 instance.png>)
### 2.Connect to EC2 Instance

ssh -i your-key.pem ec2-user@your-public-ip

![alt text](<img/connect using ssh 2.png>)
### 3.Installation of LAMP
sudo yum update<br>
sudo yum install httpd mariadb105-server php -y<br>
sudo systemctl start httpd mariadb php-fpm<br>
sudo systemctl enable httpd mariadb php-fpm<br>
* run the file:
sudo bash lamp.sh

![alt text](<img/installation of lamp2.png>)
### 4.Taking url from GIT
sudo wget < url >

![alt text](<img/getting url from wordpress2.png>)
### 5.Decompress the file from git 
sudo tar -xvzf latest.tar.gz

![alt text](<img/detar wordpress application.png>)
### 6.Installation of connector
sudo yum install php8.5-mysqlnd.x86_64 -y

![alt text](<img/install connector2.png>)
### 7.Creating database
sudo mysql -u root -p<br>
create database wordpressdb;<br>
use wordpressdb;<br>
show tables;<br>
:it will does'nt show any table and we dont have to create table manually it will created by user apache that is created by system. 

![alt text](<img/creating database.png>)
### 8. Hit the public ip
public ip and the name of file wordpress

![alt text](<img/then we will access this page.png>)After clicking on let's go

![alt text](<img/giving information to db.png>)
You will see the this admin page where you have to fill information about database and submit but it can't submit before this we have to give permission to apache that is after clicking submit create a file named 
### wp config.php
### 9.Giving permission to apache user as owner
sudo chown -R apache:apache wprdpress/

![alt text](<img/giving permission to apache owner.png>)
now apache can create a file and it will submit and show the success!


![alt text](<img/aaccess web 2.png>)
after filling information it will look like this!!
### 10.Login to wordpress
username : root<br>
password : root
![alt text](<img/aacces web 3.png>)
#### :After login you will access the wordpress!!
### 11.Access the WORDRESS!!
![alt text](<img/main web.png>)
### 12. Data is stored in database 
different different data you can see:

![alt text](<img/database 1.png>)
Data of users that i have fill in website 

![alt text](<img/database 2.png>)
And i have succefully deployed a wordpress website !!
## Key Learnings

* AWS EC2 instance setup

* LAMP stack configuration

* Database creation and connection

* Manual deployment of WordPress

## Summary

This project successfully demonstrates deploying a WordPress website on AWS EC2 using Amazon Linux and LAMP stack. It covers all essential steps from launching an instance to configuring a database and connecting it with WordPress. This hands-on project helps in understanding real-time cloud deployment and server management.

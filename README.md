# LinuxConfiguration

## Server details

IP Address of the server : 13.127.45.56
SSH Port : 2200

URL of the hosted Application: http://ec2-13-127-45-56.ap-south-1.compute.amazonaws.com/

## List of softwares installed

#### Apache2 Server: To host the web application
#### mod_wsgi: Configured to host the flask application on apache.
#### postgres database : Installed to store the data of the catalog application.
#### Git : version control tool
#### python3: To run the flask web application.

## List of third party tools used:

#### Putty : TO connect to the server
#### Puttygen : To generate the SSH Key-pair

## SSH Key path on server for grader user:

```sh
/home/grader/.ssh/authorized_keys
```

## Steps to set up and configure server:

### Setup a server:

Start a new Ubuntu Linux server instance on Amazon Lightsail or any other cloud platform.

Loggin to the server using SSH command on linux. Windows user use putty tool to log into the server. Refer the link :https://lightsail.aws.amazon.com/ls/docs/en/articles/how-to-create-amazon-lightsail-instance-virtual-private-server-vps
to create and connect to lightsale instance.

### Securing the server:

1. Update all currently installed packages using the below commnad.

```sh
sudo apt-get update
sudo apt-get upgrade
```
2. Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH, HTTP, and NTP.

```sh
command to configure UFW:
$ sudo ufw status   --- This will give the status of the firewall
$ sudo ufw default deny incoming ---- This command will block all the incoming connections
$ sudo ufw default allow outging ---- This command will allow all the outgoing connections
$ sudo ufw allow <port_no> ----- This command will allow connection thorough the mentioned port.
$ sudo ufw enable --- THis command willl enable the firewall
```

### Creating new user and permissions:

To create a new user in the server use the following command.

```sh
$ sudo adduser <username>
```

Inorder to provide root privilege to the newly created user use the below command.

```sh
$ sudo usermod -aG sudo <username>
```

To provide the ssh access to the account refer to the steps mentioned in the below link.

https://aws.amazon.com/premiumsupport/knowledge-center/new-user-accounts-linux-instance/

### Setting up postgres database:

Most web applications require persistent data storage, typically using a database server. To install PostgreSQL use the command.

```sh
sudo apt-get install postgresql
```

Refer to the below link for crateing and providing permission for the database user.

https://www.digitalocean.com/community/tutorials/how-to-use-postgresql-with-your-django-application-on-ubuntu-14-04

### Installing Apache server:

Install Apache using your package manager with the following command: 

```sh
sudo apt-get install apache2 
```
Confirm Apache is working by visiting the public IP of the instance in your browser. You should see the apache page:

### Installing and configuring mod_wsgi:

When Apache receives a request it has a number of ways it can respond. What you’ve seen thus far is the simplest method of operation, Apache just returns a file requested or the index.html file if no file is defined within the URL.

But, Apache can do so much more! You’ll now configure Apache to hand-off certain requests to an application handler - mod_wsgi.

To install mod_wsgi user the below command:

```sh
$ sudo apt-get install libapache2-mod-wsgi
```

For detailed configuration details refer to the link  http://leonwang.me/post/deploy-flask


## Userful resources

1.  http://leonwang.me/post/deploy-flask This link provide detail explanation of setting up and configuring apache.
2.  AWS Knowledge center: https://aws.amazon.com/premiumsupport/knowledge-center/new-user-accounts-linux-instance/.
3.  Udacity knowledge portal.


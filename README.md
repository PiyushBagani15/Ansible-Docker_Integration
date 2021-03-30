# Ansible-Playbooks
🎇🎇Ansible PlayBook that does the 
following operations in the managed nodes:
🔹 Configure Docker

🔹 Start and enable Docker services

🔹 Pull the httpd server image from the Docker Hub

🔹 Run the docker container and expose it to the public

🔹 Copy the html code in /var/www/html directory
and start the web server

#Detailed Explaination

After Reading This Article, You will be able to configure the Webserver
on the top of Docker using Ansible.

So without any further delay, Let’s get started. 

What is Ansible?
===============

![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wvfxbj0v2uxzcaqqt9p3.png)

Ansible is open-source software that automates software provisioning,
configuration management, and application deployment.Ansible is included
as part of the Fedora distribution of Linux, owned by Red Hat, and is
also available for Red Hat Enterprise Linux, CentOS, openSUSE, SUSE
Linux Enterprise, Debian, Ubuntu, Scientific Linux, and Oracle Linux via
Extra Packages for Enterprise Linux (EPEL), as well as for other
operating systems. Ansible is procedural rather than declarative. In
ansible, we define what we want to do and ansible go through each and
every step for that.Ansible uses SSH to connect to remote hosts and do
the setup, no software needed to be installed beforehand on a remote
host. It’s simple, powerful and flexible.

Let’s have a look at some of the terminology used in Ansible:

Controller Node: Machine where Ansible is installed. Managed Node:
Managed nodes are also sometimes called hosts. Inventory: Information
regarding servers to be managed Playbook: Automation is defined using
tasks defined in YAML format Task: Procedure to be executed Module:
Predefined commands executed directly on remote hosts.

What is Docker?
===============

![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/oqdskqx5oorgq9qnm39o.png)

Docker is a software platform that allows you to build, test, and deploy
applications quickly. Docker packages software into standardized units
called containers that have everything the software needs to run
including libraries, system tools, code, and runtime. Using Docker, you
can quickly deploy and scale applications into any environment and know
your code will run.

This article contains the following tasks:

🎇Configure Docker

🎇 Start and enable Docker services

🎇 Pull the httpd server image from the Docker Hub

🎇 Run the httpd container and expose it to the public

🎇 Copy the html code in /var/www/html directory and start the
Web-Server.

The system that you want to make Control Node install Ansible in it
using command pip3 install ansible, then install openssh using command
yum install openssh. Now after installing ansible, just check using
ansible — version command. 
![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/l9pm1qw1bzlbjv1dd5zv.png)

Now It is clear that Ansible is installed perfectly.

After installing Ansible create an Inventory anywhere in the system,
here I have created an inventory named ip.txt

Now we have to provide details of managed node in this file created.
Here I am Using RHEL8 Os as my Managed Node. ![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k5rlknj7khuhsug97aif.png)

Here, 192.168.0.113 is IP of Managed Node ansible\_ssh\_user : User you
want to login in managed node ansible\_ssh\_pass: provide the password
of the above user Now check the connectivity with Managed Node using the
command ansible all -m ping ![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/4s38wdxf3sddyhheapwm.png)

If it shows a message in green color that means there is connectivity
and you will see the message ping pong. For running ansible command, we
need inventory file which is expected to be at a specified path:
“/etc/ansible/hosts”. We can change its path using ansible config file
(ansible.cfg file) in ansible workspace and define inventory file path
there 
![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jsyx09jizi5z4zqwh8rk.png)

Now create yml file, here i have created file name docker.yml. This yml
file is playbook where we write code in YAML. The code in playbook is as
below: 
![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/esgo9marul83mhm8xw0e.png)

![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/hbmlkfx6vl7kmaz6505m.png)

Now run the playbook using the command ansible-playbook docker.yml 
![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ua2yqgx66a7fjq5emrx1.png)

Here, If we see green color then it means that much code is skipped, if
we orange then some changes are made and if we don’t see any red color
in output then it means The playbook is executed successfully. Now we
can verify that docker is installed in Managed Node. 
![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dx83ybjk8uu31op8v25c.png)

Also Docker repo created in /etc/yum.repos.d
 ![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/m42pv8tnxndamebwp1in.png)

We can also see that container is launched.
 ![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dyozfiewimcaord8ea44.png)

Now check IP of the container. 
![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1t5jvic006r01i08973e.png)

Docker service also started 
![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9unth054i2havzyhwlj1.png)

Now finally So the webpage is working well and showing the content
properly whatever I write in the index.html file. 
![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/5ishry8a0fis0kmm4g02.png)

Voila, We did it

I hope you got an idea about how to configure webserver on the top of docker using Ansible. If you have any problem with the playbook then you check in the Github repository.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Thank You So Much For Reading😊
==============================

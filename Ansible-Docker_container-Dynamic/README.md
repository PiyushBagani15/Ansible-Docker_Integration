# Ansible-Playbooks

 Ansible Docker Integration with Dynamic Container IP 
 
🎇Ansible playbook that will retrieve newContainer IP 
and update the inventory. So that further Configuration
of Webserver could be done inside that Container.

# Detailed Explaination

Hello Readers👋👋,

Here In this Article, I will demonstrate how to Dynamically Update
Docker Container IP in the Inventory using Ansible.

Now we know what Ansible and Docker so without any further delay, let’s
get started with the demonstration…

→ Create an Inventory file with an extension .txt, Here I have created a
file called ip.txt and We don’t need to add the IP address in that as it
will be dynamically updated. ![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/23l69re76m4uq95nvtkb.png)

→ Create Ansible Configuration file:

To create an ansible file, create a file with the extension .cfg, here I
have a configuration file with named ansible.cfg ![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dbrjgf3b65iprfctxseb.png)

→ Now Create ansible playbook

Create an Ansible playbook with an extension .yml, here I have created a
playbook named docker\_new.yml ![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1fjfqipd8nl9xormokyt.png)

![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9e07n5aghkwephsrsdq8.png)

![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8a6mfr6r1j1ktf7bc4uu.png)

Don’t Worry about the code I will provide the link of GitHub Repository,
from where you can find the playbooks.

I have created the Ansible playbook in such a way that it will configure
Docker, install docker, pull Docker image, and then fetch the IP of the
container and updated it in an inventory of the controller node.

Here While launching docker container, it will pull the image which I
have created and uploaded it to Docker Hub. In this Image I have
Dockerized SSH- Install SSH and Enable SSH Service in Docker, this is
because Docker containers are not pre-configured with SSH service so
because of this We won’t be able to update IP dynamically. This is the
reason I have created seperate image. Tricky😰 Right, Don’t Worry….

For Your Reference only I am providing Steps to do above tricky task of
Dockerizing SSH

Make sure to follow these steps in creating image-

yum install net-tools -y yum install openssh-server -y ssh-keygen -A put
/usr/sbin/sshd in /root/.bashrc file set some password for root account,
which is used in inventory file during ssh

Reference Links:

Link: https://docs.docker.com/engine/reference/commandline/commit/ 
Link: https://docs.docker.com/engine/reference/commandline/push/

→Now Lets run the Playbook

To run the playbook use the command ansible-playbook <name-of-playbook>
![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/g660q72npmo2ca6d79d0.png)
![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/brjdlih4b95254b4sw3l.png)
Yeah, Playbook ran successfully!!!🎇🎇

→ Let’s Check ip.txt file…

Earlier we have seen that ip.txt was empty but it is updated
dynamically. 
![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wl8t0ajetfb2t59uaj49.png)

→ So that’s how we can configure the docker container in such a way that
the IP of the container is updated dynamically to the Inventory of
Controller Node.

Also I have created playbook for configuring Web-Server and The Target
Node will be the container and we got its IP updated in Inventory. So we
are good to go…

→ Playbook named webserver-docker.yml ![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/eqc4ygr2d2hoi5kvkok0.png)

Now after running this playbook we got : ![alt
text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/xk7xft9w5ci3hku4a62q.png)

Hurrah🎇🎇, The Web-Server is configured properly inside Container. 



Prerequisites:

installation and working platform of both software
Vagrant
Virtualbox
git

vagrant init geerlingguy/centos7
update Vagrantfile
run vagrant up and test ssh login's are working with both VM's
then login to ansibox and build container

use nfs or git clone bring Dockerfile in the docbox. 
ansible docbox -i host.yml -m ping.
ansible-playbook -i hosts.yml playbook.yml.

Starting container:
login to docbox.
name is not mandatory if container will be use with jenkins or drone for several build
docker network create --subnet=172.18.0.0/16 nginxnet
docker run -it -p 80:80 -p 443:443 --ip 172.18.0.22 alpinenginx:latest

Testing:
build docker container in the host with:-
docker build -t alpine37nginx:latest .
start the container using:
docker run --it -p 80:80 -p 443:443 alpinenginx:latest
docker ps

<table>
CONTAINER ID        IMAGE                COMMAND             CREATED             STATUS              PORTS                                      NAMES
f42f24e90841        alpinenginx:latest   "nginx"             16 seconds ago      Up 16 seconds       0.0.0.0:80->80/tcp, 0.0.0.0:443->443/tcp   upbeat_einstein
</table>

verify from chrome http://127.0.0.0

todo:
fix nfs issue while provisioning vagrant vm's.
fix docker container network to reach from network.
test the ansible playbooks.
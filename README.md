**What is required.**

 - Vagrant  
 - Virtualbox 
 -  Git

**Vargrant box startup procedure**

 - vagrant init geerlingguy/centos7  
 - vagrant up  vagrant status 
 - check the boxes are running

**Ansible provisoning**

 - vagrant scp playbook.yml, hosts.yml, Dockerfile ansibox 
 - vagrant ssh ansibox
 - ansible docbox -i host.yml -m ping 
 - ansible-playbook -i  hosts.yml playbook.yml exit
   
**Docker startup**

 - vagrant docbox
 - docker run -it -p 80:80 -p 443:443 --ip 172.18.0.22 alpinenginx:latest

**Host Testing:** 
 - docker build -t alpine37nginx:latest . 
 - docker run --it -p 80:80 -p 443:443 alpinenginx:latest docker ps

**task need to be done:** 
 - fix nfs issue while provisioning vagrant vm's. 
 - fix docker container network to reach from network.
 -  test the ansible playbooks.

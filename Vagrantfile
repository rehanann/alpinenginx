# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
  config.vm.define "ansibox" do |ansibox|
    ansibox.vm.box = "geerlingguy/centos7"
    ansibox.vm.box_version = "1.2.5"
    ansibox.vm.network "private_network", ip: "192.168.33.10"
    ansibox.vm.synced_folder ".", "/vagrant", type: "nfs", nfs_udp: false
    ansibox.vm.hostname = "ansibox"
    ansibox.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--name", "ansibox"]
      vb.memory = "1024"
    end
    config.vm.provision "shell", inline: <<-SHELL
    sudo yum install epel-release
    sudo yum install ansible
    SHELL
  end
  
  config.vm.define "docbox" do |docbox|
    docbox.vm.box = "geerlingguy/centos7"
    docbox.vm.box_version = "1.2.5"
    docbox.vm.network "private_network", ip: "192.168.33.11"
    docbox.vm.synced_folder ".", "/vagrant", type: "nfs", nfs_udp: false
    docbox.vm.hostname = "docbox"
    docbox.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--name", "docbox"]
      vb.memory = "1024"
    end
    config.vm.provision "shell", inline: <<-SHELL
    sudo yum check-update
    curl -fsSL https://get.docker.com/ | sh
    sudo systemctl enable docker
    sudo systemctl start docker
    SHELL
  end
end

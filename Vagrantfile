# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  common = <<-SHELL
    cat /home/vagrant/.ssh/me.pub >> /home/vagrant/.ssh/authorized_keys
    sudo usermod -aG sudo vagrant
    sudo apt update && sudo apt upgrade -y
  SHELL

  config.vm.box = "generic/debian10"

  config.vm.define "ansible-test1" do |master_config|
    master_config.vm.hostname = "ansible-test1"
    master_config.vm.network "private_network", ip: "192.168.98.101"
    master_config.vm.network :forwarded_port, guest: 22, host: 22101, id: "ssh"
    master_config.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--cpus", "1" ]
      v.customize ["modifyvm", :id, "--memory", "2500" ]
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.customize ["modifyvm", :id, "--name", "ansible-test1"]
    end
    config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/me.pub"
    config.vm.provision "file", source: "~/.ssh/id_rsa", destination: "~/.ssh/me"
    config.vm.provision :shell, :inline => common
  end

  config.vm.define "ansible-test2" do |master_config|
    master_config.vm.hostname = "ansible-test2"
    master_config.vm.network "private_network", ip: "192.168.98.102"
    master_config.vm.network :forwarded_port, guest: 22, host: 22102, id: "ssh"
    master_config.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--cpus", "1" ]
      v.customize ["modifyvm", :id, "--memory", "2500" ]
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.customize ["modifyvm", :id, "--name", "ansible-test2"]
    end
    config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/me.pub"
    config.vm.provision "file", source: "~/.ssh/id_rsa", destination: "~/.ssh/me"
    config.vm.provision :shell, :inline => common
  end

  config.vm.define "ansible-test3" do |master_config|
    master_config.vm.hostname = "ansible-test3"
    master_config.vm.network "private_network", ip: "192.168.98.103"
    master_config.vm.network :forwarded_port, guest: 22, host: 22103, id: "ssh"
    master_config.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--cpus", "1" ]
      v.customize ["modifyvm", :id, "--memory", "1024" ]
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      v.customize ["modifyvm", :id, "--name", "ansible-test3"]
    end
    config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/me.pub"
    config.vm.provision "file", source: "~/.ssh/id_rsa", destination: "~/.ssh/me"
    config.vm.provision :shell, :inline => common
  end
end

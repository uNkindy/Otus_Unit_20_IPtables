# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config| 

config.vm.define "centralRouter" do |centralRouter|
  config.vm.box = 'centos/7'

  centralRouter.vm.host_name = 'centralRouter'
  centralRouter.vm.network "private_network", ip: "192.168.56.240"

  centralRouter.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
  end

config.vm.define "inetRouter" do |inetRouter|
  config.vm.box = 'centos/7'

  inetRouter.vm.host_name = 'inetRouter'
  inetRouter.vm.network "private_network", ip: "192.168.56.241"
  
  inetRouter.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
  end

config.vm.define "centralServer" do |centralServer|
  config.vm.box = 'centos/7'
    
  centralServer.vm.host_name = 'centralServer'
  centralServer.vm.network "private_network", ip: "192.168.56.242"
    
  centralServer.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
  end

config.vm.define "inetRouter2" do |inetRouter2|
  config.vm.box = 'centos/7'
      
  inetRouter2.vm.host_name = 'centralRouter'
  inetRouter2.vm.network "private_network", ip: "192.168.56.243"
      
  inetRouter2.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
  end
end


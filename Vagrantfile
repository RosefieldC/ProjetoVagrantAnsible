# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "generic/debian12"

  # Configuração do provider VirtualBox
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"

    vb.customize ["createhd", "--filename", "diskp.vdi", "--size", 10240] # 10 GB
    vb.customize ["createhd", "--filename", "disks.vdi", "--size", 10240] # 10 GB
    vb.customize ["createhd", "--filename", "diskt.vdi", "--size", 10240] # 10 GB

  end  # <-- Fechando o bloco provider VirtualBox

  config.vm.network "private_network", ip: "192.168.57.10"
  config.vm.hostname = "HelioJessica"

  # vb.customize ["createhd", "--filename", "diskp.vdi", "--size", 10240] # 10 GB
  # vb.customize ["createhd", "--filename", "disks.vdi", "--size", 10240] # 10 GB
  # vb.customize ["createhd", "--filename", "diskt.vdi", "--size", 10240] # 10 GB

  # Configurar automação com provisionamento Ansible
   config.vm.provision "ansible" do |ansible|
    ansible.playbook = "/home/vagrant/playbook.yml"
  
end  # <-- Fechamento do bloco Vagrant.configure


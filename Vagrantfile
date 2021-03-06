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
  
  config.vm.define "vault-master" do |config|
    config.vm.box = "hashicorp/bionic64"
    config.vm.box_version = "1.0.282"

    config.vm.hostname = "vault-master"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
    config.vm.network "private_network", ip: "192.168.100.10"

  # Install utility tools

    config.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get -y install zip unzip
      apt-get -y install curl
      apt-get -y install jq
      # For testing Database Engine
      apt-get -y install mysql-server
    SHELL

    config.vm.provision "shell",
      path: "scripts/setupVaultServer.sh"

    config.vm.provision "shell",
      path: "scripts/initAndUnsealVault.sh"
  
  end

end

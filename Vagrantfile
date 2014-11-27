# -*- mode: ruby -*-
# vi: set ft=ruby :

# Author: Yves Hwang, 03.06.2014
# http://macyves.wordpress.com

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.define :selenium do |selenium|
        selenium.vm.box = "pfus-box"
        selenium.vm.network "forwarded_port", guest: 4444, host:4444
        selenium.vm.network "private_network", ip: "192.168.1.44"
        selenium.vm.provider "virtualbox" do |vb|
          vb.memory = 4096
          vb.cpus = 4
        end
        $script_selenium = <<SCRIPT
        service Xvfb start
        service selenium-grid start
        service selenium-node start
SCRIPT
        selenium.vm.provision :shell, :inline => $script_selenium
    end
end

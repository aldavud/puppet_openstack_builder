# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.define :node01 do |n1config|
    n1config.vm.box = "precise64"
    n1config.vm.network :hostonly, "10.0.1.11"
    n1config.vm.network :hostonly, "10.0.2.11"
    n1config.vm.provision :shell, :inline => "apt-get update; apt-get install git vim -y"
    n1config.vm.customize ["modifyvm", :id, "--memory", 4096]
    n1config.vm.host_name = 'node01'
  end

  config.vm.define :node02 do |n2config|
    n2config.vm.box = "precise64"
    n2config.vm.network :hostonly, "10.0.1.12"
    n2config.vm.network :hostonly, "10.0.2.12"
    n2config.vm.provision :shell, :inline => "apt-get update; apt-get install git vim -y"
    n2config.vm.customize ["modifyvm", :id, "--memory", 4096]
    n2config.vm.host_name = 'node02'
  end
end

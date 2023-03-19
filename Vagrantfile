# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
    ansible.become = "true"
  end  

  config.vm.define "pxeserver" do |server|
    server.vm.box = "nvkmv/rockylinux9"
    server.vm.host_name = 'pxeserver'    
    server.vm.network :private_network,
                       ip: "10.0.0.20",
                       virtualbox__intnet: 'pxenet'
    server.vm.network "forwarded_port", guest: 80, host: 8081
    server.vm.network "forwarded_port", guest: 25151, host: 25151  
    server.vm.synced_folder "./data", "/home/vagrant/data"
  end

  config.vm.define "pxeclient" do |client|
    client.vm.box = "nvkmv/rockylinux9"
    client.vm.host_name = 'pxeclient'
    client.vm.network :private_network,
                       virtualbox__intnet:'pxenet'
    client.vm.synced_folder "./data", "/home/vagrant/data"                   
  end
end

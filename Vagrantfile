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
    server.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end    
    server.vm.synced_folder "./data", "/home/vagrant/data"
  end

  config.vm.define "pxeclient" do |client|
    client.vm.box = "nvkmv/rockylinux9"
    client.vm.host_name = 'pxeclient'
    client.vm.network :private_network,
                       virtualbox__intnet: 'pxenet'
    client.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.gui = true
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize [
        'modifyvm', :id,
          '--nic1', 'intnet',
          '--intnet1', 'pxenet',
          '--nic2', 'nat',
          '--boot1', 'net',
          '--boot2', 'none',
          '--boot3', 'none',
          '--boot4', 'none'
        ]
    end                      
    client.vm.synced_folder "./data", "/home/vagrant/data"                   
  end
end
